---
title: "fstab help before I lose the ability to mount drives"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by KPJ on 2010-12-14
Please excuse my "newbie" issue - but I would like to adk for assistance before I make things worse.

I am attempting to change the permissions of my Maxtor OneTouch4 Plus so that I can rip DVD files from my laptop to the external HD. The HD is a NTFS format and I now realize that I must make changes in the fstab file in order to change the permissions once the external HD mounts to Ubuntu. 

I thought I had made a back-up of the fstab file but I can not find it (or I thought I had).

I can still mount the CD/DVD Rom drive and the Maxtor HD. Ubuntu still boots fine. I can edit the fstab file as well. I can not play movies from the CD/DVD drive and I still need to change permissions on the Maxtor so Acid/DVD ripper can copy straight to the ext HD. 

blkid looks like:
[B]/dev/loop0: UUID="a027b7c8-b627-4c20-a0ee-56d924fb3b8c" TYPE="ext4" 
/dev/sda1: UUID="1E985EEA10A5FCB9" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="1E5AE66A5AE63E61" TYPE="ntfs" 
/dev/sdc1: LABEL="OneTouch4 Plus" UUID="55D123D9E79ABF54" TYPE="ntfs" 

fstab file is:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0  $
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


Any suggestions on how best to add the mountpoints  back for the DVD and the ext HD? 

The system is a WUBI install and teh extra "HP" drive is a backup partition.

Thanks,

Ken

[/B]

---

### Post by Soldier2580 on 2010-12-14
How did you back up the fstab?

I'm kinda noobish myself, but I know when I was messing around with the fstab, I created a backup like so:
```
sudo cp /etc/fstab /etc/fstab.backup
```
and then, whenever I messed up, all my fails and errors were gone by simply doing
```
sudo cp /etc/fstab.backup /etc/fstab
```
as I said, I'm not a pro, but I hope it helps, if not now, maybe the next time :)

---

### Post by KPJ on 2010-12-14
Thanks soldier

I thought I had completed that command but apparently not!  

I am learning the terminal commands so that I can verify next time.

---

