---
title: "Changed mount point, now drive won't mount!"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by PistolPLC on 2009-10-20
Hi - 

So, I'm working on some hard drive sharing problems, and I thought one problem could be that my external hard drive "MyBook" was being mounted somewhere that wasn't working properly.  (Basically, Samba shares folders in all other locations properly, like "/home", but not "/media/MyBook" for some reason.)

So, my genius solution is to right click the MyBook icon in the desktop, go to the tab where I can change "mountpoint", and I put something in like "/home/USBdrive".

Now, MyBook - though it shows up as a possible hard drive option, won't mount anywhere, and I can't get back to that "mountpoint" entry to change it back.  Any help would be appreciated.

And, while you're here, any help on why my samba shares for "/home" work, but don't work for "/media/MyBook" would be appreciated.  (I can both "MyBook" and "Home" in my windows box in the network locations, but I get errors on MyBook, and Home works perfectly.)

Thanks!

PistolPLC

---

### Post by ukripper on 2009-10-20
> **PistolPLC said:**
> Hi - 

So, I'm working on some hard drive sharing problems, and I thought one problem could be that my external hard drive "MyBook" was being mounted somewhere that wasn't working properly.  (Basically, Samba shares folders in all other locations properly, like "/home", but not "/media/MyBook" for some reason.)

So, my genius solution is to right click the MyBook icon in the desktop, go to the tab where I can change "mountpoint", and I put something in like "/home/USBdrive".

Now, MyBook - though it shows up as a possible hard drive option, won't mount anywhere, and I can't get back to that "mountpoint" entry to change it back.  Any help would be appreciated.

And, while you're here, any help on why my samba shares for "/home" work, but don't work for "/media/MyBook" would be appreciated.  (I can both "MyBook" and "Home" in my windows box in the network locations, but I get errors on MyBook, and Home works perfectly.)

Thanks!

PistolPLC

can you post output of the following commands:
```
sudo fdisk -l
```

and 

```
sudo mount
```

---

### Post by PistolPLC on 2009-10-20
Sure - 
--------------------------
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xab42ab42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         685     5178568+   b  W95 FAT32
/dev/sda2   *         686        5452    36038520    7  HPFS/NTFS
/dev/sda3            5453       10337    36930600    5  Extended
/dev/sda5            5453       10137    35418568+  83  Linux
/dev/sda6           10138       10337     1511968+  82  Linux swap / Solaris

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       38913   312568641    c  W95 FAT32 (LBA)
--------------------
AND
--------------------
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nagle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nagle)
--------------------

If it matters, the drive that I've been messing with (MyBook) is dev/sdf1.

Thanks!

---

### Post by ukripper on 2009-10-20
I assume your MYBOOK is FAT32 partioned?

---

### Post by PistolPLC on 2009-10-20
That's correct.

---

### Post by ukripper on 2009-10-20
To manually mount your Fat32 drive you need to do the following:
create a directory if doesn't exist:
```
sudo mkdir /media/MyBook
```

then mount your drive by using following command:
```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sdf1 /media/MyBook
```

if that works then I will show you how to add this in fstab which will automatically mount your drive and reboot.

---

### Post by PistolPLC on 2009-10-20
I assume it worked...I didn't seem to get any errors.  The output of the last command was:

-----------------
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


-PistolPLC

---

### Post by PistolPLC on 2009-10-20
Actually, if that was supposed to fully mount the drive as it was before, then it didn't work.  I don't see it on the desktop, and when I browse in the file browser to /media/MyBook, its empty.

Is that what should happen?

---

### Post by ukripper on 2009-10-20
> **PistolPLC said:**
> Actually, if that was supposed to fully mount the drive as it was before, then it didn't work.  I don't see it on the desktop, and when I browse in the file browser to /media/MyBook, its empty.

Is that what should happen?

Yes i was only testing it. If you do the following and see if it mounts on your desktop and lets you browse.

```
sudo umount /media/MyBook
```

edit fstab ```
sudo gedit /etc/fstab
```add below line at bottom of your fstab as :
```
/dev/sdf1         /media/MyBook           vfat   user,fmask=0111,dmask=0000            0   0
```

save it and close.

then run this command:
```
sudo mount -a
```

this should mount your drive on your desktop.

---

### Post by PistolPLC on 2009-10-20
AHA!  It Worked!  Now, I assume I should still go in and get rid of my alternate and incorrect mountpoint?  

Thank you so much for your help!!

-PistolPLC

---

### Post by ukripper on 2009-10-20
> **PistolPLC said:**
> AHA!  It Worked!  Now, I assume I should still go in and get rid of my alternate and incorrect mountpoint?  

Thank you so much for your help!!

-PistolPLC

No problem. It will mount automatically for you at each reboot, given that your drive is switched on.

Have fun!:)

---

### Post by ukripper on 2009-10-20
what was your alternate mountpoint?

---

### Post by PistolPLC on 2009-10-20
How I got into this whole mess in the first place.  (Right Click -> Properties -> Settings -> Mountpoint) Changed from blank to "/media/USB".

I deleted it again, so back to the usual blank there.

Thanks again.

---

### Post by ukripper on 2009-10-20
> **PistolPLC said:**
> How I got into this whole mess in the first place.  (Right Click -> Properties -> Settings -> Mountpoint) Changed from blank to "/media/USB".

I deleted it again, so back to the usual blank there.

Thanks again.

Do you still have blank icon now? Is you drive mounting ok?

---

### Post by blur xc on 2009-10-20
> **ukripper said:**
> Yes i was only testing it. If you do the following and see if it mounts on your desktop and lets you browse.

```
sudo umount /media/MyBook
```edit fstab ```
sudo gedit /etc/fstab
```add below line at bottom of your fstab as :
```
/dev/sdf1         /media/MyBook           vfat   user,fmask=0111,dmask=0000            0   0
```save it and close.

then run this command:
```
sudo mount -a
```this should mount your drive on your desktop.


I would reccomend using the drives UUID instead of /dev/sdf1 designation.  I had my fstab set to automount my external drive, /dev/sdb1, but one day, after a boot up, it didn't mount.  After doing a sudo fdisk -l, I found it was no /dev/sdg1.  The letter is assigned first come, first serve as the computer boots and discovers the devices.  Sometimes it finds them in a different order than other times.  The UUID never changes and is unique to the device.  

Run blkid to find the uuid number, and instead of /dev/sdf1, enter UUID=<crazy long number w/o quotes>

BM

---

### Post by ukripper on 2009-10-20
> **blur xc said:**
> I would reccomend using the drives UUID instead of /dev/sdf1 designation.  I had my fstab set to automount my external drive, /dev/sdb1, but one day, after a boot up, it didn't mount.  After doing a sudo fdisk -l, I found it was no /dev/sdg1.  The letter is assigned first come, first serve as the computer boots and discovers the devices.  Sometimes it finds them in a different order than other times.  The UUID never changes and is unique to the device.  

Run blkid to find the uuid number, and instead of /dev/sdf1, enter UUID=<crazy long number w/o quotes>

BM

Even I would opt up for UUID. But in this situation I just needed to make sure everything is working for OP and then we can replace /dev/sdf1 to UUID using blkid.

---

### Post by PistolPLC on 2009-10-20
UKRIPPER - things are working fine now.  I just meant that I should "undo" the thing that I did in the first place.  (which was entering "/media/usb" into that mountpoint entry...)  But your fix worked wonderfully.

Regarding the BLKID part - I'll see if I can find a tutorial or some other resources, and along with what you described in your posts, I'll see if I can get that done.  If not, I'm sure I'll be back on this thread hoping you'll be willing to help me out again...

Thanks much for the quick and detailed responses!

PistolPLC

---

### Post by ukripper on 2009-10-20
> **PistolPLC said:**
> UKRIPPER - things are working fine now.  I just meant that I should "undo" the thing that I did in the first place.  (which was entering "/media/usb" into that mountpoint entry...)  But your fix worked wonderfully.

Regarding the BLKID part - I'll see if I can find a tutorial or some other resources, and along with what you described in your posts, I'll see if I can get that done.  If not, I'm sure I'll be back on this thread hoping you'll be willing to help me out again...

Thanks much for the quick and detailed responses!

PistolPLC


All you need to do is as following for UUID:

find your UUID of your partition:
```
sudo blkid
```

in blkid's output look for /dev/sdf1 and corresponding UUID. Copy that UUID and open your fstab:
```
sudo gedit fstab
```
replace /dev/sdf1 with > UUID=paste your copied UUID 

save and close fstab and thats it. 

```
sudo mount -a
```
it should mount fine if it doesn't post error here, we will help you.

Goodluck!

---

