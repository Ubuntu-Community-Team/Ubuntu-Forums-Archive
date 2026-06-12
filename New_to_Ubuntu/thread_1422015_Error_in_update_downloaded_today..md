---
title: "Error in update downloaded today."
date: 2010-03-04
forum: New to Ubuntu
---

### Post by superbeefus on 2010-03-04
I'm pretty new to Ubuntu, but I've managed to troubleshoot my way (with help from these forums!) through everything to get my system just the way I want it. However, today, there were alot of critical updates and reccomended updates in the update manager. So I installed them. System rebooted. Now, when it tries to load grub, I get a list of error messages that get cleared off the screen really quick, then I get a message "cannot load kernel", then the following prompt:
 
sh$grub>
(or something like that, filling this out at work, Ubuntu's installed on my desktop at home...)
Not sure where to go from here. I don't really know how to use any of the commands, or even what the problem might be. I've checked a few other forum posts, that SEEM to be a similar problem, but I'm not entirely sure if it's the same issue. Can anyone help?

---

### Post by superbeefus on 2010-03-04
If it helps, I'm using Ubuntu 9.10, and since installing last week, I have installed all the available updates, and am using a command-line installed video card driver (can't remember which version, the latest, not available in the update manager)  Running an AMD X2 5000+ black, Asus M2NSLI motherboard, 4gb of PC 6400 DDR2 OCZ Gold, I think, and an Nvidia 9800gt video card.  Seagate 160gb SATA2 HDD.

---

### Post by nmccrina on 2010-03-04
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

That has a lot of info on Grub. 

Does holding down the shift key while booting get you a menu?

---

### Post by kansasnoob on 2010-03-04
I wonder if this was a Wubi install?

Now many OS's do you have?

Did you install like this:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Or this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It could be really helpful to se the output of The Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by superbeefus on 2010-03-05
I haven't tried holding the shift key yet. I will try that. And i installed it as the sole partition on the drive. I do have Win 7 RC 7100 installed on another drive, but I don't use it anymore, as the "trial" expired on monday. I'll try that post and see what I come up with.
 
Edit for clarification: I didn't install in windows w/wubi, I booted from the CD and did a complete install to one drive.

---

### Post by myolbug on 2010-03-05
Don't feel bad.  AGAIN!, I have installed the latest greatest updates including the new kernal and it has wiped out my evolution address book.  This is the SECOND time this has happened to me.

I am FURIOUS!!  I thought Windows was bad.  ](*,)

---

### Post by kansasnoob on 2010-03-05
> **myolbug said:**
> Don't feel bad.  AGAIN!, I have installed the latest greatest updates including the new kernal and it has wiped out my evolution address book.  This is the SECOND time this has happened to me.

I am FURIOUS!!  I thought Windows was bad.  ](*,)

Well that makes no sense to me. Your settings should be safe through any update, furthermore it's not related to this topic!

---

### Post by kansasnoob on 2010-03-05
> **superbeefus said:**
> I haven't tried holding the shift key yet. I will try that. And i installed it as the sole partition on the drive. I do have Win 7 RC 7100 installed on another drive, but I don't use it anymore, as the "trial" expired on monday. I'll try that post and see what I come up with.
 
Edit for clarification: I didn't install in windows w/wubi, I booted from the CD and did a complete install to one drive.

If you would post the results of that Boot Info Script we could see what you're dealing with:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by superbeefus on 2010-03-05
Shift key did nothing, just the same "syntax error" and "error: unknown command 'include'"

Boot info results inc:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95e995e9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        96,389        96,327  de Dell Utility
/dev/sdb2              98,304   312,496,127   312,397,824   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a9e0c2fd-0124-46ba-8b9d-e824a76fb8e0   ext4                                     
/dev/sda1        CCC4DE1FC4DE0C18                       ntfs       System Reserved               
/dev/sda2        7664E39864E358FF                       ntfs                                     
/dev/sdb1        07D9-0A17                              vfat       DellUtility                   
/dev/sdb2        34ECCAB2ECCA6DA4                       ntfs       New Volume                    
/dev/sdb         Dell                                  ddf_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


======================== sdb2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 34eccab2ecca6da4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ccc4de1fc4de0c18
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb2/Wubi: Location of files loaded by Grub: =================


   5.4GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
   3.8GB: boot/initrd.img-2.6.31-19-generic
   5.3GB: boot/initrd.img-2.6.31-20-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   1.2GB: boot/vmlinuz-2.6.31-19-generic
   5.2GB: boot/vmlinuz-2.6.31-20-generic
   5.3GB: initrd.img
   3.8GB: initrd.img.old
   5.2GB: vmlinuz
   1.2GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ERROR: ddf1: both header signatures bad on /dev/sdb
ERROR: ddf1: both header signatures bad on /dev/sdb

```

---

### Post by mcduck on 2010-03-05
Based on that output, you *did* install with Wubi. I suggest making a fresh install, this time really doing it as standalone install instead of installing inside a Windows filesystem...

---

### Post by kansasnoob on 2010-03-05
Well it looks like you had a Wubi install and converted it to a hard install :

> **sd[COLOR="Red"]a[/COLOR]2**: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe **/wubildr.mbr /wubildr**

> **sd[COLOR="Red"]b[/COLOR]2**: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   **/ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr **
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk


I've honestly never seen that but with Ubuntu being the only OS now this can't work:

> => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb


So I'd boot a Live CD and do this (note: the "recheck" commands will take several minutes to run):

```
sudo mount /dev/sdb2 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

```

```
grub-install /dev/sda
```

```
grub-install --recheck /dev/sda
```

```
grub-install /dev/sdb
```

```
grub-install --recheck /dev/sdb
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then see what happens. I have doubts :-?

---

### Post by superbeefus on 2010-03-05
That's really wierd, because I didn't even have the windows 7 drive* plugged in* when I installed!  I'll have a go at it then. sigh.

---

### Post by myolbug on 2010-03-05
> **kansasnoob said:**
> Well that makes no sense to me. Your settings should be safe through any update, furthermore it's not related to this topic!

Yes it is totally related to this topic.  He had errors with an upgrade, well this is the error that I got.  And yes, this is the second time I have had this happen with and upgrade, I thought someone could point me in the right direction.

---

### Post by superbeefus on 2010-03-05
The first command line gave me this:

mount: mount point /mnt/dev does not exist.

I tried it again, and it said:

fuse: mount failed Device or resource busy

2nd command line gave me:

grub-mkdevicemap: error: cannot open /boot/grub/device.map

---

### Post by HermanAB on 2010-03-05
Well, you got to ask yourself: If the system is working properly, why update?

I never update, beyond the initial installation.  Then in 6 months to 3 years when I feel like it, I install the latest version of Linux.  Updates cause more trouble than they are worth, because they are not tested as well as a complete new release and the developers do not know what changes you have made to your system since you installed it.

On Windoze, the system quality is so bad that almost every update is an improvement, but on Linux that is not true.

---

### Post by mcduck on 2010-03-05
> **HermanAB said:**
> Well, you got to ask yourself: If the system is working properly, why update?

I never update, beyond the initial installation.  Then in 6 months to 3 years when I feel like it, I install the latest version of Linux.  Updates cause more trouble than they are worth, because they are not tested as well as a complete new release and the developers do not know what changes you have made to your system since you installed it.

On Windoze, the system quality is so bad that almost every update is an improvement, but on Linux that is not true.

good luck with that, considering that the only updates Ubuntu provides are security updates and fixes to more serious bugs... Somehow both feel like quite sensible things to install... ;) So you don not get any updates that would introduce new features or change the existing ones in any way that would be likely to break things (unless of course you've enabled some third-party repositories and made your own configurations in wrong places/ways)

(by the way, the only ways how I've ever seen an update break things on stable Ubuntu release have been a) graphics card drivers installed from outside of Ubuntu's repositories (in which case you need to reinstall them after kernel update), and b) the user has massed some configuration files, or mixed repositories from different releases. Of course this is all related to the "developers don't know what you've made to your system"-sittuation you mentioned, but in my experience if you do your changes in correct ways then updates shouldn't be any problem

---

### Post by myolbug on 2010-03-05
> **HermanAB said:**
> Well, you got to ask yourself: If the system is working properly, why update?

I never update, beyond the initial installation.  Then in 6 months to 3 years when I feel like it, I install the latest version of Linux.  Updates cause more trouble than they are worth, because they are not tested as well as a complete new release and the developers do not know what changes you have made to your system since you installed it.

On Windoze, the system quality is so bad that almost every update is an improvement, but on Linux that is not true.

Thanks HermanAB, I will keep that in mind next time.  I appreciate the response.

---

### Post by Paddy Landau on 2010-03-05
> **HermanAB said:**
> On Windoze, the system quality is so bad that almost every update is an improvement, but on Linux that is not true.
That made me laugh. But, I'm not so sure that Linux updates are not improvements. I'm one of the lucky ones, though; on all five computers in my family, Ubuntu and Xubuntu updates have never caused a problem. I wonder if the hardware is a factor in this?

---

### Post by Ricket on 2010-03-05
I know exactly your problem; I experienced it when I upgraded to 2.6.31-19. I noticed I'm getting a bit of traffic today to a blog post I wrote a while back, and it has the solution.

So either read [_my blog post_]("http://blog.rickyc.org/2010/02/26/wubi-kernel-upgrade-goes-to-shgrub-prompt/"), or here's [_the direct link to the fix_]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10&oldid=214") (under the heading Solution).

---

### Post by kansasnoob on 2010-03-05
> **superbeefus said:**
> The first command line gave me this:

mount: mount point /mnt/dev does not exist.

I tried it again, and it said:

fuse: mount failed Device or resource busy

2nd command line gave me:

grub-mkdevicemap: error: cannot open /boot/grub/device.map

That failed because I totally had my head up my nether region :oops:

**[COLOR="Red"]sdb2/Wubi[/COLOR]**

So having Windows installed to the mbr of both drives was right all along. Run the script again and look at those first two lines. Hopefully it still says:

>  => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb


If not we can easily fix it just using an Ubuntu live CD. Sorry I goofed, I must have been more tired than I realized. In my defense you'd said this:

> **And i installed it as the sole partition on the drive.**

Which is incorrect. Ubuntu is installed with Wubi inside of the NTFS partition on sdb2, I should have caught that though.

Regarding these Wubi issues with Karmic. There is a known bug and it's all explained in the following link (along with the fix):

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Sorry again for my goof up. If you run that script again and find that the mbr of either drive is changed you can fix it like this using the Live CD:

```
sudo apt-get install lilo
```

Then depending on which drive (sda or sdb) needs a Windows readable mbr either:

```
sudo lilo -M /dev/sda mbr
```

Or:

```
sudo lilo -M /dev/sdb mbr
```

Or even both, it won't hurt anything.

Although to be honest I can't see the purpose of having a Wubi install if Ubuntu is the only working OS. I mean the Wubi install is not even in an NTFS partition with a Win OS:

```
sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

```

It just kind of baffles me :confused:

---

