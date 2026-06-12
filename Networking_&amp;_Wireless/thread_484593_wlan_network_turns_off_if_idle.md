---
title: "wlan network turns off if idle"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by waylow on 2007-06-26
I am running Ubuntu Studio (Feisty) with a wireless network

it all works good except if the network remains idle for about 10 or 15 mins (ie. I am not transferring any information from the internet or other computers) the network seems to break.

the icon says it is still connected however I cannot ping any machine and the only way to get it working again is to run these commands in one terminal while pinging the router in another
```

sudo ifdown wlan0;sudo ifup wlan0

```

or 
```

sudo /etc/init.d/networking restart

```

sometimes it will restart straight away other times i will have to execute the commands 2 or 3 times. 
if it remains actively transferring data it doesn't break (eg Bit torrent or DL'ing)

any things I should try to get it to stop breaking?

---

### Post by waylow on 2007-07-09
bump

---

### Post by waylow on 2007-07-13
I think I have solved the problem

I set up my card Lynksys WMP54g - Broadcom 4306 chipset  
to use the ndiswrapper driver but when i ran the command

ndiswrapper -l
the driver listed was wrong

therefore i removed ndiswrapper and used the native driver that is compiled in the kernel
BCM43xx
according to here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")

I haven't had any issues so far

---

