---
title: "BCM4311 WLAN problems"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by ChristianSchaller on 2014-02-14
Hi,

just recently I installed LinuxMint 16 Petra on my old HP G7000.
Everything seems fine except the WLAN is not working.
The system output was:

[FONT=courier new]01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02) 
Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller
Kernel driver in use: b43-pci-bridge[/FONT]

I browsed through a number of web site and did the following:

[B]1. I tried
[/B]
[FONT=courier new]rfkill unblock all
[/FONT]
-> no positive effects.

[B]2. To my understanding the systems uses the wrong driver. 

[/B]So I blacklisted b43-pci-bridge AND b43
After a reboot I had still the same effect.

[FONT=arial black][B][FONT=arial]3[FONT=arial black]. I tried to manually activate the driver ndiswrapper[/FONT][/FONT] 

[/B][/FONT]...but the system could not find the driver. Do I have to install that? How?

So until now the use of my linux machine is only very limited. Any help is greatly welcome ....

Best regards, Christian

---

### Post by varunendra on 2014-02-14
Welcome to Ubuntu Forums Christian !

So you seem to have furiously tried things that we strongly urge to refrain from (unnecessary blacklisting, ndiswrapper) :)

Please do these -

* Un-blacklist the drivers (there is no such driver as b43-pci-bridge, it is just an alias for b43+ssb, and b43 is the correct one for your card).
* Purge ndiswrapper if you have installed it.

Then with a wired connection, install the firmware for b43 -
```
sudo apt-get install linux-firmware-nonfree
```
Followed by a reboot. Does it work now?

If not, we may have to see what else need to be 'Undone'. To provide a detailed info, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by ChristianSchaller on 2014-02-14
Hi Varun,

thanks for your support! It works!! I am typing these words by using my wireless connection .....
It could have been so easy ...

Best regards,
   Christian

---

### Post by varunendra on 2014-02-14
Congratulations ! 

As long as you are using this card (BCM4311), the only thing you'll need (on ANY Linux distro) is the firmware for the native b43 driver. Once you have installed it, you won't need to install it again even across kernel upgrades. The only time when you'll need to reinstall it is if you do a fresh install again.

Enjoy Ubuntu and your wireless. :)

---

