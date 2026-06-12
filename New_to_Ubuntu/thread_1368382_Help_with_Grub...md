---
title: "Help with Grub.."
date: 2009-12-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-12-30
I installed ubuntu on a to a partition on my Dell Inspiron 1525 (the other partition currently contains a retail install of Mac OS X with the Chameleon bootloader) although grub has an option to boot OS X I believe it tries to boot using the usual OS X bootloader and not with the Chameleon bootloader

Any help would be gratefully received.

PS: Sorry if this is in the wrong section but theres a few places were it could of gone...

---

### Post by kamitsukai on 2009-12-30
Just thought I'd mention that I've solved the problem by editing /boot/grub/grub.cfg however every time there's an update to grub or the kernel I assume I'd have to redo the following?

```
sudo chmod 644 /boot/grub/grub.cfg
```&

```
sudo gedit /boot/grub/grub.cfg
```and then change the OS X option to _one_ of the following (bear in mind that partition/drive numbers may be different on your setup):

```
menuentry "MacOS X, chameleon, multi" {
         insmod hfsplus
         set root=(hd0,2)
         multiboot /boot
 }
```or

 ```
menuentry "MacOS X, chameleon" {
         insmod hfsplus
         search --file --set=root /boot
         multiboot /boot
 }
```Taken from: [http://www.insanelymac.com/forum/index.php?showtopic=189079&st=0#entry1313225](http://www.insanelymac.com/forum/index.php?showtopic=189079&st=0#entry1313225)

---

### Post by gabo.cr on 2009-12-30
Nice done.
Chameleon can boot Ubuntu also, but it is better if you keep using Grub.
The bad thing is that I like the Chameleon splash image better.

You should get a warning every time there is an update for Grub, and it will give you the option to re-write Grub or not.

---

### Post by kamitsukai on 2009-12-30
> **gabo.cr said:**
> Nice done.
Chameleon can boot Ubuntu also, but it is better if you keep using Grub.
The bad thing is that I like the Chameleon splash image better.

You should get a warning every time there is an update for Grub, and it will give you the option to re-write Grub or not.

Okay cool thanks for the info =] and I have to agree chameleon definitely wins the look factor:)

---

