---
title: "Looking to spread my wings."
date: 2010-11-03
forum: New to Ubuntu
---

### Post by robsonic on 2010-11-03
Hello everyone,

My name is Robby, and I am looking to start up my own server for web hosting. I have a fairly broad knowledge of computers in general, but not much on Ubuntu. I was a Windows user in my previous years. I am fairly uncertain of where to start in my endeavor, and if any senseis would care to grace me with advice, I would certainly appreciate it immensely. 

Thank you all.

---

### Post by Zzl1xndd on 2010-11-03
Welcome to Linux and Ubuntu. 

I would probably just start with the normal Desktop play around a bit with apache. Once your comfortable then move on to server. 

Best of Luck.

---

### Post by hot_rod_hippie on 2010-11-03
If you're not comfortable working with just the command line, I'd go with just a desktop install (probably Ubuntu 10.04LTS to avoid needing version upgrades that can sometimes break a server system).

It is pretty easy to install and configure Apache as a web server.
For command line setup in 10.04 try the Ubuntu Server Guide: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Have fun playing!
Hippie

---

### Post by e24ohm on 2010-11-03
> **robsonic said:**
> Hello everyone,

My name is Robby, and I am looking to start up my own server for web hosting. I have a fairly broad knowledge of computers in general, but not much on Ubuntu. I was a Windows user in my previous years. I am fairly uncertain of where to start in my endeavor, and if any senseis would care to grace me with advice, I would certainly appreciate it immensely. 

Thank you all.

Welcome to Linux, or more specifically Ubuntu.

I would recommend Drupal for a nice content management software, which can be nice place to start since it will need a few other applications. This will give you nice experience on a broad range of services related to Linux hosting.

However, you will want to first start by reading the following link, and the sub sections.

[https://help.ubuntu.com/10.04/serverguide/C/web-servers.html](https://help.ubuntu.com/10.04/serverguide/C/web-servers.html)

---

### Post by Crazedpsyc on 2010-11-03
from ubuntu desktop open a terminal from Applications>Accessories>Terminal and enter
```
sudo apt-get install apache2
```Then you can add your website's files to /var/www by running the following from a terminal
```
sudo nautilus /var/www
``` to open the file browser. if you want php support on your server run:
```
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
```
Edit: And you should install webmin for a great web-based control panel to any server you choose.
```
firefox [http://prdownloads.sourceforge.net/webadmin/webmin_1.520_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.520_all.deb)
```

Good luck!

---

### Post by robsonic on 2010-11-03
I currently have the 10.04 Desktop release of Ubuntu, should I go ahead and upgrade to the 10.10 release?

---

### Post by Barriehie on 2010-11-03
> **robsonic said:**
> Hello everyone,

My name is Robby, and I am looking to start up my own server for web hosting. I have a fairly broad knowledge of computers in general, but not much on Ubuntu. I was a Windows user in my previous years. I am fairly uncertain of where to start in my endeavor, and if any senseis would care to grace me with advice, I would certainly appreciate it immensely. 

Thank you all.

Are you wanting this for your own use or are you planning on 'renting' access to the machine?  The costs of one versus the other are quite different!

---

### Post by Crazedpsyc on 2010-11-03
I think you'll be alright with that as long as you don't have a low download allowance (from your ISP) like me and yu have plenty of time to spare

---

### Post by robsonic on 2010-11-03
> **Barriehie said:**
> Are you wanting this for your own use or are you planning on 'renting' access to the machine?  The costs of one versus the other are quite different!

I will be using my own machine for this.

---

### Post by kaldor on 2010-11-03
> **robsonic said:**
> I currently have the 10.04 Desktop release of Ubuntu, should I go ahead and upgrade to the 10.10 release?

I greatly advise users to never upgrade their OS. Do a clean install instead. Upgrades are known to cause issues.

As for hosting servers, I also recommend trying out CentOS as well. Here's a quick comparison:

_Ubuntu Server Edition_

- LTS versions with 3 years of support. I recommend you use 10.04 for hosting.

- Relative ease, paid support available.

- Up to date software AND low system requirements (I am running it on 500 mhz and 85 mb of RAM

- No Desktop/GUI option on installer (last time I installed was 8.04... I may be wrong)

_CentOS_

- Based on RedHat Enterprise Linux making it a reliable "standardized" platform.

- Stable and well-tested. 

- Lots of software options for different needs on the installer.

- GNOME and KDE desktop options on installer.

---

### Post by e24ohm on 2010-11-03
> **kaldor said:**
> I greatly advise users to never upgrade their OS. Do a clean install instead. Upgrades are known to cause issues.

As for hosting servers, I also recommend trying out CentOS as well. Here's a quick comparison:

_Ubuntu Server Edition_

- LTS versions with 3 years of support. I recommend you use 10.04 for hosting.

- Relative ease, paid support available.

- Up to date software AND low system requirements (I am running it on 500 mhz and 85 mb of RAM

- No Desktop/GUI option on installer (last time I installed was 8.04... I may be wrong)

_CentOS_

- Based on RedHat Enterprise Linux making it a reliable "standardized" platform.

- Stable and well-tested. 

- Lots of software options for different needs on the installer.

- GNOME and KDE desktop options on installer.

Kaldor is correct. Use the LTS versions, or you will have to update in a short time. CentOS is rpm based, so some commands will be different. In addition, CentOS does not go out of date as fast as the standard version of Ubuntu, and that is why Kaldor is recommending the LTS version.

LTS give you a longer service life; however, this is really not needed if you are in a test environment.

---

### Post by ArgusVision on 2010-11-03
I agree with hot_rod_hippie, stick with 10.04. Especially for a server.
+1 for webmin
I'm personally on the fence about adding apache to the desktop vs. installing server and adding a gui.
If you're just starting out, yes desktop is easier to navigate and work on learning about linux. However, if you're building a server it's hard to beat 'server'.

---

