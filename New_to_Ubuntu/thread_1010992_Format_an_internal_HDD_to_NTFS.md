---
title: "Format an internal HDD to NTFS"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-14
Hi,

I have a 2nd internal 1TB hard drive that i would like to format to NTFS so i can can share it with both windows XP and ubuntu which I dual boot with on the other hard drive.

The 2nd hard drive has about 700GB of media saved on it and it is un partitioned. Can i format this hard drive to NTFS without having to move all the media off it and obviously without losing any of the media.

Any ideas much appreciated.

Thanks

Fletch:popcorn:

---

### Post by taurus on 2008-12-14
Formatting a drive will wipe out the data on the drive so if you want to reformat it, you need to do a backup or move those files somewhere else first.

---

### Post by tomtom1982 on 2008-12-14
> **fletcham said:**
> The 2nd hard drive has about 700GB of media saved on it and it is un partitioned. Can i format this hard drive to NTFS without having to move all the media off it and obviously without losing any of the media.


Which file system your 2nd hdd has?

It's possible to convert from fat32 to ntfs, for example (without loosing content).

---

### Post by fletcham on 2008-12-14
Not sure what file system it is. I just mounted it and dragged loads of files into it. I guess its ext3. If so would I have to move evrything somewhere else and then format it?

Cheers for your help!!

---

### Post by taurus on 2008-12-14
You can see what filesystem it is from looking at the output of this command.  Chances are it's fat32/vfat because you have to format it to ext3 since those new harddrives don't come with ext3 as a default filesystem.

```
sudo fdisk -l
```

---

### Post by w4ett on 2008-12-14
I use Ext2fs to mount my ext3 drives in windows it works well (so far) might be worth considering.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by fletcham on 2008-12-14
This is my output from fdisk -l:



fletch@fletch-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee876

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3589    28828611    7  HPFS/NTFS
/dev/sda2            3590       59382   448157272+  83  Linux
/dev/sda3           59383       60801    11398086    f  W95 Ext'd (LBA)
/dev/sda5           59383       60091     5694979+  82  Linux swap / Solaris
/dev/sda6           60092       60092        8001   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a750a74

   Device Boot      Start         End      Blocks   Id  System
fletch@fletch-desktop:~$ 



Can you tell what the file system is for sdb then?

Thanks again!!

Fletch:popcorn:

---

### Post by taurus on 2008-12-14
> **fletcham said:**
> This is my output from fdisk -l:



fletch@fletch-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee876

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3589    28828611    7  HPFS/NTFS
/dev/sda2            3590       59382   448157272+  83  Linux
/dev/sda3           59383       60801    11398086    f  W95 Ext'd (LBA)
/dev/sda5           59383       60091     5694979+  82  Linux swap / Solaris
/dev/sda6           60092       60092        8001   82  Linux swap / Solaris

[B][COLOR="Blue"]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a750a74

   Device Boot      Start         End      Blocks   Id  System[/COLOR][/B]
fletch@fletch-desktop:~$ 


Can you tell what the file system is for sdb then?

Thanks again!!

Fletch:popcorn:

There is no filesystem on /dev/sdb.  Are you sure you have files on that 1TB harddrive--/dev/sdb?  You need to create a partition, something like /dev/sdb1, and format it first before you can use it.

---

### Post by fletcham on 2008-12-14
Well i didnt actuall do anything to the 1TB hard drive. Just put it in the computer, mounted it and the dragged loads of media files from the other hard drive into it. So what does that mean? Sorry for being thick, im not that good on computers.

thanks again!

---

### Post by taurus on 2008-12-14
Can you access those files on that new drive from windows?  When you first get a new drive, you have to create a partition and put a filesystem on it before you can use it.

---

### Post by fletcham on 2008-12-14
No, in windows when i go to 'my computer' it just shows the 30GB windows partition from my smaller hard drive. Is there something I would need to do to mount it in windows?

Thanks.

---

### Post by taurus on 2008-12-14
So basically you didn't really move a bunch of files to that new harddrive then.

You can boot into Ubuntu and use gparted to create a partition, /dev/sdb1, and format it.  I assume you want to use ntfs filesystem.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted ntfs-config
gksudo gparted
```
Once you have create a partition, /dev/sdb1, for that harddrive, you can have it mount automatically in Ubuntu each time you boot.

```
gksudo ntfs-config
```
Now, reboot into windows and see if you can read and write to that new harddrive.

---

### Post by fletcham on 2008-12-14
errrm... what do you mean 'basically i didnt move a bunch of files to the new hard drive' - i did. Ive got 700GB of files on it and it already mounts automatically in ubuntu and I can access all the files. Ive have only installed XP in the last few days and dont know how to access it through windows.

Do you see what i mean?

---

### Post by fletcham on 2008-12-14
By the way, gparted recognises the drive as being unallocated and unused?

---

### Post by fletcham on 2008-12-14
The 1TB hdd is mounted on my ubuntu desktop. I just right clicked it then went into properties and it says its filesystem ext3. So if i want to format it to NTFS i will have to move everything out of it and then format it... is this right?

Or is there a better way to allow me to access it through windows?

---

### Post by taurus on 2008-12-14
Can you post the output of this command then to see if your 1TB harddrive is really mounted?

```
df -h
```

---

### Post by fletcham on 2008-12-14
fletch@fletch-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             421G   59G  341G  15% /
varrun                950M  116K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   52K  950M   1% /dev
devshm                950M   12K  950M   1% /dev/shm
lrm                   950M   39M  912M   5% /lib/modules/2.6.24-22-generic/volatile
/dev/sdb              917G  654G  217G  76% /media/mynewdrive
fletch@fletch-desktop:~$ 


This is the output?

What do you reckon. Cheer Taurus

---

### Post by taurus on 2008-12-14
> **fletcham said:**
> fletch@fletch-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             421G   59G  341G  15% /
varrun                950M  116K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   52K  950M   1% /dev
devshm                950M   12K  950M   1% /dev/shm
lrm                   950M   39M  912M   5% /lib/modules/2.6.24-22-generic/volatile
**[COLOR="Blue"]/dev/sdb              917G  654G  217G  76% /media/mynewdrive[/COLOR]**
fletch@fletch-desktop:~$ 

This is the output?

What do you reckon. Cheer Taurus

That is one weird looking line especially the first part.  What are the outputs of these commands?

```
mount
ls -la /media/mynewdrive
```
Do you see all the files from the output of the second command?

---

### Post by fletcham on 2008-12-14
fletch@fletch-desktop:~$ ls -la /media/mynewdrive
total 104
drwxrwxr-t  13 root   plugdev  4096 2008-12-11 17:42 .
drwxr-xr-x   5 root   root     4096 2008-12-14 19:06 ..
drwxr-xr-x  15 fletch fletch   4096 2008-12-02 17:33 Audio
drwxr-xr-x  28 fletch fletch   4096 2008-11-20 17:57 Comedy
drwx------  52 fletch fletch  20480 2008-11-23 17:51 Films
-rw-r--r--   1 root   root     6127 2008-12-11 17:42 GRUB
drwx------   2 root   root    16384 2008-10-18 13:25 lost+found
drwx------ 251 fletch fletch  20480 2008-12-10 20:04 Music
drwxr-xr-x   4 fletch fletch   4096 2008-11-03 16:59 My Docs
drwxr-xr-x  12 fletch fletch   4096 2008-09-10 18:01 Photos
drwxr-xr-x   7 fletch fletch   4096 2008-12-10 23:14 random
drwxr-xr-x  15 fletch fletch   4096 2008-12-07 12:26 Sport
drwx------   2 fletch fletch   4096 2008-12-10 22:52 .Trash-fletch
drwxr-xr-x   6 fletch fletch   4096 2008-11-30 11:16 TV Series
fletch@fletch-desktop:~$ 



This is the output from 2nd command.

What was wierd about the first bit. Is there anything you reckon i need to sort out. Im trying to get my system all sorted out nicely at the minute. Cheers again.

---

### Post by taurus on 2008-12-14
Your 1TB harddrive behaves like a raw device (no partition).  What's the output of the first command?  Just want to see the exact filesystem of it.  Looks like ext2/ext3!

---

### Post by fletcham on 2008-12-14
fletch@fletch-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
/dev/sdb on /media/mynewdrive type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
fletch@fletch-desktop:~$ 

This was the result from the code: 'mount'.

 I only bought the 1TB hdd about a month ago and ever since then every time i boot up is starts to scan sdb and it takes a while then stops. It then comes up with loads of writing and eventually says press 'CTRL & D' to cancel something and continue. It then loads up fine and runs normally - takes a while to boot up tho, quite annoying!

---

### Post by taurus on 2008-12-14
Can you post your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by fletcham on 2008-12-14
fletch@fletch-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f43c90ee-e69b-4908-b2cf-e79590581064 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=878d426e-0221-465d-aaf8-a975ec30c4ae none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb    /media/mynewdrive   ext3    defaults     0        2
fletch@fletch-desktop:~$

---

### Post by taurus on 2008-12-14
It's probably best to back up your /media/mynewdrive.  Then, use gparted to create a partition, /dev/sdb1, and format it to ext3.  You need to unmount it first before you can create a partition with gparted.  

Then, edit /etc/fstab and replace the /dev/sdb with /dev/sdb1.

---

### Post by fletcham on 2008-12-14
Nice one Taurus. But wouldn't i want to format it to NTFS tho in order to use it with windows and ubuntu?

---

### Post by solwic on 2008-12-14
> **fletcham said:**
> The 1TB hdd is mounted on my ubuntu desktop. I just right clicked it then went into properties and it says its filesystem ext3. So if i want to format it to NTFS i will have to move everything out of it and then format it... is this right?

Or is there a better way to allow me to access it through windows?

Does Windows XP even recognize hard drives that large?  I know it picked up my 500GB Sata, but still...1TB is pretty big.  

You should be able to go to Control Panel -> Administrative Tasks.  Look for a "Computer" option...it'll open a window and on the left there should be a "Disk Manager" there.  It's been a while since I used Windows, and I can't remember exactly where it is.  

But it should give you the option to delete partitions and make new ones.  Also, before you do *any* work to a hard drive, *always* back the data up.  :)

Good luck!

---

### Post by solwic on 2008-12-14
> **fletcham said:**
> Nice one Taurus. But wouldn't i want to format it to NTFS tho in order to use it with windows and ubuntu?

There are programs that let you use a hard drive formatted with ext in Windows.  But it'll probably perform better in Windows if it's formatted NTFS, yes.

---

### Post by taurus on 2008-12-14
You can format it to ntfs filesystem if you want but windows can read and write to ext2/ext3 with fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by solwic on 2008-12-14
> **taurus said:**
> You can format it to ntfs filesystem if you want but windows can read and write to ext2/ext3 with fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

That's the program I was thinking of.  Forgot what it was called.

---

### Post by fletcham on 2008-12-14
Ok then cool. Is fs driver easy to use and set up?

If you had the option to format toext3 or NTFS what would you go for?

Ta:popcorn:

---

### Post by taurus on 2008-12-14
Ext3 is 100% (and more) better.

---

### Post by solwic on 2008-12-14
> **fletcham said:**
> Ok then cool. Is fs driver easy to use and set up?

If you had the option to format toext3 or NTFS what would you go for?

Ta:popcorn:

I've never used FS Driver, so I wouldn't know about the setup.  

As for choosing a file system...it depends.  If you primarily use Ubuntu, go with Ext and use FS-Driver.  If you primarily use Windows, use actual NTFS.

NTFS will need defragmented, and ext3 (usually) doesn't, which will affect drive speed.  I know defragging a 500GB 3GB/s SATA drive took FOREVER, so 1TB has to be even worse.  

I recommend ext3, but it all depends on what you do with your PC.  

Good luck!

---

### Post by fletcham on 2008-12-14
Ext3 it is then. thanks for the advice!

---

### Post by fletcham on 2008-12-14
Just one more thing while were at it to double check. If i buy a 1TB external HDD to back up on and it comes formatted in FAT32, can i use gparted and format it to ext3? Can I use it on ubuntu with the fat32 format?

Cheers aain :guitar:

---

### Post by taurus on 2008-12-14
Yes, you can read and write to fat32/vfat from Ubuntu.  Just remember that fat32/vfat won't let you write a file larger than 4GB to it.

---

### Post by dwasifar on 2008-12-14
> **fletcham said:**
> Just one more thing while were at it to double check. If i buy a 1TB external HDD to back up on and it comes formatted in FAT32, can i use gparted and format it to ext3? 

Usually the answer to this is yes, you can format your external drive to any filesystem you want.

However, I have run into the occasional external drive enclosure that will not let you partition to Linux/Unix filesystems.  The external enclosure allowed me to USE it with ext3 filesystem, but not CREATE one.  It's very frustrating.  In that situation I was forced to remove the drive from the enclosure and connect it to SATA inside the system to do the partitioning.  
 
If the external enclosure has an eSATA connection, then you can (and should) use that, and you should have no partitioning problems.  If you plan to use USB, you should check the external enclosure's documentation to be sure it does not have this limitation.

BTW: if you want an external drive, it is usually a better idea to buy a bare drive and an external enclosure to put it in, than to buy a preassembled unit.  You are less likely to have compatibility and driver problems that way; and later on when you want a bigger external drive, you can just buy a new bare drive and install it in the enclosure, rather than spending more on a whole new unit.

---

