---
title: "Apt-get is using tor?"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by jesc on 2011-03-27
Hey there,
I decided to test tor with polipo and vidalia. upon removing apt-get update results in the following error. 

Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Could not connect to 127.0.0.1:8123 (127.0.0.1). - connect (111: Connection refused)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Could not connect to 127.0.0.1:8123 (127.0.0.1). - connect (111: Connection refused)
Err [http://ppa.launchpad.net/ailurus/ppa/ubuntu/](http://ppa.launchpad.net/ailurus/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ailurus/ppa/ubuntu/](http://ppa.launchpad.net/ailurus/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg

....and so on

 I have since removed both polipo and vidalia and the problem persists.
How can I get apt-get to stop attempting to use loopback?

   
Any help is greatly appreciated.

---

### Post by ikt on 2011-03-27
> **jesc said:**
> Hey there,
I decided to test tor with polipo and vidalia. upon removing apt-get update results in the following error. 

Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Could not connect to 127.0.0.1:8123 (127.0.0.1). - connect (111: Connection refused)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Could not connect to 127.0.0.1:8123 (127.0.0.1). - connect (111: Connection refused)
Err [http://ppa.launchpad.net/ailurus/ppa/ubuntu/](http://ppa.launchpad.net/ailurus/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ailurus/ppa/ubuntu/](http://ppa.launchpad.net/ailurus/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en_US
  Unable to connect to 127.0.0.1:8123:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Unable to connect to 127.0.0.1:8123:
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg

....and so on

 I have since removed both polipo and vidalia and the problem persists.
How can I get apt-get to stop attempting to use loopback?

   
Any help is greatly appreciated.

can you post your /etc/apt/sources.list please

---

### Post by jesc on 2011-03-27
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Ailurus - [http://code.google.com/p/ailurus/](http://code.google.com/p/ailurus/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A6FE242
deb [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) maverick main

#### Wine - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

#### XBMC Media Center - [http://xbmc.org/](http://xbmc.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 91E7EE5E
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main


####### 3rd Party Source Repos

#### Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

#### XBMC Media Center (Source) - [http://xbmc.org/](http://xbmc.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 91E7EE5E
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main

---

### Post by Enigmapond on 2011-03-27
If you are not using TOR, remove it. Also check Preferences/Network Proxy and make sure the top is checked for "Direct Connection".

---

### Post by jesc on 2011-03-30
The problem is now solved.  It was a matter of going into the network proxy settings and changing it to direct connection "system wide".  I really appreciate the help.

---

### Post by Enigmapond on 2011-03-30
You are welcome! :P

---

