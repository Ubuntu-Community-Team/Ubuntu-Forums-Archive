---
title: "Write permission not enabled in other partition!!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by rj7 on 2011-08-23
Hi,
    I recently found that my three other partitions are write protected....
I cannot write anything to those partitions... Someone tell me how do i change it...

---

### Post by papibe on 2011-08-23
Could you post the result of the following commands?
```
$ df -h

$ sudo mount -l

$ sudo fdisk -l
```
Regards.

---

### Post by rj7 on 2011-08-23
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              31G   11G   19G  37% /
none                  1.9G  380K  1.9G   1% /dev
none                  1.9G  1.3M  1.9G   1% /dev/shm
none                  1.9G  200K  1.9G   1% /var/run
none                  1.9G  4.0K  1.9G   1% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda7              33G   87M   33G   1% /media/IMPORTANT!!
/dev/sda5             169G  140G   30G  83% /media/Media
/dev/sda6             167G  165G  2.1G  99% /media/Study
/dev/sda3              56G   45G   11G  82% /media/_OS
/dev/sdb1             3.8G  1.2G  2.6G  32% /media/PASSCAPE


```
sudo mount -l
```

/dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda7 on /media/IMPORTANT!! type ntfs (rw,noexec,nosuid,nodev,nls=utf8,umask=0222) [IMPORTANT!!]
/dev/sda5 on /media/Media type ntfs (rw,noexec,nosuid,nodev,nls=utf8,umask=0222) [Media]
/dev/sda6 on /media/Study type ntfs (rw,noexec,nosuid,nodev,nls=utf8,umask=0222) [Study]
/dev/sda3 on /media/_OS type ntfs (rw,noexec,nosuid,nodev,nls=utf8,umask=0222) [ OS]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raja/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raja)
/dev/sdb1 on /media/PASSCAPE type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush) [PASSCAPE]

```

sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18        1307    10360832    7  HPFS/NTFS
/dev/sda3            1307        8534    58051307    7  HPFS/NTFS
/dev/sda4            8535       60801   419833377+   f  W95 Ext'd (LBA)
/dev/sda5            8535       30575   177043031+   7  HPFS/NTFS
/dev/sda6           34655       56340   174181376    7  HPFS/NTFS
/dev/sda7           56340       60559    33886208    7  HPFS/NTFS
/dev/sda8           60560       60801     1943833+  82  Linux swap / Solaris
/dev/sda9           30576       34654    32762880   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006975

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         489     3921856    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(487, 254, 63) logical=(488, 65, 25)


```

---

### Post by Morbius1 on 2011-08-23
> /dev/sda7 on /media/IMPORTANT!! type ntfs (rw,noexec,nosuid,nodev,nls=utf8,**[COLOR=Blue]umask=0222[/COLOR]**) [IMPORTANT!!]
/dev/sda5 on /media/Media type ntfs (rw,noexec,nosuid,nodev,nls=utf8,[COLOR=Blue]**umask=0222**[/COLOR]) [Media]
/dev/sda6 on /media/Study type ntfs (rw,noexec,nosuid,nodev,nls=utf8,**[COLOR=Blue]umask=0222[/COLOR]**) [Study]
/dev/sda3 on /media/_OS type ntfs (rw,noexec,nosuid,nodev,nls=utf8,[COLOR=Blue]**umask=0222**[/COLOR]) [ OS]If the above partitions are the problem then they are write protected because you made them so.

Go back into fstab and change that to a umask=0000

---

### Post by rj7 on 2011-08-23
I tried what you said... But still I cannot write anything on those disks....
my fstab file is 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc               proc  nodev,noexec,nosuid                0  0  
#Entry for /dev/sda9 :
/dev/disk/by-uuid/1780f923-3682-4867-841a-dcc0975afb6a  /                   ext4  errors=remount-ro                  0  1  
#Entry for /dev/sda7 :
/dev/disk/by-uuid/588ACD678ACD41EC                      /media/IMPORTANT!!  ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda5 :
/dev/disk/by-uuid/1CA2CE40A2CE1E60                      /media/Media        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda2 :
/dev/disk/by-uuid/863C1AC43C1AAEE5                      /media/RECOVERY     ntfs  nls=utf8,ro,noauto,umask=0222      0  0  
#Entry for /dev/sda6 :
/dev/disk/by-uuid/50C2A213C2A1FCFA                      /media/Study        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda3 :
/dev/disk/by-uuid/40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda1 :
/dev/disk/by-uuid/07DA-071B                             /media/sda1         vfat  noauto                             0  0  
/dev/disk/by-uuid/28d37f3b-98f9-42dc-ae1e-b2a2dfb42246  none                swap  sw                                 0  0  
#Entry for /dev/sda8 :
/dev/disk/by-uuid/ec1b57bd-79fd-47d3-a98b-e4ddf9fdfa31  /media/sda8         swap  defaults                           0  0  




```

---

### Post by rj7 on 2011-08-23
I also have another problem..
I cannot unmount these partitions..
It says only root can unmount it!!
What i actually did was i tried to auto mount the partitions... So i installed configured them using ntfs-config and pysdm.. But then i stated having lot of problems....

---

### Post by fdrake on 2011-08-24
to unmount them do:
```

sudo umount /dev/sda7 
sudo umount /dev/sda5 
sudo umount /dev/sda6 
sudo umount /dev/sda3

```

---

### Post by rj7 on 2011-08-24
That works but why do i need root permission to do that...
Is there any way i can change it....
and any idea about "WRITE PERMISSION" problem???

---

### Post by fdrake on 2011-08-24
> **rj7 said:**
> That works but why do i need root permission to do that...
Is there any way i can change it....
and any idea about "WRITE PERMISSION" problem???

who(wich users beside root) do you want to be able to write/delete the files in the filesystems. You can make all users able to see or execute the file if you want. Do you have some kind of filtering/restrictions in mind? or jus free access to everyone?

ps . the umask commmand that Morbius1 gave you will take effect after a rebbot. did you reboot yet?

---

### Post by rj7 on 2011-08-24
Ya even after reboot i couldnt write any thing in it.... Thats why i posted my fstab file...
I am the only possible user in this system so there is no restriction in accessing those partitions....
Every thing was working fine before i fixed this problem
[http://ubuntuforums.org/showthread.php?t=1830391](http://ubuntuforums.org/showthread.php?t=1830391)

---

### Post by fdrake on 2011-08-24
i just noted that you putted the ids of the partitions i  a wrong way:
copy the fstab below (your previuos one)
sudo cp /etc/fstab /etc/fstab.bk
sudo gedit /etc/fstab
(select all, delete , paste, save)
apply the command that Morbious1 gave you about the umask

reboot
basically just replace your new fstab with the old one.
the fact that your nfts filesystem show up twice is due to the way you have configured you menu-tab on the left. You have probably select to show mount points and devices too

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc               proc  nodev,noexec,nosuid                0  0  
#Entry for /dev/sda9 :
UUID=1780f923-3682-4867-841a-dcc0975afb6a  /                   ext4  errors=remount-ro                  0  1  
#Entry for /dev/sda7 :
UUID=588ACD678ACD41EC                      /media/IMPORTANT!!  ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda5 :
UUID=1CA2CE40A2CE1E60                      /media/Media        ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda2 :
UUID=863C1AC43C1AAEE5                      /media/RECOVERY     ntfs  nls=utf8,ro,noauto,umask=0222      0  0  
#Entry for /dev/sda6 :
UUID=50C2A213C2A1FCFA                      /media/Study        ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda3 :
UUID=40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0222,user  0  0  
#Entry for /dev/sda1 :
UUID=07DA-071B                             /media/sda1         vfat  noauto                             0  0  
UUID=28d37f3b-98f9-42dc-ae1e-b2a2dfb42246  none                swap  sw                                 0  0  
#Entry for /dev/sda8 :
UUID=ec1b57bd-79fd-47d3-a98b-e4ddf9fdfa31  /media/sda8         swap  defaults                           0  0

```

---

### Post by rj7 on 2011-08-24
I did what you said and still i could not write anything onto those disks and now the partitions are displayed twice!!!! 
i have pysdm installed now... Is that a problem!!

---

### Post by rj7 on 2011-08-24
All i want is to have all the default values.... As i said i must have done something stupid with pysdm and ntfs-config(Trying to auto mount)....

---

### Post by fdrake on 2011-08-24
they are displayed twice because beside nautilus manager you have also  PySDM . before probably one of the 2 managers could not read the properly the way the devices were mounted (that's why it showed only once)


---------------------------Notes--------------------------------------
 PySDM is a PyGTK Storage Device Manager that allows full customization of hard disk mountpoints whitout manually access to
 fstab. It also allows the creation of udev rules for dynamic configuration of storage devices
-----------------------------------------------------------------------
NTFS-config: Enable/disable write support for any NTFS devices
 This program allow you to easily configure all of your NTFS devices to allow write support via a friendly gui. For that
 use, it will configure them to use the open source ntfs-3g driver. You'll also be able to easily disable this feature.
-----------------------------------------------------------------------

(in my opinion you did not need those in the first place) lets try to get the ownership first done.

```
sudo chown -R /media
sudo chmod -R 755 /media
```

---

### Post by rj7 on 2011-08-24
Really thanks fdrake.. Those explanations helped me a lot
Actually i had disabled permission to write on those disks(unknowingly) in ntfs-config
All i did was started ntfs-config and tick the check boxes to enable the permission...
I got both my problem fixed... my present fstab file like this for all the entry
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc               proc  nodev,noexec,nosuid                0  0  
#Entry for /dev/sda9 :
/dev/disk/by-uuid/1780f923-3682-4867-841a-dcc0975afb6a  /                   ext4  errors=remount-ro                  0  1  
#Entry for /dev/sda7 :
/dev/disk/by-uuid/588ACD678ACD41EC                      /media/IMPORTANT!!  ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda5 :
/dev/disk/by-uuid/1CA2CE40A2CE1E60                      /media/Media        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda2 :
/dev/disk/by-uuid/863C1AC43C1AAEE5                      /media/RECOVERY     ntfs  nls=utf8,ro,noauto,umask=0222      0  0  
#Entry for /dev/sda6 :
/dev/disk/by-uuid/50C2A213C2A1FCFA                      /media/Study        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda3 :
/dev/disk/by-uuid/40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda1 :
/dev/disk/by-uuid/07DA-071B                             /media/sda1         vfat  noauto                             0  0  
/dev/disk/by-uuid/28d37f3b-98f9-42dc-ae1e-b2a2dfb42246  none                swap  sw                                 0  0  
#Entry for /dev/sda8 :
/dev/disk/by-uuid/ec1b57bd-79fd-47d3-a98b-e4ddf9fdfa31  /media/sda8         swap  defaults                           0  0  



```because if i change it like you said, it displays the partitions two times...
And just one more thing how to unmount without using sudo ie...) In nautilus itself without using command line...
Will that be present in ntfs-config too??

---

### Post by fdrake on 2011-08-24
> **rj7 said:**
> Really thanks fdrake.. Those explanations helped me a lot
Actually i had disabled permission to write on those disks(unknowingly) in ntfs-config
All i did was started ntfs-config and tick the check boxes to enable the permission...
I got both my problem fixed... my present fstab file like this for all the entry
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc               proc  nodev,noexec,nosuid                0  0  
#Entry for /dev/sda9 :
/dev/disk/by-uuid/1780f923-3682-4867-841a-dcc0975afb6a  /                   ext4  errors=remount-ro                  0  1  
#Entry for /dev/sda7 :
/dev/disk/by-uuid/588ACD678ACD41EC                      /media/IMPORTANT!!  ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda5 :
/dev/disk/by-uuid/1CA2CE40A2CE1E60                      /media/Media        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda2 :
/dev/disk/by-uuid/863C1AC43C1AAEE5                      /media/RECOVERY     ntfs  nls=utf8,ro,noauto,umask=0222      0  0  
#Entry for /dev/sda6 :
/dev/disk/by-uuid/50C2A213C2A1FCFA                      /media/Study        ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda3 :
/dev/disk/by-uuid/40C61EF4C61EE9C4                      /media/_OS          ntfs  defaults,nls=utf8,umask=0000,user  0  0  
#Entry for /dev/sda1 :
/dev/disk/by-uuid/07DA-071B                             /media/sda1         vfat  noauto                             0  0  
/dev/disk/by-uuid/28d37f3b-98f9-42dc-ae1e-b2a2dfb42246  none                swap  sw                                 0  0  
#Entry for /dev/sda8 :
/dev/disk/by-uuid/ec1b57bd-79fd-47d3-a98b-e4ddf9fdfa31  /media/sda8         swap  defaults                           0  0  



```because make it look like the old one displays the partitions two times...
And just one more thing how to unmount without using sudo ie...) In GUI itself not in command line...

i know that you can eject media and removable disk in nautilus but i do not know about hdd partitions.  You can costumize your nautilus entries but it may take a while before you figure it out and with the richt entries for your drive.
but you can use disk-utility,
menu-bar > administration > disk utility .
it gives you the option to "unmount disk" with no password

---

### Post by rj7 on 2011-08-24
Ya i can do that too...
I am more concerned about learning how these things work rather than being like  "My system should always work fine"
So if there s  any link from where i can learn these just post me!!!
And thanks for helping me out!!!

---

### Post by fdrake on 2011-08-24
look for the package "nautilus-actions" (google it) .

you can try to create a new entry for your right click menu, when you select a folder (partition-drive) in nautilus. In this entry use the "udisks" command (no mount / umount because it does not require password). Create the command entry with the variable present in nautilus. It may take a while but if you can do it you will be able to make any kind of entry that you like in nautilus,

good luck! 

ps  you r welcome

---

### Post by rj7 on 2011-08-24
Thanks fdrake..

---

