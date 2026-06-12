---
title: "Trouble Unmounting a USB Drive"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by sharkllama on 2010-03-19
Hi Guys, 
   I've set up my fstab to mount a couple of different external usb drives that I use for backups, temporary storage and so forth.  These hard drives all mount up properly on boot, but when I go to try and unmount the drive I get an error:

(CLI)
umount: only root can unmount UUID=46cd6293-fb04-435f-87cc-5db56dc1800e from /media/LLAMA_BACKUP

Heres my fstab file:

## /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/nvidia_eddhacde1 /  ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_eddhacde5    none    swap, sw        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# External Drives
UUID=46cd6293-fb04-435f-87cc-5db56dc1800e   /media/LLAMA_BACKUP ext2   user,rw,exec,auto  0  0
UUID=13eaca78-2baf-430a-a536-f96a033c84ed   /media/LLAMA_MEDIA  ext2   user,rw,exec,auto  0  0
UUID=E116-1B19                              /media/LLAMA_POCKET vfat   user,rw,auto  0  0
UUID=3485-911A                          /media/SOOTHSAYER       vfat    user,rw,auto    0       0 


I had thought by including the user option that I would be able to unmount without a sudo, apparently I am wrong. Any ideas on why this is occuring and how I can fix this?
-Brant

---

### Post by linuxman94 on 2010-03-19
On boot the drives listed in fstab are mounted as root.

---

### Post by sharkllama on 2010-03-19
Alright, 
   How would I mount on boot otherwise?  I'd like to mount/unmount these volumes at boot, or upon plugin, so that a user can unmount them.
-Brant

---

### Post by Ozymandias_117 on 2010-03-19
> **sharkllama said:**
> 
# External Drives
UUID=46cd6293-fb04-435f-87cc-5db56dc1800e   /media/LLAMA_BACKUP ext2   user,rw,exec,auto  0  0
UUID=13eaca78-2baf-430a-a536-f96a033c84ed   /media/LLAMA_MEDIA  ext2   user,rw,exec,auto  0  0
UUID=E116-1B19                              /media/LLAMA_POCKET vfat   user,rw,auto  0  0
UUID=3485-911A                          /media/SOOTHSAYER       vfat    user,rw,auto    0       0 


I had thought by including the user option that I would be able to unmount without a sudo, apparently I am wrong. Any ideas on why this is occuring and how I can fix this?
-Brant

You are correct about user. It should be letting you unmount... Just a test... try changing it to users then add the account you want to be able to unmount into the users group. Just to see.

---

