---
title: "Two Distros, One Not in Grub Bootloader"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-01-31
I'm currently using the grub bootloader installed by Ubuntu 8.10. I just added CrunchBang Lite to a new partition (/dev/sda8 ). CrunchBang Lite doesn't show up in the grub bootloader option. What would I have to add into the menu.lst to get it to show up? Reason I ask is I know Linux has special names (depending on kernel version), so how would I know what to name CrunchBang Lite in the menu.lst? Thanks in advance for any help.

---

### Post by rraj.be on 2009-01-31
Could you post me thecontent of

/boot/menu.lst and 

```
sudo fdisk -l 
``` From terminal

---

### Post by bumanie on 2009-01-31
You should only need to chainload the other distro
In the /boot/grub/menu.lst there should be a section that says This section for other debian based distros (or something to that effect - I'm at work on an M$ machine, so can't check) You should add something like this

title crunchbag
root (hd0,7)
chainloader +1

It should be added to the list and should be able to boot assuming you installed grub's root to sda8 during installation.

---

### Post by RookieUbuntuUser58 on 2009-01-31
Heres the output of sudo fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38b83a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5610    45062293+   7  HPFS/NTFS
/dev/sda2            5611       11347    46082452+  af  Unknown
/dev/sda3           11348       19457    65143575    5  Extended
/dev/sda5           11348       17183    46877638+  83  Linux
/dev/sda6           17184       17305      979933+  82  Linux swap / Solaris
/dev/sda7           17306       17317       96358+  83  Linux
/dev/sda8           18485       19457     7815591   83  Linux

```


I tried that Bumanie but when I selected it in Grub Bootloader it threw an error. Is this because I selected don't install boot loader when I was installing it (in advanced right before install)? I thought I had to do that to prevent my current Grub boot loader from getting overwritten.

---

### Post by RookieUbuntuUser58 on 2009-01-31
I just reinstalled and made sure I made the bootloader added to /dev/sda8. But I still get the same problem. When I click on Crunchbang added in Grub bootloader I get "Error 12: Invalid device requested."

---

### Post by bumanie on 2009-01-31
That's odd, I did the exact same thing when installing jaunty alpha 3 the other day ie the chainloader addition - it worked fine. Can you post teh output of > cat /boot/grub/menu.lstassuming you can boot into ubuntu.

---

### Post by RookieUbuntuUser58 on 2009-01-31
Okay got it to work sort of. I click on CrunchBang in the original Grub bootloader and it takes me to another Grub bootloader. There there is a bunch of Ubuntu versions (different kernels). I click the first Ubuntu option and it loads CrunchBang. I tried to edit the menu.lst in CrunchBang to fix this but it seems 

```
sudo gedit /boot/grub/menu.lst
``` 

isn't working. Says it doesnt recognize sudo gedit. Anyone know the lingo to edit the menu.lst in CrunchBang?

---

