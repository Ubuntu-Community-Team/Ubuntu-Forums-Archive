---
title: "Trouble Installing Packages, Dependencies"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mfmbcpman on 2009-05-17
I am trying to install some components on a VPS I purchased but running into some trouble. 

This is what I am trying to run
```
apt-get install apache2 libapache2-mod-scgi rtorrent screen wget gawk sqlite unzip php5-cgi php5-common php5-sqlite php5-xmlrpc php5-curl
```


This is the message returned
> Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version.
libapache2-mod-scgi is already the newest version.
rtorrent is already the newest version.
screen is already the newest version.
wget is already the newest version.
wget set to manually installed.
gawk is already the newest version.
sqlite is already the newest version.
unzip is already the newest version.
unzip set to manually installed.
php5-common is already the newest version.
php5-common set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-cgi: Depends: php5-common (= 5.2.6-2ubuntu4) but 5.2.6-2ubuntu4.1 is to be installed
  php5-curl: Depends: php5-common (= 5.2.6-2ubuntu4) but 5.2.6-2ubuntu4.1 is to be installed
  php5-sqlite: Depends: php5-common (= 5.2.6-2ubuntu4) but 5.2.6-2ubuntu4.1 is to be installed
  php5-xmlrpc: Depends: php5-common (= 5.2.6-2ubuntu4) but 5.2.6-2ubuntu4.1 is to be installed
E: Broken packages


How do I fix this? Thanks in advance! I'm on Ubuntu 8.10

---

### Post by taurus on 2009-05-17
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Make sure you don't mix releases in /etc/apt/sources.list.  If you are running Intrepid, make sure all the repos are for intrepid.

---

