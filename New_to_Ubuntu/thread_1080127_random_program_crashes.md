---
title: "random program crashes"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-02-25
vlc totem mozilla and mythtv 
all crashing randomly especially when i have guests 
athlon 2000+
768 M ram
ati radeon 5200
40 GB hdd
hauppauge 15O_pvr
ubuntu doesnt crash though just the programs

---

### Post by mikechant on 2009-02-25
Two possibilities spring to mind:
Firstly, a graphics card driver bug - you could see if ATI have a more up to date Linux driver available for your card.

Secondly, I guess these programs are all quite memory intensive, so one possibility is that you have a dodgy area in your RAM (which Ubuntu itself doesn't happen to hit). You could try selecting the 'memtest' option from the grub boot menu and leaving it to run overnight.

Before you do anything else though you might as well try running one or more of the crashing apps from the command line and see if you get any error messages on the terminal when the crash occurs.

---

### Post by Arthur Millar on 2009-02-26
> **mikechant said:**
> T

Before you do anything else though you might as well try running one or more of the crashing apps from the command line and see if you get any error messages on the terminal when the crash occurs.



mythtv output 
Segmentation fault


mozilla had no terminal errors

---

