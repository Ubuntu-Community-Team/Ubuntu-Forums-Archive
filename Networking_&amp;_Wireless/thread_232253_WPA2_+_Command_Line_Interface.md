---
title: "WPA2 + Command Line Interface"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by DarkAngel88 on 2006-08-08
Hi, 

I'm trying to configure ubuntu to work with my WPA2 network.  I've been following this guide ([http://ubuntuforums.org/showthread.php?t=194886&highlight=wpa2]("http://ubuntuforums.org/showthread.php?t=194886&highlight=wpa2"))
and works perfectly.  Only problem is that I'm using other networks using wep keys.  If I want to connect to those I have to manually edit the file in the guide 
to remove any traces of the wpa network.  Usualy, I was able to change between networks using little scripts that I made like this one : 

```
sudo iwconfig eth1 essid "MYESSID" key "MYWEPKEY"
sudo dhclient eth1
```

It was working perfectly.  Now I'd like to know if there is a way to configure my wpa2 network the same way I'm doing with those wep networks ??  
Like a single command line to connect to my WPA2 network.

Thank you very much for your help !!

---

### Post by bensexson on 2006-08-08
I do not believe there is a way normally.  I think a while ago I saw the iwpriv commands to control WPA for intel chipsets.  You may want to search the forum to see if you can find this.  I have a custom script I run a boot the loops through all of the networks I connect to.  It stops when it finds a connection and then makes a symbolic link to a interfaces file which then allows me to ifup and ifdown with the settings for the WAP I am connecting to.

---

### Post by DarkAngel88 on 2006-08-08
Is your script able to connect to a wpa network ?

---

