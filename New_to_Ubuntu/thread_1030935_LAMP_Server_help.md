---
title: "LAMP Server help"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by BeyondThePale on 2009-01-04
Howdy folks.

I have managed to install the LAMP server version of ubuntu, 8.10. I have gotten this installed on an Blue and White G3 tower, and I am able to remotely access it on my home network with Putty. I have also installed Webmin and gotten it working. 

My problem is currently disk management. I have two drives on the machine, a small one for the OS and a larger one for network storage. I had Gnome installed and while it saw the second drive, it couldn't access it. I have since removed the desktop GUI. 

How do I see, manage, and format this second drive at the command line?

---

### Post by Iowan on 2009-01-04
Short of re-running the setup disk partitioner, see if [this]("http://ubuntuforums.org/showthread.php?&t=283131") thread helps.

---

### Post by BeyondThePale on 2009-01-25
Um, wow. That was a ton of info, and I'm pretty newbish.

Listing the hardware on the box, I get that the hard drives available are...

disk:0   This is my boot disk, all looks as it should be here. Logical name hdc. Reads fine.

disk:1   This is my data disk. It's a 200 gig drive, ata, logical name hdd. Doesn't show up annywhere but when I do a "lshw"

Not really sure how to proceed.

---

### Post by callan79 on 2009-01-25
> **BeyondThePale said:**
> Um, wow. That was a ton of info, and I'm pretty newbish.



Hello BeyondThePale,

If you break it down into its individual steps it'll seem easier for you ... at some time we've all been where you are now, sometimes it can seem overwhelming!

Anyway here goes. I have two hard disks in my machine too, so I'll show you what mine says as an example...


(1) Find out what disks you have in the machine

```

callan@brutis:~$ sudo fdisk -l
[sudo] password for callan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc518c518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         272     2184808+  82  Linux swap / Solaris
/dev/sda2             273        1294     8209215   83  Linux
/dev/sda3   *        1295        3875    20731882+   7  HPFS/NTFS
/dev/sda4            3876        9729    47022255   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb45cb45c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401   83  Linux

```

Okay, so on my machine, sda is an 80GB drive which has my operating systems (dual boot Ubuntu/XP) on it. The sdb device is 200GB, and that's for storage, just like yours.

I guess you already know that sda1, sda2 etc refer to the first and second etc partition on the 'sda' device?


(2) Assuming you want to totally blank the second drive and format, first step is to delete any partitions on there and create one or more new partitions :

```

sudo cfdisk /dev/sdb

```

You'll then get a nice CFDISK interface. You can use your keyboard to select an option at the bottom to delete partitions, then create new ones. After you create a new one, set the TYPE to Linux, that's type 83 by the way.


(3) Let's say that you just created one big partition. Now you need to format it :

```

sudo mkfs.ext3 -L fred /dev/sdb1

```

Of course change 'fred' to whatever you want your disk to be called.


(4) Once you've formatted it, you need to mount it. This involves making a mount point within your file system, and then putting the mount details into /etc/fstab. It's easier than you think.

Let's say you will be calling your mount point /media/fred, we need to make the mount point :

```

cd /media
sudo mkdir fred
sudo chown yourusername:yourgroupname fred
ls -l /media/

```

I end up with this, you'll get something similar :

```

drwxr-xr-x  2 callan callan 4096 2009-01-26 10:27 fred

```

Then you need to add the mount details into /etc/fstab so it mounts on boot :

```

sudo nano /etc/fstab

```

Put this line at the end, and make sure that you always have one or blank line at the bottom of /etc/fstab (just go to the end and press enter a few times) :

```

/dev/sdb1  /media/fred  ext3  defaults,auto  0  0

```


(5) Let's try to mount it :

```

sudo mount -a

```

Hopefully you get nothing on your screen - this means success! Now let's check it mounted :

```

mount

```

You should get something like this :

```

/dev/sdb1 on /media/fred type ext3

```

If you do, you've successfully mounted the device.


(6) One last thing you have to do is check the permissions ....

```

ls -l /media/

```

You might find that the owner/group of 'fred' has gone back to root & root. You can change this back to yourself with :

```

sudo chown yourusername:yourgroupname /media/fred

```

Note also if you're playing with network storage and SAMBA etc, you might need to set some different owner/group and permissions for it to work. But that's a conversation for a different thread :-)

Hope this worked for you!

Cheers
Callan

---

### Post by BeyondThePale on 2009-01-26
> **BeyondThePale said:**
> Listing the hardware on the box, I get that the hard drives available are...

disk:0   This is my boot disk, all looks as it should be here. Logical name hdc. Reads fine.

disk:1   This is my data disk. It's a 200 gig drive, ata, logical name hdd. **Doesn't show up anywhere but when I do a "lshw"**

Thanks for the help, but right at the get-go I am not seeing what I should. I don't see the second disk when doing fdisk. Just the main disk.

lshw is the only way I see the drive.

---

### Post by callan79 on 2009-01-26
> **BeyondThePale said:**
> lshw is the only way I see the drive.


Ahh, right...

Could it be possible that the disk has either (1) no partitions defined, or (2) invalid/broken partitions?

Can you do a ```
sudo cfdisk /dev/hdd
``` at all?

CD

---

### Post by BeyondThePale on 2009-01-26
Excellent! It gives me details about the drive. Looks like two partitions.

hdd2  |  no flag  | primary partition |  W95 FAT32  | No Label  |  4466 MB

hdd1  | Boot flag  |  primary partition  |  NTFS  | [] Label  | 195572 MB

8MB free space.

I see a series of options listed below as well. Progress! WHat's the next step? Oh, and thanks again.

---

### Post by callan79 on 2009-01-27
> **BeyondThePale said:**
> Excellent! It gives me details about the drive. Looks like two partitions.

hdd2  |  no flag  | primary partition |  W95 FAT32  | No Label  |  4466 MB
hdd1  | Boot flag  |  primary partition  |  NTFS  | [] Label  | 195572 MB

I see a series of options listed below as well. Progress! WHat's the next step? Oh, and thanks again.


Hi BeyondThePale,

Well, I assume you want to wipe the drive and start again with a clean Linux filesystem etc.

So use the up and down arrows to select a partition, then the left/right arrows to select 'delete' and get rid of all partitions.

Then create a new partition, change the type to Linux (83), write the changes and quit.

Then you can format the filesystem and mount the drive per my previous post....

Easy :)

If you want to keep the existing data though, that's a little more involved :(

Cheers
Callan

---

### Post by BeyondThePale on 2009-01-27
You rock. I hit every step of the way without issue. Just one thing...

Where is my disk? Where is that 200 gig? 

I can get to /media/g3storage (the name I used instead of fred). I am just used to hard drive structures of a:, B:, etc.

---

### Post by callan79 on 2009-01-28
> **BeyondThePale said:**
> I can get to /media/g3storage (the name I used instead of fred). I am just used to hard drive structures of a:, B:, etc.


Hi,

Yep, /media/g3storage/ is your "drive"

In Linux you mount filesystems ("drives") somewhere within your existing directory tree. Take a little bit of getting used to, but is actually pretty cool.

Just be careful of one thing ... remember the g3storage is a directory on your filesystem, right? And then you mount your external drive there.

But if you unplug the 500GB drive, or there is a problem with the mounting, /media/g3storage acts just like a directory on your main system drive.

For example - my father in law has a 200GB system/data drive, plus a 120GB drive purely for backup purposes. For some reason he unplugged the backup drive, so the mount failed. Then when his backups ran, the data just got stored on the main drive, and eventually filled it up.

Just food for thought :)

CD

---

### Post by BeyondThePale on 2009-01-28
I greatly appreciate all of your help. There were times I never thought I'd get it to work, but I have a venerable Blue and White G3 serving up files to my home PCs. I have consolidated our pictures and music library to this and look forward to tinkering further.

Fine community you folks have put together. I might have to stick around a bit.:D

---

