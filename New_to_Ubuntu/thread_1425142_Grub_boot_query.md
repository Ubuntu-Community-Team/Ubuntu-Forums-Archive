---
title: "Grub boot query"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by boxcorner on 2010-03-08
I want Ubuntu to be my primary OS.  When I re-installed my OS's recently, I tried to put Ubuntu exclusively on my 1st drive and XP on the 2nd.  I had hoped that doing so would reduce the lengthy boot time.  However, when I installed XP, it insisted on grabbing a small partition on the 1st drive.  I installed XP first and then Ubuntu, because that was the only way I knew of getting a dual boot menu.  Now when I boot, there are 3 Ubuntu pairs before the XP option. Linux 2.6.31-20, below are 19 & 14, then the memtest and finally XP. My questions are: Why have I got 19 & 14?  Are they contributing to the boot delay?  Is there any way of removing them?  Thanks.

---

### Post by Method X on 2010-03-08
> **boxcorner said:**
> I want Ubuntu to be my primary OS.  When I re-installed my OS's recently, I tried to put Ubuntu exclusively on my 1st drive and XP on the 2nd.  I had hoped that doing so would reduce the lengthy boot time.  However, when I installed XP, it insisted on grabbing a small partition on the 1st drive.  I installed XP first and then Ubuntu, because that was the only way I knew of getting a dual boot menu.  Now when I boot, there are 3 Ubuntu pairs before the XP option. Linux 2.6.31-20, below are 19 & 14, then the memtest and finally XP. My questions are: Why have I got 19 & 14?  Are they contributing to the boot delay?  Is there any way of removing them?  Thanks.

Hi there.
Sorry, if i understanding you right... you want Windows to be first in boot menu?

---

### Post by linuxman94 on 2010-03-08
The 19 and 14 are older kernels.  Kernels are basically manage the systems resources.  Old kernels will not contribute to a boot delay.  They are good to keep in case the newer one fails to boot.  You can remove them by going terminal (Applications -> Accessories -> Termanal and typing:

```
sudo apt-get remove --purge 2.6.31-19-*
sudo apt-get remove --purge 2.6.31-14-*


```

---

### Post by boxcorner on 2010-03-08
> **Method X said:**
> Hi there.
Sorry, if i understanding you right... you want Windows to be first in boot menu?
No!  I want Ubuntu to be first in the boot menu.  My question is: Why are there 3 options for Ubuntu?  Are all 3 necessary?  How do I reduce the menu so there is only one for Ubuntu, then memtest and Windows?  Thanks.

@ linuxman94
Thanks.  Sounds like I'd best leave them.  Still don't understand how/why they've appeared, as I only recall having one in my original installation.

@ Method X
Thank you

---

### Post by Method X on 2010-03-09
> **boxcorner said:**
> No!  I want Ubuntu to be first in the boot menu.  My question is: Why are there 3 options for Ubuntu?  Are all 3 necessary?  How do I reduce the menu so there is only one for Ubuntu, then memtest and Windows?  Thanks.

@ linuxman94
Thanks.  Sounds like I'd best leave them.  Still don't understand how/why they've appeared, as I only recall having one in my original installation.

Ah, got it.

```
sudo nano /boot/grub/grub.cfg
```

(If no grub.cfg it is menu.lst)

Locate for menuentries.

here are mine entries (This is only an example):

[SIZE="2"]```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set eae4ddca-b9b1-48d4-abba-e26bc44027a4
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=eae4ddca-b9b1-48d4-abba-e26bc44027a4 ro   
        initrd  /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set eae4ddca-b9b1-48d4-abba-e26bc44027a4
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=eae4ddca-b9b1-48d4-abba-e26bc44027a4 ro single 
        initrd  /boot/initrd.img-2.6.31-20-generic
}
#menuentry "Ubuntu, Linux 2.6.28-11-generic" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
#       set quiet=1
#       insmod ext2
#       set root=(hd0,5)
#       search --no-floppy --fs-uuid --set eae4ddca-b9b1-48d4-abba-e26bc44027a4
#       linux   /boot/vmlinuz-2.6.28-11-generic root=UUID=eae4ddca-b9b1-48d4-abba-e26bc44027a4 ro   
#       initrd  /boot/initrd.img-2.6.28-11-generic
#}
#menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
#       insmod ext2
#       set root=(hd0,5)
#       search --no-floppy --fs-uuid --set eae4ddca-b9b1-48d4-abba-e26bc44027a4
```[/SIZE]

As you can see you can comment lines you don't need with "#".
But be careful. All menu entry from "menuentry" with both "{"........"}" must be commented with "#".

Also you can comment memtests etc.

But i recommend you to leave one recovery mode. Never know when you'll need it.

---

### Post by linuxman94 on 2010-03-10
@Method X
Grub.cfg is not meant to be edited.

> @ linuxman94
Thanks. Sounds like I'd best leave them. Still don't understand how/why they've appeared, as I only recall having one in my original installation.


The new kernels are installed when you update Ubuntu.

---

