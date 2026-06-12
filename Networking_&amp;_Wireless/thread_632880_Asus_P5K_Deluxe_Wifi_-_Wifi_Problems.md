---
title: "Asus P5K Deluxe Wifi - Wifi Problems"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by BRISKbaby on 2007-12-05
Hello, 
I'm new to Linux (you're probably hearing that a lot lately) and I'm having some wifi trouble (You're probably hearing that a lot lately as well).

I'm dual booting Vista 64 and Linux 64. I fixed the grub loader so I can get back into vista. The problems I'm having are using the WPA Wifi connection in my home. With a fresh install I cannot configure the Wifi via network (or network setup). The entry exists but has no attributes and is grayed out. I figure this is a driver issue. 

Asus provides linux drivers for the wifi card, however they fail to compile giving errors. I tried the last Ubuntu 32 bit and had the same problems. I found the following [thread]("http://ubuntuforums.org/showthread.php?t=626887") that states that the wifi drops, but I can't get it to work in the first place. Any workarounds or suggestions? (The Wifi does work in Vista)

Thank you,

BRISK

---

### Post by kevdog on 2007-12-06
Sounds like you have a realtek chipset.  Can you post

lspci -nn
lshw -C network

to confirm?

---

### Post by BRISKbaby on 2007-12-06
It is a realtek chipset.

I can post that info, but it will take a while. I can't see Linux from vista (vise versa either).

EDIT:
From the specs it is > RTL8187 Linux driver version 1.1I have work in the morning, any help you can provide would be greatly appreciated.

---

### Post by kevdog on 2007-12-06
Thats a very problematic chipset.  Do you possess windows xp and win98 drivers or have access to them from the manufacture's website?  The built-in linux driver sometimes works for these devices (at least it did in Fesity). Im not aware of anything that has been reported to be different in Gutsy.  ndiswrapper with the win98 driver has been reported to be the most reliable for many, however we can try the built-in driver if you want.

---

### Post by BRISKbaby on 2007-12-06
I do have xp drivers. I'll check out your guide and see what I can do to get this working. I'll check back with results and for help.

---

### Post by kevdog on 2007-12-06
You are likely going to need the win98 drivers, not the winxp drivers.  Try with the winxp drivers, but if things dont work, just remember I told you so!

---

### Post by BRISKbaby on 2007-12-11
> **kevdog said:**
> You are likely going to need the win98 drivers, not the winxp drivers.  Try with the winxp drivers, but if things dont work, just remember I told you so!

Well, I found the win98 drivers and followed your tutorial ([http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)) until this section "Verification/Modification of /etc/iftab file" and that's where the problems start. I have wlan0 and wlanmaster (or something like that). I configured (through the network GUI) the WPA2 needed but it doesn't connect. What information do you need to help me out more?

---

