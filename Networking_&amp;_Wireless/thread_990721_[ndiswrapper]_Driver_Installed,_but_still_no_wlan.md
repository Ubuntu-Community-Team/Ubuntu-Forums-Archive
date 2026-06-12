---
title: "[ndiswrapper] Driver Installed, but still no wlan"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by EggMasta on 2008-11-23
Hey all. I just installed a fresh copy of intrepid ibex. I have a broadcom 4318 wireless card in my hp dv5000 and i just installed the bcmwl5 drivers for it. ndiswrapper -l gives me:
```
ndiswrapper -l
bcmwl5: driver installed
        device (14E4:4318) present (alternate driver: ssb)
```

It seems to be installed and recognized, but still the light on my laptop is off and I cant access any of my network connections. Any help?

---

### Post by kevdog on 2008-11-23
Here is what you want to do.  

Open a terminal and type:
sudo tail -f /var/log/syslog

In a second terminal, unload and reload ndiswrapper
sudo rmmod ndiswrapper
sudo rmmod b43 
sudo rmmod ssb
sudo modprobe ndiswrapper

Does the syslog being displayed in the first terminal window give you any indication of what error is happening?

---

### Post by Joe2Shoe on 2008-11-23
egg,
I just did a fresh install of v8.10 (Intrepid Ibex) on my HP dv9000z.
My wifi card is the Broadcom BCM4312 rev. 02.
I did not use NDISwrapper or FWcutter.
I used the driver Ubuntu provided in System/Administration/Hardware Drivers.
It is listed as "Broadcom STA wireless driver".  I clicked on it and 'activated' it, now my wireless connection works, using "WPA & WPA2 Personal".
I am dual-booting ubuntu v8.10 and Vista.
My wireless works in both.

I installed the Windows Broadcom drivers (bcmwl6.sys" and "bcmwl6.inf) for my card using NDISwrapper just to see if they worked, and they did NOT!  I had to uninstall them and go back to the "Broadcom STA wireless driver".

---

### Post by Ayuthia on 2008-11-23
> **Joe2Shoe said:**
> egg,
I just did a fresh install of v8.10 (Intrepid Ibex) on my HP dv9000z.
My wifi card is the Broadcom BCM4312 rev. 02.
I did not use NDISwrapper or FWcutter.
I used the driver Ubuntu provided in System/Administration/Hardware Drivers.
It is listed as "Broadcom STA wireless driver".  I clicked on it and 'activated' it, now my wireless connection works, using "WPA & WPA2 Personal".
I am dual-booting ubuntu v8.10 and Vista.
My wireless works in both.

I installed the Windows Broadcom drivers (bcmwl6.sys" and "bcmwl6.inf) for my card using NDISwrapper just to see if they worked, and they did NOT!  I had to uninstall them and go back to the "Broadcom STA wireless driver".This option does not work with the 4318 card.  The Broadcom STA driver only works with the 4311, 4312, 4321, 4322, and 4328 cards.  Also the Vista drivers (bcmwl6) will not work with NDISwrapper.  They are not supported yet.

---

### Post by EggMasta on 2008-11-23
> **kevdog said:**
> Here is what you want to do.  

Open a terminal and type:
sudo tail -f /var/log/syslog

In a second terminal, unload and reload ndiswrapper
sudo rmmod ndiswrapper
sudo rmmod b43 
sudo rmmod ssb
sudo modprobe ndiswrapper

Does the syslog being displayed in the first terminal window give you any indication of what error is happening?

Tried that and no dice. Still no light or wireless networks present. And the syslog didnt work because it kept demanding the removal of a sd card that someone jammed into the wrong slot in my multireader... dont ask.

Anyone got any other ideas? its killing me!

---

### Post by Olivier2371 on 2008-11-23
Please do not pay attention to the led for your wireless, it works only on some laptop. My laptop led is off for the wireless. This is not an indication that your wireless is working or not.

---

### Post by EggMasta on 2008-11-23
I figured it out you guys. Thanks so much! Turns out i forgot to blacklist ssd. It works great now!

---

### Post by Olivier2371 on 2008-11-23
If your problem is solved could you mark it as solved.

---

