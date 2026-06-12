---
title: "Wireless WPA-PSK config ??????"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by pieter hollenberg on 2005-04-14
now running Ubuntu few months with much pleasure. it's a great distro.

but there is one thing that doens't want to work.

WPA-PSK encyrption on my wireless network with my neighbour (we share the costs)

chipset is Ralink rt2500

the driver is recognized and loaded, i can configure ssid, WEP, that's OK,

but I don't have some configuration tool thats really works to get WPA working.
I tried all howto I could find in all ubuntu forums.
but in every howto something goes wrong. (including wpasupplicant)

who has experience to get WPA-PSK working with ubuntu ??

thanx in advance !

---

### Post by luca_linux on 2005-04-15
Yes, but I have an ipw2200. I've never tried your card, but maybe you need to install wpa_supplicant in order to get support of wpa authentication.

---

### Post by genecaldwell on 2005-04-16
I found this( [https://www.ubuntulinux.org/wiki/WPAHowto )](https://www.ubuntulinux.org/wiki/WPAHowto )), but I am having the very same problem you are, but in my case, I just don't know what I am doing because I have only been using linux for less than a week now. I wish Ubuntu would add WPA-PSK to the default install configuration.  if any one can help someone so new to linux that they are still wet get this working I would be gratefull.  :-| I guess what I am saying is that I don't want to wait 6 months or a year trying to learn linux inorder to figure out how to secure my computers from the bad guys. WEP is configured just fine, but thats just not secure enough, I had to turn WPA off to get this laptop to connect to my AP, and now my other computers do not have WPA security. this linux machine will be the most insecure I have untill I can get WPA functioning - my other computers are win32 machines.  This Untubu Linux it the only linux I have ever seen that made me want to try it and learn it. but I have got to start from a secure begining. I think Ubuntu did an awesome job getting me just to try it, I am very open minded and looking forward to more if I can get the security and protection I want.

---

### Post by luca_linux on 2005-04-17
I wrote this howto, maybe can help: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by Ezzet on 2005-04-19
I'm using a script like this:

#!/bin/sh
echo "ISP name"
ifconfig ra0 up
echo "starting network"
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set SSID="your ESSID"
iwpriv ra0 set WPAPSK="your wpa-psk key here"
iwpriv ra0 set SSID="your ESSID"
echo "WAIT for connection!"

I got help from here [http://sourceforge.net/forum/forum.php?forum_id=370891](http://sourceforge.net/forum/forum.php?forum_id=370891)

I hope this helps you!

---

### Post by Yaniv on 2005-04-24
I got wpa working on rt2500 using th RaConfig utility. You can follow the instructions at [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) to see how to compile and use it.

---

### Post by scottylans on 2005-08-09
[QUOTE=Yaniv]I got wpa working on rt2500 using th RaConfig utility. You can follow the instructions at [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) to see how to compile and use it.[/QUOTE]


I am following the howto - but I can't get the raconfig to work.
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

(Step 6, part 2 - RA config)

> 
6. In the Terminal, type:

sudo ./path/to/RaConfig2500

You can also run RaConfig by double-clicking on it, from either a root Nautilus or Konqueror window (sudo nautilus, sudo konqueror). 




root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys # sudo ./path/to/RaConfig2500
**sudo: ./path/to/RaConfig2500: command not found**
root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys #

---

### Post by srijith on 2005-08-10
[QUOTE=scottylans]I am following the howto - but I can't get the raconfig to work.
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

(Step 6, part 2 - RA config)

root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys # sudo ./path/to/RaConfig2500
**sudo: ./path/to/RaConfig2500: command not found**
root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys #[/QUOTE]
You have to substitute "./path/to/RaConfig2500" with the actual path of your RaConfig2500 script/binary. If you don't know where it is located, try
```

which RaConfig2500

```
or 
```

locate RaConfig2500

```

---

