---
title: "ANOTHER wireless thread-no WiFi showing on Network Settings"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Jetboy170 on 2008-08-06
Hello all,,  Very new (one week) to the Linux world. I have heard a lot about it and it seems to be something I want to get into. I am very much a novice.

I loaded Linux Ubuntu onto my new Dell Inspiron 1525, with a Dell Wireless 1395 802.11g Mini-Card (Broadcom BCM94312MCG). I have tried a lot of troubleshooting in the Help program on Linux, and a few of the thread on this forum. Still..When I iwconfig, I get:

no wireless extensions

Help please. Very fustrating. I know this is a tired subject, but WTF. Why cant this get figured out...:(](*,)

---

### Post by dca on 2008-08-06
To get my sister's to work I used either this how-to:
 
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
 
...or this:
 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
 
...I could've sworn after installing Ubuntu 8.04 w/ Broadcom 43xx it shows up as a pop-up under the 'restricted drivers' area of the tray.
 
Is it (Broadcom) listed when you go to 'System -> Administration -> Hardware Drivers' from the main menu bar?

---

### Post by superprash2003 on 2008-08-06
this helped me [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) ..follow this and do a reboot and im sure it should work!!

---

### Post by Peter0Pan on 2008-08-06
> **Jetboy170 said:**
> Hello all,,  Very new (one week) to the Linux world. I have heard a lot about it and it seems to be something I want to get into. I am very much a novice.

I loaded Linux Ubuntu onto my new Dell Inspiron 1525, with a Dell Wireless 1395 802.11g Mini-Card (Broadcom BCM94312MCG). I have tried a lot of troubleshooting in the Help program on Linux, and a few of the thread on this forum. Still..When I iwconfig, I get:

no wireless extensions

Help please. Very fustrating. I know this is a tired subject, but WTF. Why cant this get figured out...:(](*,)

I have the same issue and none of the solutions mentioned help. Network Manager doesn't show any wireless option neither does lspci | grep Broadcom shows the card :(

---

### Post by Jetboy170 on 2008-08-07
Update:

  I called Best Buy, talked to one of the Geek Squad peeps. He told me to bring it in. He hook the laptop up to he internet. There was like 240 updates available. We downloaded the updates...and bingo...Wireless network showed up on the manager. 

Now...the problem is...

My WiFi card will not communicate with the Linksys router. It doesnt show the proper IP address when I do ifconfig. I was on the phone with Linksys support for two hours trying to set SOMETHING up..No luck. This really sucks. 

ANY ideas at all? 

I will try to find the time to hook up to the hard line to get a screen shot of the ifconfig and post it on here.

---

