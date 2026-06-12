---
title: "Dell wlan 1370 disabled in ubuntu 8.10"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by DragoNet on 2009-01-11
I installed 8.10 on my laptop (dual boot w/XP) and for some reason my wireless card shows as disabled. I tried the switch on my keyboard, downloaded the driver, installed it with windows wireless driver, activated with hardware drivers and nothing, still not working!!!:confused:

I was able to connect to the internet using a wired connection with no problems.

If you can give me some advise it would be great!!!!

Thanks

---

### Post by yobird42 on 2009-01-11
have you tried ndiswrapper? 
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

---

### Post by DragoNet on 2009-01-11
I was checking the network icon and saw my wireless router there....:KS I really don't know what happened but now I have wireless... thanks for your replay yobird42 !

---

### Post by yobird42 on 2009-01-11
cool. If this happens in the future just type in sudo ifconfig wlan0 in terminal. my wireless card doesn't show up until I type this.

---

### Post by cresusillo on 2009-01-20
hey, i have the same problem and i tried typing in 'sudo ifconfig wlan0' in the terminal and i haven't noticed any change in my network availability. do i have to install a specific driver for the wlan 1370?

---

### Post by cresusillo on 2009-01-20
I just input lspci -nn in the terminal and the resulting info on the network controller is as follows:

03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Does that help point anyone in the right direction?  Because that's pretty much Greek to me!!

---

### Post by cresusillo on 2009-01-20
Oh yeah, and I'm connected through an ethernet cable right now but I would love to have the wireless capability back again! ;)

---

### Post by cresusillo on 2009-01-20
another tidbit... when i entered 'ndiswrapper -l' into the terminal window the response was:

Error: no ndiswrapper utils found!

I was hoping it would detect the wireless card but no such luck.  maybe ubuntu just doesn't like the wlan 1370??

---

### Post by cresusillo on 2009-01-21
nevermind!  i found my solution on in another thread on here!!! now i'm up and running. couldn't be happier!! :-D

---

### Post by jyarhi on 2009-02-03
I have the same network adapter and the same problem. Where did you find the way to fix it...? Can someone please help me...

---

