---
title: "insatlling madwifi"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by dubs on 2007-04-24
Hi all


Need help to understand to install MADWIFI driver. So far I use this command:


sudo -s
#enter password

apt-get -y install build-essential bin86
That command line work perfectly.

The next command line I have trouble.
cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi
make clean
make
make install

The result:
root@steven-laptop:~# cd /usr/src
root@steven-laptop:/usr/src# wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
--12:55:28--  [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
           => `madwifi-cvs-current.tar.gz'
Resolving madwifi.otaku42.de... 217.24.0.78
Connecting to madwifi.otaku42.de|217.24.0.78|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:55:29 ERROR 404: Not Found.


Please help

Thank you

---

### Post by kpjoyce on 2007-04-24
I followed the same HOWTO.  It is many months old at this point, and the online repository it used to download the madwifi code no longer works.

You'll need to find the latest madwifi code somewhere else.  I'll see if I can remember where I found it, but madwifi.org is a good start.

I hope the recompile solves your problem.

Kevin

---

### Post by dubs on 2007-04-24
HI keven


I try looking for new code @ madwifi.org but all code give me a error or file not find.

---

### Post by stchman on 2007-04-25
> **dubs said:**
> Hi all


Need help to understand to install MADWIFI driver. So far I use this command:


sudo -s
#enter password

apt-get -y install build-essential bin86
That command line work perfectly.

The next command line I have trouble.
cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi
make clean
make
make install

The result:
root@steven-laptop:~# cd /usr/src
root@steven-laptop:/usr/src# wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
--12:55:28--  [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
           => `madwifi-cvs-current.tar.gz'
Resolving madwifi.otaku42.de... 217.24.0.78
Connecting to madwifi.otaku42.de|217.24.0.78|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:55:29 ERROR 404: Not Found.


Please help

Thank you

Madwifi has moved to a new server.  Follow my procedure to install madwifi drivers.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I have hosted the madwifi drivers on my website.

I hope this helps.

---

