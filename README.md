# nagios-bash-script
Bash Script to configure the Nagios on the Amazon Linux Platform
#!/bin/bash
yum install -y httpd httpd-tools php gcc glibc glibc-common gd gd-devel make net-snmp
yum install -y httpd php php-cli gcc glibc glibc-common gd gd-devel net-snmp openssl openssl-devel wget unzip
useradd nagios
groupadd nagcmd
usermod -G nagcmd nagios
usermod -G nagcmd apache
mkdir /root/nagios
cd /root/nagios
wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.9.tar.gz
wget https://nagios-plugins.org/download/nagios-plugins-2.3.3.tar.gz
tar -xf nagios-4.4.9.tar.gz
tar -xf nagios-plugins-2.3.3.tar.gz
cd nagios-4.4.9/
./configure --with-command-group=nagcmd
make all
make install
