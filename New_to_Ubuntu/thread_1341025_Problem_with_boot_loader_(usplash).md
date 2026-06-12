---
title: "Problem with boot loader (usplash)"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by k33bz on 2009-11-29
I just made my laptop a dual boot with both ubuntu 9.04 and Backtrack 4.

Ubuntu has been on there. When I installed BT4 the grub got installed again, this time on BT4. So prety much I have Grub installed twice on my computer. Not sure if that makes a difference. 

Anyway, Once I installed BT4 my Grub splash was no longer there. BT4 did not have a boot loader. But Ubuntu did. Did some reconfiguring on the new menu.lst that was on the BT4 side. No surprise, got my grub splash back and got BT4 a boot loader. 

But now the problem is my Ubuntu side does not run its boot loader. Any help will be apprecieated. I know there is a way to have a boot loader on both OS's.

---

### Post by k33bz on 2009-11-30
bump

---

### Post by sandyd on 2009-11-30
look here
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
the ubuntu version of grub was wiped off the MBR by the other OS. so you need to reinstall the grub bootloader.
oh wait. your using grub v1 right?
in that case.....
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)
use the command line. its a bit safer.
p.s. make sure your using a version of ubuntu lower than 9.10 to restore grub. from 9.10 onwards, the default bootloader is grub2, not grub

---

### Post by k33bz on 2009-12-01
The grub isn't wiped off. My grub menu shows up. I get the boot loader when I run Back Track 4 (which is based off of Ubuntu Intrepid). However when I got to boot into Ubuntu Jaunty I dont have my Boot Loader screen no more. :(

---

### Post by k33bz on 2009-12-04
bump

---

