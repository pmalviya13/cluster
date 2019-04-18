---------------------------------------
sudo su
passwd
adduser <username>
usermod -aG sudo <userame>
---------------------------------------
now login with new  user

sudo su
apt-get update
dpkg --configure -a
apt-get upgrade
---------------------------------------
IN CASE OF LOCK

sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
---------------------------------------
install and configuring ssh

apt-get install openssh-server
sudo nano /etc/ssh/sshd_config
	permitRootLogin=yes
	PasswordAuthentication=yes
service ssh restart
---------------------------------------
INSTALLING ntp

apt-get install ntp
update-rc.d ntp defaults
---------------------------------------
ADD ALL NODES IN HOSTS FILE

sudo nano /etc/hosts
	<ip>	<hostname>

---------------------------------------
CHANGING HOSTNAME

hostname <hostname>
hostname
hostname -f
		hostname and hostname -f must be same 
sudo nano /etc/network/interfaces
	NETWORKING=yes
	HOSTNAME=<machine's_hostname>
---------------------------------------
DISABLING FIREWALL

sudo ufw disable
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
---------------------------------------
apt install selinux-utils
sudo nano /etc/selinux/semanage.conf
	SELINUX=disabled
setenforce 0
umask 0022
umask
echo umask 0022 >> /etc/profile
/etc/init.d/apparmor stop
sudo update-rc.d -f apparmor remove
---------------------------------------
DISABLE ipv6

sudo nano gksudo gedit /etc/sysctl.conf
	net.ipv6.conf.all.disable_ipv6 = 1
	net.ipv6.conf.default.disable_ipv6 = 1
	net.ipv6.conf.lo.disable_ipv6 = 1
cat /proc/sys/net/ipv6/conf/all/disable_ipv6

If it reports ‘1' means you have disabled IPV6. If it reports ‘0‘ then please follow Step 4 and Step 5.  

sudo sysctl -p  #you will see this in terminal.

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Repeat above “Step 3” and it will now report 1.

---------------------------------------
apt-get update
dpkg --configure -a
apt-get upgrade
---------------------------------------

