---
title: "Hibernation Not Working In My Triple Boot"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2010-01-24
This is running Ubuntu 9.10, which when I ran as a single boot hibernation did work. Im currently running a GPT/MBR hybrid triple boot. On the first partition is a EFI partition (for OSX bootloader), next partition Snow Leopard, next partition Shared Data, next partition Windows 7, and finally Ubuntu 9.10. Now I installed the Grub bootloader on the Ubuntu 9.10 partition (not as a seperate /boot partition) and didn't make a swap partition. Anyway all three OS's work perfectly, expect that hibernation doesn't work in Ubuntu. What happens is instead of hibernation it blacks out and locks the screen. Any ideas what could be causing hibernation to fail?

---

### Post by Mahngiel on 2010-01-24
There's a known bug with Ubuntu 9.10 - Karmic on this hibernation issue.  The link eludes me at the moment, but know that you're not alone.  The priority for this bug hasn't even been determined yet, but it IS still present in 10.04.

So you know, I'm running the Ubuntu Studio kernel 2.6.31.9rt, and hibernation works perfectly whereas karmic's default doesn't shine.

---

### Post by RookieUbuntuUser58 on 2010-01-24
Wow thanks for the info. Didn't know this was a bug, actually thought it wasn't working because of my setup or something.

---

