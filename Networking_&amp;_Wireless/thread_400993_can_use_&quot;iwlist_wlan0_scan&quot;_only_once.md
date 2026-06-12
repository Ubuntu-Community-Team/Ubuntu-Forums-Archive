---
title: "can use &quot;iwlist wlan0 scan&quot; only once"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by 01ago on 2007-04-04
I'm really new to Ubuntu, though I have tried several versions.
I gave up 7.04 because of network manager.
Now I've installed Ubuntu 6.10 on my laptop with a wireless card TP-Link WN321G(RaLink RT73)

However, I have encountered problems installing wireless and connecting to network.
I had a post a week ago, no one responded.
[http://ubuntuforums.org/showthread.php?t=391623](http://ubuntuforums.org/showthread.php?t=391623)

I think the main problem is on the driver. [B]I use ndiswrapper(installed from 7.04 herd3 CD-ROM) +Ralink Driver under WinXP(rt73.ini, rt73.sys, rt73.bin three files). installing was successful, by following commands, 
> $ sudo ndiswrapper -i rt73.inf 
$sudo ndiswrapper -m 
$ sudo modprobe ndiswrapper 
but there is a strange thing that I can only use "iwlist wlan0 scan" once everytime I have started Ubuntu. Only in the first time, I am able to get some results. There is always "no scan results" afterwards, no matter how close I'm to the AP.[/B]

I wonder if it is the problem causing failure in connecting a network.
Who can tell me?:( :confused:

---

### Post by nukie77 on 2007-04-06
I have a simmilar problem.  I live in NYC, so I normally get about 15 results from any given scan.  Most of the times that I run a scan, with network-manager-gnome install, I can get one good scan, but every scan after that will only show one unencrypted network.  anyone have any ideas what might be going on?

---

### Post by Floppyjoe on 2007-04-06
> but there is a strange thing that I can only use "iwlist wlan0 scan" once everytime I have started Ubuntu. Only in the first time, I am able to get some results. There is always "no scan results" afterwards, no matter how close I'm to the AP.
Do you prefix this command with sudo. I have read that this commands needs sudo to function properly.

---

### Post by 01ago on 2007-04-08
> **Floppyjoe said:**
> Do you prefix this command with sudo. I have read that this commands needs sudo to function properly.

Yes, I did. Thank you for your help.
However, I have gave up ndiswrapper, and found the correct way to install rt73 driver by searching other posts on the forums. Now I'm using the so-called "serialmonkey" driver, and it works quite well!:lolflag: 

Maybe someone shall come and help [COLOR="Gray"]nukie77[/COLOR]?

---

