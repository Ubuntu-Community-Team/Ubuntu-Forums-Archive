---
title: "GRUB- error: no such partition grub rescue&gt;"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by alexpwnsn00b2 on 2010-04-08
[B]hi after installing Ubuntu 9.10 side by side vista i get 

[/B][B]GRUB- error: no such partition   grub rescue>  

when trying to boot up again :(

i dont know what to do and i have google for like 2 hous now with little to no luck. please help


[/B]

---

### Post by alexpwnsn00b2 on 2010-04-08
and i made a partition for ubuntu in vista before i tryed to dual boot

---

### Post by oldfred on 2010-04-08
Did you create a separate windows partition and install it there as a wubi install?
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If not this may help:
Solutions to many boot issues - meierfra.:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

Part of above page:
Boot Problems:search or no such device
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by alexpwnsn00b2 on 2010-04-08
> **oldfred said:**
> Did you create a separate windows partition and install it there as a wubi install?
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If not this may help:
Solutions to many boot issues - meierfra.:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

Part of above page:
Boot Problems:search or no such device
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)


i installed Ubuntu from a USB flash drive on my netbook i did not us wubi because i wanted Ubuntu to have its own partition. now that i think about it i should have installed Ubuntu netbook remix. 

i read evey suggestion and could not find anything that helped. is there any other way to possibly delete grub and make vista start up again so i can format the partition that ubuntu is on and try again? (i'm a noob to linux)

---

### Post by alexpwnsn00b2 on 2010-04-08
i can boot ubuntu from the usb drive so if i need to do something in terminal let me know.

are there any commands in grub rescue> that can help me boot into vista?

---

### Post by alexpwnsn00b2 on 2010-04-08
is there a way to uninstall GRUB? mmm what boot loader booted up vista? is there a way to get it back?:(

---

### Post by Didius Falco on 2010-04-08
This will tell you how to put the Vista bootloader back into the MBR using your Vista CD:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Regards,

Didius

---

### Post by oldfred on 2010-04-09
If you do not have a Windows CD you can install a generic windows boot loader from ubuntu where sdX is the drive you want to install to sda, sdb etc:

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

May require universe to be enabled, I have them all check and I was able to download it.

---

### Post by alexpwnsn00b2 on 2010-04-09
> **oldfred said:**
> If you do not have a Windows CD you can install a generic windows boot loader from ubuntu where sdX is the drive you want to install to sda, sdb etc:

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

May require universe to be enabled, I have them all check and I was able to download it.

now how do i find out which sdX to install the generic windows boot loader? is there a command to see all the sdX drives?

---

### Post by alexpwnsn00b2 on 2010-04-09
oh and how do i turn on universe. will this also work while booting from a USB drive?

---

### Post by alexpwnsn00b2 on 2010-04-09
> **oldfred said:**
> If you do not have a Windows CD you can install a generic windows boot loader from ubuntu where sdX is the drive you want to install to sda, sdb etc:

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

May require universe to be enabled, I have them all check and I was able to download it.
 

THANK YOU!!!!! after i did this in terminal and restarted my computer it booted up to vista successfully :KS:KS:KS

now if i delete the ubuntu partition will i be able to to continue to access vista?

---

### Post by oldfred on 2010-04-09
You should be able to delete the partition if you desire. You obviously figured this out but:

For the record. To list drives & partitions, but you still have to know which is the one you want if you have multiple drives. 

sudo fdisk -l 

And system, administration, software sources is where you select what sources to download software from.

---

