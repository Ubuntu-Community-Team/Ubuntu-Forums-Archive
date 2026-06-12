---
title: "Problem with Iw-0.9.11 &amp; Libnl"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by lollyhayes on 2009-04-18
I have tried to get airmon-ng to run, and set card to monitor mode. However when I do this this is what happens:

```

lawrence@lawrence-laptop:~$ sudo airmon-ng start wlan0


Found 6 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
5127	NetworkManager
5141	NetworkManagerD
5174	avahi-daemon
5175	avahi-daemon
5487	dhcdbd
5940	dhclient


Interface	Chipset		Driver

wlan0		Intel 3945ABG	iwl3945 - [phy0]

ERROR: Neither the sysfs interface links nor the iw command is available.
Please download and install iw from
[http://wireless.kernel.org/download/iw/iw-0.9.11.tar.bz2](http://wireless.kernel.org/download/iw/iw-0.9.11.tar.bz2)


lawrence@lawrence-laptop:~$ cd download
lawrence@lawrence-laptop:~/download$ ls -l
total 28
drwxr-xr-x 2 lawrence lawrence  4096 2009-03-26 11:01 iw-0.9.11
-rw-r--r-- 1 lawrence lawrence 23919 2009-04-18 10:45 iw-0.9.11.tar.bz2
lawrence@lawrence-laptop:~/download$ cd iw-0.9.11
lawrence@lawrence-laptop:~/download/iw-0.9.11$ ls -l
total 148
-rw-r--r-- 1 lawrence lawrence   849 2009-03-26 11:01 COPYING
-rw-r--r-- 1 lawrence lawrence  2433 2009-03-26 11:01 genl.c
-rw-r--r-- 1 lawrence lawrence  8388 2009-03-26 11:01 info.c
-rw-r--r-- 1 lawrence lawrence  6072 2009-03-26 11:01 interface.c
-rw-r--r-- 1 lawrence lawrence  1024 2009-03-26 11:01 iw.8
-rw-r--r-- 1 lawrence lawrence 11275 2009-03-26 11:01 iw.c
-rw-r--r-- 1 lawrence lawrence  2068 2009-03-26 11:01 iw.h
-rw-r--r-- 1 lawrence lawrence  1735 2009-03-26 11:01 Makefile
-rw-r--r-- 1 lawrence lawrence  7256 2009-03-26 11:01 mesh.c
-rw-r--r-- 1 lawrence lawrence  4754 2009-03-26 11:01 mpath.c
-rw-r--r-- 1 lawrence lawrence 36869 2009-03-26 11:01 nl80211.h
-rw-r--r-- 1 lawrence lawrence  2170 2009-03-26 11:01 phy.c
-rw-r--r-- 1 lawrence lawrence   464 2009-03-26 11:01 README
-rw-r--r-- 1 lawrence lawrence  4991 2009-03-26 11:01 reg.c
-rw-r--r-- 1 lawrence lawrence  5541 2009-03-26 11:01 scan.c
-rw-r--r-- 1 lawrence lawrence  6608 2009-03-26 11:01 station.c
-rw-r--r-- 1 lawrence lawrence  1480 2009-03-26 11:01 util.c
-rwxr-xr-x 1 lawrence lawrence   536 2009-03-26 11:01 version.sh
lawrence@lawrence-laptop:~/download/iw-0.9.11$  make
Makefile:33: *** Cannot find development files for any supported version of libnl. Stop.
lawrence@lawrence-laptop:~/download/iw-0.9.11$ 


```

This has left me questioning:
a). do I need libnl & iw.
b). have I screwed up earlier and installed the wrong stuff etc... 
Any help appreciated, couldn't find anything else apart from this:
[http://www.aircrack-ng.org/doku.php?id=mac80211&DokuWiki=afca843b5c58a99930406b7aa45e2dd2](http://www.aircrack-ng.org/doku.php?id=mac80211&DokuWiki=afca843b5c58a99930406b7aa45e2dd2)

But can't view it at the moment as there is site maintenance going on...

---

### Post by lollyhayes on 2009-04-19
bump

---

### Post by lollyhayes on 2009-04-21
bump -still can't work it out

---

### Post by simmo_11 on 2009-04-30
same problem. how to link to libnl?

---

### Post by GSS2 on 2009-06-06
make file says that you need to install libnl devel package.
after this problem should be solved. 

good luck.

---

### Post by davidmerrick on 2010-01-10
No doubt. Just grab the libnl-dev package off Syntaptic. Worked for me.

---

