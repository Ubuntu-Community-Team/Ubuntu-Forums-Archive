---
title: "Dell Vostro 1500 Wireless"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by gotron on 2008-11-24
I could not really find an exact fix for what is wrong on my end for the wireless problem in Ubuntu 8.10

Well i followed some tutorials on how to get the wireless working... well i installed the windows xp driver for my wireless card on Ubuntu... and it is still not working the only effect i see is it has permanently disabled the wl restricted driver and i can't enable it even after the reboot.

please tell me any information i need to post and i will asap.

also  if this will help i'm running the 64 bit desktop edition.

also the driver is installed this is what i got when i typed sudo ndiswrapper -l

> matthew@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: wl)
matthew@ubuntu:~$ 


---

### Post by gotron on 2008-11-24
nevermind i got it to work :D

---

### Post by sirjoebob on 2008-11-24
Good that you got it working. Which wireless card do you have anyways? I didn't have to fiddle with NDSWRAPPER or any of that nonsense because mine was supported in the restricted driver manager.

---

### Post by gotron on 2008-11-24
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

is my wireless card lol.

just wondering is there anyway to make games run better... i tried running css ran okayish sept abit of lagg and also the sound lagged very badly any fix on this?

im using wine.

---

### Post by sirjoebob on 2008-11-24
> 0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Same wireless card here. To get mine working, I only had to go to System>Administration>Hardware Drivers. Then just enable the restricted drivers for the wireless and also your Nvidia card if you havent already. this may be the issue you were having with gaming :)



I have no issues with any steam games (including L4Dead demo...) I have set hl2.exe to run in win98 mode under winecfg before. That seems to help quite a bit.

---

### Post by gotron on 2008-11-24
ugh lol i tried finding the hl2.exe but i cant seem to browse my external hard drive -.- and no its not my hard drive or maybe it is idk but it runs perfect on windows xp with the hard drive lol.

---

### Post by sirjoebob on 2008-11-24
Is it installed within WINE or are you running your windows install? To find files in wine, go to home/.wine/drive_c

You get there by going to your home folder and hitting ctrl+h to view hidden files and then find .wine

IF you are running from a windows installation, that is probably part of your issue. Also, in winecfg you can just type the exe and dont have to really search it out- worked for me. 

Have you installed the restrcited video drivers for your graphics card?

---

### Post by gotron on 2008-11-24
yes i have installed them.

---

### Post by sirjoebob on 2008-11-24
Did you install Steam, etc within WINE or are you using the install from your Windows?

---

### Post by gotron on 2008-11-25
the install from windows

---

### Post by sirjoebob on 2008-11-25
That is probably the cause of your issue. Try installing it in wine. Download the steam installer and go from there. I didn't think that programs would run at all in that configuration.

---

### Post by gotron on 2008-11-26
ill give it a shot

---

### Post by sirjoebob on 2008-11-26
> **gotron said:**
> ill give it a shot

Good luck. let me know if you need any further help.

---

