---
title: "Broadcom 4311 wireless on a Compaq Presario v6101us laptop"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by ejnoonan on 2007-02-15
Hi, 

I've followed this post:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29)

I've been trying to get the Broadcom 4311 to work with ndiswrapper 1.28 using a windows xp driver.  Somehow the computer is reading the wireless as eth1 instead of wlan0.  All I'm getting is no wireless extensions in iwconfig.  Any help would be greatly appreciated.

---

### Post by Eigenwert on 2007-02-16
You need to comment out the "eth1" line in /etc/iftab and then it should work:
```

sudo gedit /etc/iftab 

```
and put a "#" infront of the line with the "eth1" entry.

EW

Update: In my /etc/networking/interfaces I also had to comment out all other interfaces aside from lo and wlan0 by putting a # infront of all lines for the other devices. However, you may not need to do this. EW

---

### Post by ejnoonan on 2007-02-19
I did that and it still didn't work.  I even changed eth1 to wlan0 in interfaces.  Still nothing.

---

### Post by Eigenwert on 2007-02-19
What do
```
cat /etc/iftab 
```
and
```
cat /etc/network/interfaces
```
give you? (DON'T post your key, though!)

I would also double check and make sure you didn't miss steps in the guide. Sometimes I get ahead of myself and forget the ```
depmod
``` and ```
modprobe
``` commands at the end of step 5, and the ```
ndiswrapper -m
``` at the end of step 6.

Have you installed anything else, like the nvidia drivers, which effects your kernel?

EW

---

### Post by Devastator9 on 2007-02-20
Try this post here it worked for me on Broadcom 4311
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

