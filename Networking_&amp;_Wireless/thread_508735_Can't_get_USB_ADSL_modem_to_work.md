---
title: "Can't get USB ADSL modem to work"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by yakobb on 2007-07-24
Hi there,

  I have just installed Ubuntu 7.04 and my first order of business was to get it connected to the internet.. uh oh. 
I followed the guide here -> [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)  but to no avail. The modem I'm using is a USB Sagem Fast 800 E4 and my Isp is tiscali (here in the uk). Have checked all the passwords and the VP and Vc nos appear correct. After typing pon ueagle-atm I just get a message saying plugin so loaded. Plog gives me the following info everytime, with the modem lights on or off:

tom@tom-desktop:~$ plog
Jul 24 20:32:15 tom-desktop pppd[5840]: Plugin pppoatm.so loaded.
Jul 24 20:32:15 tom-desktop pppd[5842]: pppd 2.4.4 started by tom, uid 1000
Jul 24 20:32:15 tom-desktop pppd[5842]: connect(0.38): No such device
Jul 24 20:32:15 tom-desktop pppd[5842]: Exit.
tom@tom-desktop:~$ 

When started up, the lights on the modem are both off. If I unplug the USB cable and plug it back in the Lights both come on and stay on. I am dual booting with XP and everything in windows works fine so it's not a hardware issue.

Could someone suggest something? If I can't get this to work Im going to have to bail on ubuntu and just stick with boring windows...  

Thanks

---

