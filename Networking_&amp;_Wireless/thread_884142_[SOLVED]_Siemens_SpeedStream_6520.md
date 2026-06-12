---
title: "[SOLVED] Siemens SpeedStream 6520"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by ahmdgh on 2008-08-08
Hey guys,
I have a somewhat a long story here. I was using Ubuntu 8.04 on a Compaq Evo desktop, with a ADS: USB modem running the ueagle-atm driver. The only ISP here in Egypt (TE-Data, 00/35 VC/VP) has changed their settings to allow monitoring everyone's internet activity. They provided me with a password and username, so i added that to the ueagle-atm scrpit as well as the pap and chap secrets.
Everything was working fine until the April 6 strike, which was organized through facbook, so they are now insisting everyone uses a username/password and install their modem/router drivers from their website. One day i wake up, try to surf anywhere, and i get the TE-DATA page that i have to install the driver for my router, an .exe file, before i can do anything. So i hooked up the modem to my laptop (running XP) and it worked fine.
I suspected the Ubuntu installation, so i reinstalled it using the 7.10 version i have, tried to get the modem to work like before using this [https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)
Followed all the steps perfectly until i got to pon ueagle-atm, and i gives me this error:
```
Plugin pppoatm.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/ueagle-atm: unrecoginzed option '00.35'
```

So i tried editing the ueagle-atm with gksudo gedit to "00.35", <00>.<35> and numerous other forms but it still gives me an error.

I decided to drop all this and used a Speedstream 6520 siemens modem, and i followed this thread [http://ubuntuforums.org/showthread.php?t=318154](http://ubuntuforums.org/showthread.php?t=318154) but my ifconfig command displays three things instead of two! I have eth0, lo and eth0:avah.

I have no more ideas after that. My ISP doesnt offer technical support for linux, and even with windows (after calling 5 times) the connection is laggy and some pages like yahoo dont even load!! The tech guy says there is a problem with my laptop, so i am now trying with my linux desktop to get it back up.

Any ideas?

Thanx!!

---

### Post by ahmdgh on 2008-08-11
I thought the Ubuntu community would be have been kinder to me, or perhaps admins thought "the !@#$in stupid questions those towel-heads come up with??" :P ..anywho.. it worked!!!

The problem i had was to access the Siemen's router setting page, i got around that by hooking it up to the ethernet port of a WinXP laptop. The settings of the Local area connection have to be assigned, the IP, Subnet mask and default gateway for it to actually connect. Once connected, the router settings page loads and you change the ISP connection settings to PPPoE, with the same numbers 00/35 and it works like a charm!! 

I had it with PPPoATM and it was driving me crazy with the ISP's page showing everytime i surf anywhere. Hooked up the ethernet to my Ubuntu 7.10 desktop and i have internet!


The Aztech 208U modem however is still not working, i cant figure out what am i doing wrong here, but i cant enter those VP/VC numbers in a way that pleases the pon ueagle-atm command!!


Peace out

---

### Post by david0075 on 2008-08-13
hey ahmdgh,

im also trying to setup my usb modem. i have found a bit but it doesnt work for me. go to [http://ubuntuforums.org/showthread.php?p=5579510#post5579510](http://ubuntuforums.org/showthread.php?p=5579510#post5579510) . ive read a couple of things, and this is what ive done so far. perhaps if you ask there, someone will come along and answer all questions.

---

