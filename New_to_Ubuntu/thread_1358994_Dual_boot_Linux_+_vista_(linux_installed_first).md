---
title: "Dual boot Linux + vista (linux installed first)"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by OwNeD on 2009-12-19
so i guess you knowh what i am trying to do... i am following this guide : [http://blogs.zdnet.com/hardware/?p=609](http://blogs.zdnet.com/hardware/?p=609) however on number 8. Install Vista normally.  remember to install it onto the disk space you just freed up using GParted (it&#8217;ll show up as unallocated space, more than likely on Disk 0). how can i do this? when i startup my vista recovery disk, it dosent give me a option to install it on the unallocated space... it says i have to use GParted,but how can i use GParted while there is already a vista recovery disk innside cd drive??
 
 
and.. how can i move the unallocated space back to my dev/sda1 linux system ??
 
 
Thanks

---

### Post by OwNeD on 2009-12-19
Please help me

---

### Post by audiomick on 2009-12-19
Hallo.
Have another look at point #8. It is not telling you to use Gparted at that point, but rather to use the space created by Gparted in the previous steps.

I can imagine that the Windows installer doesn't have an option to use unallocated space, as windows tends to assume that it is the only system on the computer, and that you want to use all of the disc space on the computer for windows. **I do not know this for sure, as I have not used a windows installer for more than 6 years, and never Vista**.
Perhaps you need to make a note of the position on the disc of the empty space, and direct the windows installer to it with an option other than one called "unallocated space".

---

### Post by OwNeD on 2009-12-19
how can i move the unallocated space back to my dev/sda1 linux system ??

---

### Post by audiomick on 2009-12-19
boot up into the gparted cd again, and just make the linux partition bigger again.

Note: I don't think it is mentioned in the guide, but one should always take the precaution of backing up anything the is really critical before moving partitions around.

If you can't get the windows install working the way it is described, as a last resort you can also start from scratch by removing the Linux, Installing the windows then reinstalling the Linux. Whether that is an attractive idea or not depends on how much you need to backup out of the Linux install. If it is a new or nearly new installation, there should not be too much to back up, and that might be the easier solution. It is certainly very easy to install Linux after windows.

---

### Post by OwNeD on 2009-12-19
> **audiomick said:**
> Hallo.
Have another look at point #8. It is not telling you to use Gparted at that point, but rather to use the space created by Gparted in the previous steps.
 
I can imagine that the Windows installer doesn't have an option to use unallocated space, as windows tends to assume that it is the only system on the computer, and that you want to use all of the disc space on the computer for windows. **I do not know this for sure, as I have not used a windows installer for more than 6 years, and never Vista**.
Perhaps you need to make a note of the position on the disc of the empty space, and direct the windows installer to it with an option other than one called "unallocated space".
 
Using GParted : clicking on unallocated space ==> New ==> Create New partition > Create as extended partition, file system extended? should i do this to make vista install detect the new partition? or????

---

### Post by Zimmer on 2009-12-19
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4)

It appears from the article the Windows bootloader will ask you where to install and you point it to the unallocated space you have created..

I used variations of the articles at APC and one from the EasyBCD site to get a Vista dual boot, although mine was Vista installed first..

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

EDIT:
BTW the IMPORTANT thing to realise in using EasyBCD and Vista is that GRUB is NOT to be installed in the MBR.

GRUB must be installed (or in your case re installed) to the Linux partition..

---

### Post by OwNeD on 2009-12-19
:d

---

### Post by OwNeD on 2009-12-19
so... i put in my Vista install/recovery cd,and loaded it up. it shows "Welcome to Recovery manager" ...this will format the whole harddrive and all data will be lost.. and then it starts to format... it dosent give me any option to install it elsewhere...what should i do??

---

### Post by audiomick on 2009-12-19
Hi.
That looks like it is a recovery cd, and not an install cd, which I believe are two different things, although I am not sure.

If you let it do what it wants, it will probably overwrite your Ubuntu install and put the computer back in the state it was in when you bought it. That may be simpler if it doesn't mean too much effort backing up your existing Ubuntu install.

---

