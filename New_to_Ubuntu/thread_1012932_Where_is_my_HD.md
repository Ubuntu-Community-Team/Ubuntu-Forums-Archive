---
title: "Where is my HD?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by abo999 on 2008-12-16
I've been about 24 hours with Ubuntu now and after some teething troubles (read: user error...) it looks like I've got a stable desktop to work with.

I've converted everything over from Windows XP. I started off with a single IDE HD and I've just added a pair of SATA HD's which I want to configure as a RAID.

I've added the 'dmraid' package and the GParted now sees them as a single entity: /dev/mapper/nvidia_becfbcee and I've formatted it to ext3.

Now, bearing in mind I've only ever used Windows... Where is the drive? I'm guessing it will need to be mounted?

---

### Post by taurus on 2008-12-16
Yes, you need to mount them first before you can use/access them.  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by abo999 on 2008-12-16
Thanks! Here is the output.

There is a FAT32 HD connected at the moment called 'Music Drive'. You can ignore this for the moment I guess, I'm just copying the files across to my 'music' folder, and then I intend to format this also.

neal@neal-desktop:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbeadbea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14334   115137823+  83  Linux
/dev/sdc2           14335       14946     4915890    5  Extended
/dev/sdc5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcea630b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/dm-0: 122.9 GB, 122985644032 bytes
255 heads, 63 sectors/track, 14952 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table
neal@neal-desktop:~$ sudo blkid
/dev/sdc1: UUID="75f5a58e-44ce-4731-80e0-ff7ddb4972e8" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="2b387174-8e99-47d6-ad0b-d5c59fab5a94" 
/dev/sdd1: UUID="DC8837FD8837D52C" LABEL="Music Drive" TYPE="ntfs" 
/dev/mapper/nvidia_becfbcee: UUID="0e661faa-653c-4e65-be97-601e87af7876" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda: UUID="0e661faa-653c-4e65-be97-601e87af7876" SEC_TYPE="ext2" TYPE="ext3" 
neal@neal-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=75f5a58e-44ce-4731-80e0-ff7ddb4972e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2b387174-8e99-47d6-ad0b-d5c59fab5a94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
neal@neal-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             109G   27G   77G  26% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  104K 1014M   1% /dev
devshm               1014M   52K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon      109G   27G   77G  26% /home/neal/.gvfs
/dev/sdd1              56G   54G  2.4G  96% /media/Music Drive

---

### Post by donkyhotay on 2008-12-16
Also be aware that drives work different under *nix then they do in windows. Although you may automatically see some shortcuts in your GUI any mounted drives are not as seperate like they are in windows (i.e. C: & D: & etc.), additional mounted drives will be part of the overall file structure and appear as folders somewhere within it (usually /mnt). This is really only applicable when using CLI as generally gnome/nautilus will automatically create/display links to the mounted drives for convenience purposes so it appears more windows-ish.

---

### Post by Hospadar on 2008-12-16
In ubuntu, all your non-root drives generally get mounted in /media
So take a look there and see what you can see

---

### Post by donkyhotay on 2008-12-16
> **Hospadar said:**
> In ubuntu, all your non-root drives generally get mounted in /media
So take a look there and see what you can see

Oops, your right hospadar, sorry about the misinformation. )c:

---

### Post by abo999 on 2008-12-16
Looks like everything is working now. I used the partition editor to create a single large ext3 partition, and then mounted it from the terminal using sudo mount /dev/dm-0 /media/storage and Bob's your uncle; 113GiB of storage :D

---

### Post by abo999 on 2008-12-16
Ah scratch that; I've just rebooted the machine and the dm-0 didn't mount. I needed to re-mount it again in the terminal. Is there a way to mount this during boot?

And... I can't create folders on it

---

### Post by abo999 on 2008-12-18
Ok, still having problems with this...

I was having a display driver issue in Heron, so I trashed the system and installed Ibex instead. All is well, apart from this raid thing.

If I do sudo fdisk -l I get:

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006d4e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14952   120101908+  83  Linux

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbeadbea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14334   115137823+  83  Linux
/dev/sdc2           14335       14946     4915890    5  Extended
/dev/sdc5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb04f0f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    c  W95 FAT32 (LBA)

So fdisk is seeing the two individual drives but not the raid. Gparted does show the raid as /dev/mapper/nvidia_becfbcee1 formatted to ext3.

blkid gives:

/dev/sdc1: UUID="61539b8f-0b64-47a1-ae92-e9ff4743bce2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="625d3158-c0b2-4696-b007-1bcc257b4a23" 
/dev/sdd1: LABEL="UNTITLED" UUID="0000-0000" TYPE="vfat" 
/dev/sda1: UUID="063afbe1-334e-4925-8b7d-95a2d2160a90" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/nvidia_becfbcee1: UUID="063afbe1-334e-4925-8b7d-95a2d2160a90" SEC_TYPE="ext2" TYPE="ext3" 

so the raid is showing there...

Can anyone tell me how to find out the volume name, then maybe I can have a go at mounting it?

---

### Post by Songwind on 2008-12-18
It looks like it's "/dev/mapper/nvidia_becfbcee1"

So that's the device.  Obviously you figured out how to mount it interactively.  To get it to mount automatically, you need to add a line to /etc/fstab.

You can pretty much copy the line for your "/" drive, and just replace "/" with whatever location you want to use, and the other drive's UUID with the one from blkid.  The "sudo mount -a" will mount everything that's in fstab that is not yet mounted.

By default, it will probably only be writable by root.  You can fix this by issuing:
**sudo chmod -R a+rwx /your/mountpoint/**  (this changes it to give read, write, and execute to all users)

If you want a particular user to have sole access, you can change ownership to that user with **chown** and then **sudo chmod 700 /your/mountpoint** which will give only that user right to it.

---

### Post by Malalo on 2008-12-18
(Ubuntu n00b here)

Friends told me that Ubuntu (as in other distros) has almost no command line anymore... from what I see here (and in many other threads) that statement wasn't completely true....

---

### Post by Duck2006 on 2008-12-18
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Songwind on 2008-12-18
> Friends told me that Ubuntu (as in other distros) has almost no command line anymore... from what I see here (and in many other threads) that statement wasn't completely true....

I think the need for CLI depends on a lot of factors.  Some of them depend on exactly what way you want to do something.  For example, if the OP wanted to access his drive and that's it, he would be fine without any CLI.  Also, some things are doable in the gui but are faster or simpler to do via command line.

Case in point.  Changing permissions and owners is doable from a root session of nautilus, but it's easier to just give someone the command input string, rather than saying "press F2 and run "gksudo nautilus /"  "Now navigate to the directory."  "Right click."  Etc.

Some of these tasks are doable with GUI utilities that are perhaps not yet installed.

So I think there are a lot of qualifiers that some Linux evangelists leave out when they talk about the command line.

---

### Post by abo999 on 2008-12-18
> **Songwind said:**
> It looks like it's "/dev/mapper/nvidia_becfbcee1"

So that's the device.

Thanks, dunno why but I was expecting to see a sda-type volume name or something...

Anyway, that all did the trick; I have a nice 113 GiB of RAID storage now.

Only thing is, the 250GB FAT32 drive in there has disappeared...

---

### Post by donkyhotay on 2008-12-18
> **Malalo said:**
> (Ubuntu n00b here)

Friends told me that Ubuntu (as in other distros) has almost no command line anymore... from what I see here (and in many other threads) that statement wasn't completely true....

Some things are easier to do with CLI some things are easier to do with GUI. Personally I use both depending on what I'm trying to do. Usually when giving help/advice I go with CLI as there is less likely to be confusion by telling someone type this into the terminal.
```
sudo apt-get install glob2
```
then explaining go into synaptic, update the repositories, do a search for glob2, click on the box, etc.

---

### Post by abo999 on 2008-12-18
Ah, of course I can mount a FAT32 drive just like any other drive, so I've created a mount point and I can use the mount /dev/sdd1 successfully in the terminal.

Only snag is, I've tried entering a line into fstab to mount it on boot like the other drive I just did, but it doesn't mount. Here is the fstab entry:

# /dev/sdd1
UUID=0000-0000
/dev/sdd1 /media/winHD vfat defaults,errors=remount-ro 0

fdisk -l shows:

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb04f0f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    c  W95 FAT32 (LBA)

and blkid:

/dev/sdd1: LABEL="UNTITLED" UUID="0000-0000" TYPE="vfat" 

Can anyone suggest a correct entry for fstab?

Cheers

---

### Post by Duck2006 on 2008-12-18
This will help.

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by abo999 on 2008-12-19
Yeas that helped no end. I now have an automatically mounting FAT32 HD, thanks.

Just need to fix my graphics flicker now and the system will be perfect.

---

### Post by pietjanjaap on 2008-12-19
gksudo pysdm
With this you can with gui(grafical), mount a harddisk to a file.

---

### Post by Malalo on 2008-12-19
> **donkyhotay said:**
> Some things are easier to do with CLI some things are easier to do with GUI. Personally I use both depending on what I'm trying to do. 

Right... I found an analogy, it's better to type "ipconfig /all" in a DOS shell than trying to find all the network info in windows GUI... Guess it's the same here...

And my apologies to the OP for starting a new subject in his thread...

---

