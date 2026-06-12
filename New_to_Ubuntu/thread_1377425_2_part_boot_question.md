---
title: "2 part boot question"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by richie3418 on 2010-01-10
I recently got back to Ubuntu and installed it on a hard drive with xp. I only had the Ubuntu Hardy Heron LTS 8.04 so it is on there with the xp and working ok.
#1. If I downloaded the new version and put it on a cd how would you install it. You can't boot from the cd because when it asks for the size of space it only shows the xp partition on the hard drive, it doesn't show that I already have Ubuntu on it. I was already told I can upgrade to the 10.4 LTS straight from my 8.04. I just wanted to know how to do it from a cd if I ever wanted to.
#2. I was talking to my Hughes satellite tech yesterday about my downloads slowing during certain times. He went through some things then he wanted me to reboot to F8 for safe mode. I tried and with this dual boot I can't seem to get there. I can get F2 & F12 but not what he wanted. Does anyone know how to boot into the F8 safe mode for windows when you have a grub boot?
I have a 320 GB. hard drive with windows on 220 gb and Ubuntu on the other 100 gb.

---

### Post by QLee on 2010-01-10
[QUOTE=richie3418]
#2. I was talking to my Hughes satellite tech yesterday about my downloads slowing during certain times. He went through some things then he wanted me to reboot to F8 for safe mode. I tried and with this dual boot I can't seem to get there. I can get F2 & F12 but not what he wanted. Does anyone know how to boot into the F8 safe mode for windows when you have a grub boot?
[/QUOTE]

The F2 and F12 are probably there before GRUB starts and are likely the BIOS entry point and boot menu point from your system.

To enter Windows safe mode,what works for me is push the F8 key immediately after pushing Enter when selecting XP from the GRUB menu. Immediately, before the progress bar is presented.

Naturally there would also be a "heavy handed" way to force Windows to show the Windows Advance Options Menu, crash the Windows while booting with a forced power off. Windows will notice and present the menu on next try to boot. Disclaimer, this is not recommended by either MicroSoft or me and might cause data loss or worse.

I wonder why he needed safe mode to troubleshoot a possible download problem.

---

### Post by richie3418 on 2010-01-11
Thank you for answering the second part, now I can get back to Hughes and find out why they wanted that function.

---

### Post by Elfy on 2010-01-11
I see that question 1 made it to a seperate thread. [http://ubuntuforums.org/showthread.php?t=1378176](http://ubuntuforums.org/showthread.php?t=1378176)

---

