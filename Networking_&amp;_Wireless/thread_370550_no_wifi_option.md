---
title: "no wifi option"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by longrunner on 2007-02-25
After about a month of trying to figure out how to make my wireless connection work with a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card.  Its a different one, it doesn't fit the standard how-to here on the forums.  I finally was able to install a driver bcmwl5.inf, but as soon as I was able to install this windows driver under ndiswrapper my option for wireless connections dissapeared under the networking menu.

I blacklisted the bcm43xx driver.  (interesting note, i had to log in as root and manually change this file, couldn't call it up from sudo).

If anyone can help me use this installed wifi card driver, or find another driver, and restore my wi-fi option I would be very grateful.

thanks

---

### Post by ukripper on 2007-02-26
> **longrunner said:**
> After about a month of trying to figure out how to make my wireless connection work with a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card.  Its a different one, it doesn't fit the standard how-to here on the forums.  I finally was able to install a driver bcmwl5.inf, but as soon as I was able to install this windows driver under ndiswrapper my option for wireless connections dissapeared under the networking menu.

I blacklisted the bcm43xx driver.  (interesting note, i had to log in as root and manually change this file, couldn't call it up from sudo).

If anyone can help me use this installed wifi card driver, or find another driver, and restore my wi-fi option I would be very grateful.

thanks

If you have bcm4318 then definitely I recommend  follow this [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) guide as instructed and you won't have any problems with your wireless card anymore. It took me 2 minutes to setup my wireless card on my acer 3003lmi with bcm4318 yesterday, hope it is helpful.

---

