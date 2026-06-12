---
title: "deleting grub loader"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by $am on 2010-03-11
Here's what's going on:

I installed kubuntu onto a flash drive (not the live cd, but the whole os) to try. However, now the grub loader has replaced my windows 7 boot program, and grub won't work unless I have the flash drive inserted. Now I want to reformat the flash drive and get rid of kubuntu. I've tried other suggestions but they haven't worked. I have windows 7 on the hard drive with no other partitions containing an os. I am running windows 7 ultimate, 32 bit, which I upgraded from windows vista ultimate, which in turn was upgraded from windows vista home or business. I have the windows 7 upgrade cd, but it's the kind that only lets you upgrade from vista. 

Also, whenever I go into the boot menu and tell it to boot from the hard disk, it tells me there's no such disc, but if I insert the flash drive, boot from it, and use grub to access windows 7 (loader) it goes fine. I can't do this without the flash drive. 

Do you have any suggestions? I'm new to this whole linux/partitioning stuff (hence the location of the thread)

Thanks.

---

### Post by Daveth on 2010-03-13
have you looked at this?

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by presence1960 on 2010-03-13
Boot into ubuntu or boot the ubuntu Live CD & choose "try ubuntu without any changes." Open a terminal and run ```
sudo apt-get install lilo
```Ignore warnings. Then in terminal run ```
sudo lilo -M /dev/sda mbr
```Your internal disk's MBR will now be a windows MBR and you will boot right to windows.

GRUB was installed to MBR of the internal disk and GRUB looks to files on your Kubuntu disk that are needed to boot. When the flash disk is not plugged in at boot it can't find those files. The solution is to put GRUB on MBR of the flash disk. If you need help with that post back

---

