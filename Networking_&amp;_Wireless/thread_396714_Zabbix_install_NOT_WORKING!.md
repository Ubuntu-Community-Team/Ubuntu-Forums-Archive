---
title: "Zabbix install NOT WORKING!"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by twiztid on 2007-03-29
Anyone else have serious issues installing Zabbix?  I got everything off of the repo's, mysql, apache, php, zabbix, did the installation, went to run the front end and for some reason my browser tries to download the .phtml file instead of viewing it.

Any ideas?

I've never set up a db before so this is very new to me.

---

### Post by selectron on 2007-06-14
Hi!
twiztid, I have some trouble on first server, but when I installed Zabbix on second server this trouble was not. May be it's because of apache2 or browser settings.
At this time I can't resolve it. How you?
Sorry for my English.

---

### Post by selectron on 2007-06-19
Hi, twiztid!
I think that I resolved this problem. I think that folder "frontends/php/*" is'n t in true place on your PC. I copied it in folder "/var/www/zabbix/*".
It's work!
[http://www.howtoforge.com/zabbix_network_monitoring](http://www.howtoforge.com/zabbix_network_monitoring)  - this is good howto.

---

### Post by bkingx on 2007-06-20
Hi all!  I have had the same problems and figured it out.  Here is my complete install procedure on Feisty server:

Intended for Zabbix 1.4 on Ubuntu Feisty Fawn 7.04


Install pre-requisites:
Apache
MySQL-Server
PHP5
Net-Snmp libraries

sudo aptitude install build-essentials mysql-server php5 php5-gd snmp libsnmp9-dev snmpd

1 - Make the zabbix user and group:

sudo adduser zabbix
	enter in new password
	confirm
	use the remaining defaults.

Add zabbix to the admin group:

sudo adduser zabbix admin


2 - Download and Untar the sources:

su - zabbix
wget [http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz](http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz)
tar zxvpf zabbix-1.4.tar.gz


3 - Create a zabbix database and populate it:

mysql -u root -p
create database zabbix;
quit;

mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/schema/mysql.sql
mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/data/data.sql


4 - Configure, compile and install the server:

cd zabbix-1.4/
./configure --prefix=/usr --with-mysql --with-net-snmp \
--enable-server --enable-agent &&
make
sudo make install


5 - Prepare the rest of the system:

sudo nano /etc/services

Add at the end:

zabbix_agent 10050/tcp # Zabbix ports
zabbix_trap 10051/tcp

Save and exit.

sudo mkdir /etc/zabbix
sudo chown -R zabbix.zabbix /etc/zabbix/
cp misc/conf/zabbix_* /etc/zabbix/

Edit /etc/zabbix/zabbix_agentd.conf:

nano /etc/zabbix/zabbix_agentd.conf

Make sure that the Server parameter points to the server address, for the agent that runs on the server it is like this:

Server=127.0.0.1

Edit /etc/zabbix/zabbix_server.conf:

nano /etc/zabbix/zabbix_server.conf

For small sites this default file will do, however if you are into tweaking your config for your 10+ hosts site, this is the place.

Change this:

# Database password
# Comment this line if no password used

DBPassword=Secret

Start the server :

zabbix_server

Start the client:

zabbix_agentd &


6 - Configure web interface

mkdir /home/zabbix/public_html
cp -R frontends/php/* /home/zabbix/public_html/

Edit /etc/apache2/sites-enabled/000-default:

sudo nano /etc/apache2/sites-enabled/000-default

Work into file:

Alias /zabbix/ /home/zabbix/public_html/
<Directory /home/zabbix/public_html>
  AllowOverride FileInfo AuthConfig Limit Indexes
  Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
  <Limit GET POST OPTIONS PROPFIND>
    Order allow,deny
    Allow from all
  </Limit>
  <LimitExcept GET POST OPTIONS PROPFIND>
    Order deny,allow
    Deny from all
  </LimitExcept>
</Directory>

Save and exit.

Make php.ini adjustments:

sudo nano /etc/php5/apache2/php.ini

Change the following values:

max_execution_time = 300     ; Maximum execution time of each script, in seconds
date.timezone = America/Kentucky/Louisville
(use this url to find your correct timezone format: [http://us3.php.net/manual/en/timezones.php](http://us3.php.net/manual/en/timezones.php) )


Restart Apache:

sudo /etc/init.d/apache2 restart


Now point your browser to:

http://<servername or ip>/zabbix/

1. Introduction

read and click Next

2. License Agreement

Read, check 'I Agree', click Next

3. Check of Pre-Requisites

Fix any problems, click retry.  Click Next when all pre-requisites are OK.

4. Configure DB Connection

Enter appropriate settings and click Test Connection.
Click Next when OK.

5. Pre-Installation Summary

Verify installation settings, click Next.

6. Install

Click Save Configuration file and save to machine.
Copy zabbix.conf.php to /home/zabbix/public_html/conf/zabbix.conf.php

One way to do this from a desktop machine (requires ssh installed):
scp zabbix.conf.php zabbix@<serverip>:/home/zabbix/public_html/conf/

Click Retry and click Next when OK.

7. Finish

Click Finish to complete installation.


Your New Zabbix install will now be shown.

Log in with username: Admin
No Password

First go to the tab Configuration and then Hosts.

Now create a host-group, see that you can give it some templates, e.g: Application.MySQL, Host.SNMP, Host.Standalone, Host.Unix.

Then some hosts:

Select your host-group and use Link with Template Host.Unix

Now a lot of triggers are imported and the game begins.

Go to the monitoring tab and watch the latest values roll in.

For specifics on configuration, please refer to the Zabbix user manual.

[www.zabbix.com](www.zabbix.com)

---

### Post by selectron on 2007-06-21
Hi, bkingx.
I think that you must copy folder "frontends/php/*" to "/var/www/zabbix/*".
[http://www.zabbix.com/forum/showthread.php?t=6340&page=2&pp=10&highlight=connect]("http://www.zabbix.com/forum/showthread.php?t=6340&page=2&pp=10&highlight=connect")

---

### Post by zhivko.neychev on 2007-07-16
I installed:
sudo aptitude install build-essentials mysql-server php5 php5-gd snmp libsnmp9-dev snmpd
and when I try to make 
/configure --prefix=/usr --with-mysql --with-net-snmp --enable-server --enable-agent &&make

generate error:  Not found MySql library.
Have you any ideas?

---

### Post by selectron on 2007-07-18
Hi, zhivko.neychev!
Did you install mysql-common package?

---

### Post by kvonb on 2007-10-03
bkingx's instructions worked for me on Feisty (excellent tutorial, thanks bkingx) with a few additions:

The package install line should be:

```
sudo aptitude install build-essential mysql-server php5 php5-gd snmp libsnmp9-dev snmpd libmysqlclient15-dev mysql-common

```And also the addition of the folder in /var/www as suggested by selectron:

```
sudo mkdir /var/www/zabbix
sudo cp -R frontends/php/* /var/www/zabbix/

```You then have to place the downloaded config file into /home/zabbix/public_html/conf/

It works for me but the configuration is ridiculous, I can't understand how any of it actually works :/

The other problem is that it doesn't seem to be able to monitor a pppoe connection which makes it completely useless to me :(.

For an easier and more useful system monitor, install phpsysinfo instead ([http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)), and install lmsensors and hddtemp through synaptic first.

---

