---
title: "Squid and Squid Guard.."
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by SVFUSiON on 2015-09-10
I've been trying to setup a Squid Server with SquidGuard, mostly to just block ads on our network. Since ads are a leading cause of virus downloads.. (fake download buttons, ect) I know there are other ways of doing this, and this is mostly just experimental  ATM.. 

I'm justing Hyper-V Server 2012 R2
Ubuntu 14.04.1

I can have squid working fine.. 
Let's start from the beginning.. 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install squid3

sudo nano /etc/squid3/squid.conf

Make the following changes,

visible_hostname machine-name
http_port 3128
cache_dir ufs /var/spool/squid 1000 16 256
cache_access_log /var/log/squid/access.log

 

acl intranet 10.50.0.0/24
http_access allow intranet

sudo service start squid

Config my test machine and BAM! Squid works like a champ! Let me make a setpoint in Hyper-V Server manager..

It's time for me to install squidGuard
sudo apt-get install squidguard

For the next commands, I have to use the sudo command, or I don't have permission.. 

sudo mkdir /opt/3rdparty

sudo cd /opt/3rdparty 
sudo wget [http://www.shallalist.de/Downloads/shallalist.tar.gz](http://www.shallalist.de/Downloads/shallalist.tar.gz)
sudo tar xzf shallalist.tar.gz 

I'm going to copy the one of the rules to the DB, I'm going to use porn as an example
sudo cp -a /opt/3rdparty/BL/porn /var/lib/squidguard/db

sudo squidGuard -C all
I'm assuming when I installed squid it made a user named "proxy"
chown -R proxy:proxy /var/lib/squidguard/db/

Add this to my /etc/squid3/squid.conf 
url_rewrite_program /usr/bin/squidGuard

Make my /etc/squidguard/squidGuard.conf look like this

#
# CONFIG FILE FOR SQUIDGUARD
#

dbhome /usr/local/squidGuard/db
logdir /usr/local/squidGuard/logs

dest porn {
        domainlist porn/domains
        urllist porn/urls
        }

acl {
        default {
                pass !porn all
                redirect [http://localhost/block.html](http://localhost/block.html)
        }
 }

Not only that doesn't block porn, Squid stops working all together..  Any ideas??

Edit, I've tried a different list now after restarting from scratch.. Squid doesn't crash anymore, but nothing is being blocked..

---

### Post by SVFUSiON on 2015-09-11
adding url_rewrite_access allow all to my squid.conf fixed this issue.

---

