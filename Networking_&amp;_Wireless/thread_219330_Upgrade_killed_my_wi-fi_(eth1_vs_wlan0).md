---
title: "Upgrade killed my wi-fi (eth1 vs wlan0)"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by d3j4v00 on 2006-07-19
I have a Gateway M675 Notebook on which I intstalled Ubuntu 5.10 around a month ago, and was able to get my wi-fi chip running perfectly with ndiswrapper. Yesterday I upgraded to 6.06 LTS, and the wifi is messed up. It's not that the card is unrecognized, it's there, but it's set up as eth1 instead of wlan0

Is there a way to change it from eth1 to wlan0?

---

### Post by unconquerable on 2006-07-20
I have that same issue, I have been getting my wifi to work on and off with various fixes (blacklist ipv6).

This is a fresh install of dapper and it automatically recognizes my wireless card as eth1 and not wlan0, it recognizes my ethernet as eth0.  I can still put in an ssid and connect (sometimes) through it, should this be changed somehow to wlan0

---

### Post by awaldram on 2006-07-20
lookin iftab in etc 

it pretty self explanitary

---

### Post by d3j4v00 on 2006-07-20
> **unconquerable said:**
> I have that same issue, I have been getting my wifi to work on and off with various fixes (blacklist ipv6).

This is a fresh install of dapper and it automatically recognizes my wireless card as eth1 and not wlan0, it recognizes my ethernet as eth0.  I can still put in an ssid and connect (sometimes) through it, should this be changed somehow to wlan0

I tried the ipv6 fix, but it didn't seem to help. I'm not sure if it's supposed to be wlan0 or if eth1 works just as well, but it used to work when it was called wlan0 so I'm trying to get back to that.

> **awaldram said:**
> lookin iftab in etc 

it pretty self explanitary

Thanks, that got it back to being wlan0 so it remebered all of it's settings. 
---
Still does not work though. The notebook has this hardware button which is supposed to turn the wifi on and off (for saving power). The button has no effect any more, and the LED under it indicates that the wifi is deactivated.

I'm going to try reinstalling the drivers, but can anyone point me to where I could manually activate the card?

---

### Post by d3j4v00 on 2006-07-20
> **d3j4v00 said:**
> Still does not work though. The notebook has this hardware button which is supposed to turn the wifi on and off (for saving power). The button has no effect any more, and the LED under it indicates that the wifi is deactivated.

I'm going to try reinstalling the drivers, but can anyone point me to where I could manually activate the card?

Nevermind, I found a workaround! :D 
[http://www.linuxlaboratory.org/index.php?title=Talk:Welcome_to_LinuxLaboratory.org#Ubuntu_Dapper_Broadcom_Wireless_Issue](http://www.linuxlaboratory.org/index.php?title=Talk:Welcome_to_LinuxLaboratory.org#Ubuntu_Dapper_Broadcom_Wireless_Issue)

The internet is awesome.

---

