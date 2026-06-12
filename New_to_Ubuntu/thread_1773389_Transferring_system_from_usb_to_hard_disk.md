---
title: "Transferring system from usb to hard disk"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by rng on 2011-06-02
I managed to install ubuntu 10.10 to usb pendrive by running live install cd and choosing usb drive for installation. It boots and runs fine on my 2 computers. I have installed more softwares into it through synaptic. Can I now transfer the whole system to a hard drive partition? Please help.

---

### Post by tea for one on 2011-06-02
Yes, you can use a live USB installation to subsequently install onto other hard drives.

However, I am not sure that it will transfer all the additional software unless you have already created a remastered image.

If you add Remastersys and then create another ISO, the newly remastered image will also contain the Ubuntu installer and it will also install all the software (inc codecs) that you have added.

[http://geekconnection.org/remastersys/ubuntu.html](http://geekconnection.org/remastersys/ubuntu.html)

There are other applications like Clonezilla which will perform similar functions but I am less familiar with them.

---

### Post by rng on 2011-06-02
Thanks for the info. Can I use dd command for this?

---

### Post by tea for one on 2011-06-02
> **rng said:**
> Thanks for the info. Can I use dd command for this?

Yes, I'm sure you can but the transfer may be slow because your file size will probably be over 700MB.

Also, you will have to consider what will happen with Grub i.e if you are booting a "live" system from USB without a user name, it may be better to install via the Ubuntu installer to your hard drive and create a user in the normal way.

So many choices...........

---

### Post by rng on 2011-06-02
How about this command:  dd if=/dev/sdb1 of=/dev/sda5  (if sdb is usb pendrive partition and sda5 is hard disk partition) ;  then I point the grub installed on hard disk mbr to sda5 files. Will it work?

Will simple cp command work to copy all files from /sdb1 to /sdb5 ?  Will this hard disk install automatically use the linux swap partition available on hard disk?

---

### Post by oldfred on 2011-06-02
You can use dd, we have seen users do that. dd is intended to copy from identical size drives to another drive of the same size. dd also has the nickname Data Destroyer, so you have to be very careful. You end of having to make changes to one or the other system as you have identical UUIDs on two drives which will not work.

You can use cp or rsync to copy data. But then you have to reinstall grub & edit fstab to have correct UUIDs.

I think it is best just to reinstall a nice clean install. Then copy /home over so you have all the user settings. If you have installed a lot of applications you can extract those and reinstall easily. Only if you do not have high speed Internet are any of the copy methods possibly better.

My backup procedure is not an image, but assuming I will reinstall. So all my data in a backup is my data & settings, but not system files.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by rng on 2011-06-02
Thanks oldfred. This computer of mine does not have internet connection. That is the main problem. Please give me exact rsync (or cp) command to copy all files from usb pendrive (sdb1) to hard disk partition (sda5). 

I understand that I need to edit /boot/grub/grub.cfg to correct the uuid. I also need to correct uuid in /etc/fstab. Any other place I need to correct uuid?

Again, many thanks for your help.

---

### Post by oldfred on 2011-06-02
I have not copied full system, but it should be identical to moving /home ( I did move /boot that way once). You have to preserve permissions and ownership, root for system files and you as user for /home.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo, then root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I think it is just grub & fstab that have to be updated. You can chroot into your new copy and run a grub install and grub-update to automatically reset everything, but the only way I know to update fstab is manually.

In my backup I list several of the rsync parameters that I use:

-l: copies symlinks as symlinks
-t: preserves modification times
-D: preserves device and special files

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress

---

### Post by rng on 2011-06-03
I have copied whole system using rsync -av command (after booting with a linux live cd). I am now getting grub2 screen with menu items of copied usb. The /boot/grub.cfg menuitem entry is as follows: 

menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 91dc13e3-ea0a-4a6d-a9c4-4ca17412c50b
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=91dc13e3-ea0a-4a6d-a9c4-4ca17412c50b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}

I think I need to edit at following points: 

set root =(hd1,1)    
linux /boot/vmlinux.....   root=uuid......

The hard disk partition is sda5. 
How should I change the above commands?
Can I replace uuid with (hd0,4) (old grub format)?  What would be grub2 equivalent?
What about "search --no-floppy...... " line?

I appreciate your help.

---

### Post by oldfred on 2011-06-03
Set root has to be to new partition, now drive 0? Partitions with grub2 are numbered the same as Ubuntu's devices so sda5 is (hd0,5). You only have to edit one boot stanza to be able to boot then an update-grub will fix all the others. Or you can chroot into your system and run the updates.

Use this to know the new UUIDs

sudo blkid

Reinstall grub2's boot loader to the MBR to know to boot new partition.

You also have to update the UUID's in fstab.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by JohnBonne on 2011-06-03
> **oldfred said:**
> You can use dd, we have seen users do that. dd is intended to copy from identical size drives to another drive of the same size. dd also has the nickname Data Destroyer, so you have to be very careful. You end of having to make changes to one or the other system as you have identical UUIDs on two drives which will not work.

You can use cp or rsync to copy data. But then you have to reinstall grub & edit fstab to have correct UUIDs.

I think it is best just to reinstall a nice clean install. Then copy /home over so you have all the user settings. If you have installed a lot of applications you can extract those and reinstall easily. Only if you do not have high speed Internet are any of the copy methods possibly better.

My backup procedure is not an image, but assuming I will reinstall. So all my data in a backup is my data & settings, but not system files.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Thanks oldfred. I'll have a look.

---

### Post by rng on 2011-06-03
Thanks oldfred for taking time to answer my queries. I changed the UUIDs and it worked. My problem is solved at last. Thanks very much once again.

---

### Post by oldfred on 2011-06-03
Glad it worked.:D

---

### Post by rng on 2011-06-03
I have been using this hard disk install for last one day and it seems to be working all right, except that sound is not coming. If I boot with usb on same computer sound is all right. Please help.

---

### Post by oldfred on 2011-06-03
I do not know about sound. Even more strange that it works with USB. I would suggest a new thread as those that may know about sound issues will not look at  a thread titled transferring system.

The only issue I had before was the volume was muted. It actually works better than windows for me on my system. I installed a windows driver once and took weeks to find out it had to be physically unplugged & replugged in to the auto sense to know speakers were plugged in.

---

### Post by rng on 2011-06-04
Could you just guide me how to check if it is muted. I checked through the top panel > preferences > sound: it is not muted there (I made the volume max). Alsamixer command does not work on my system (usb or hd). Is there any other way to check if it is muted?

---

### Post by rng on 2011-06-04
The sound is here again. I had added some program which had interfered with sound system. Thanks.

---

