---
title: "Uninstall GRUB"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by IgotsDibs on 2010-01-02
In case it isn't already abundantly clear, I am quite new to Ubuntu. Anyway, I tried to set up my computer so that I could boot XP off of the internal hard drive, or boot Ubuntu 9.10 from an external USB drive. I can get them to boot, but the problem is that when I unplug the external USB hard-drive, it can't boot XP saying: > GRUB LOADING
error: no such disk
grub rescue>

So what I'd like is to remove GRUB altogether and just use the XP boot loader. But I don't know exactly where GRUB is, nor how to uninstall it. If I remember correctly, when I installed Ubuntu it said that the boot loader was save to (hd0). It's GRUB 1.97 Beta, if that helps.

---

### Post by m4tic on 2010-01-02
grub is instald on ur usb. you should try dual booting ubuntu with xp on ur external hdd

---

### Post by talsemgeest on 2010-01-02
Take a look at my guide [here](http://ubuntuforums.org/showthread.php?t=1014708), you can either follow the instructions to install grub onto only your usb hdd, or to reinstall the xp bootloader.

---

### Post by IgotsDibs on 2010-01-03
Okay, so I booted it up with the XP CD and entered fixmbr, and that seems to have fixed the problem with XP. But then I couldn't get into Ubuntu, so I just reinstalled it onto the external hard drive again, but this time I saved GRUB to dev/sdb and that seems to have solved the problem. Thanks a lot.

---

### Post by CaptainMark on 2010-01-03
this is the best option, well done for figuring it out, most new guys have trouble with this. if you set your bios to boot from usb hdd first then if the usb is present it will boot ubuntu if it isnt it will boot windows, just what you want by the sounds of it

---

