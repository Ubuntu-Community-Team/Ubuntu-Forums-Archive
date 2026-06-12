---
title: "gparted. how to set flags"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by senorian on 2011-08-13
I have repartitioned my hard drive but cannot set the boot flag
thanks

---

### Post by oldfred on 2011-08-13
Grub does not use a boot flag. Windows has to have a boot flag if it is using its boot loader. A few motherboards (Intel for one) require a boot flag on a primary partition as if you only boot windows and the BIOS gives an error.

In gparted you click on a partition and right click set flags. You can also use Disk Utility or command line.

set boot flag on for sda[COLOR=Red]2[/COLOR] (off for others)
sudo sfdisk -A[COLOR=Red]2 [/COLOR]/dev/sda

---

### Post by senorian on 2011-08-13
oldfred
Thanks
I was unable to get ubuntu 10.04.3 to load to my hard drive; but Kubuntu 10.04.3 did.
Both are 64 bit iso
Now I have to find a way to get flash working. The instructions that Falko "the perfect desktop kubuntu 10.04  gives 
don't work.It seems that the 10.04.3 version has some changes.
So a new topic!
Thanks for the info about grub.

---

