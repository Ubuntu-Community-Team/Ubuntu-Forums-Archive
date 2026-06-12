---
title: "Mount this?! NTFS, FAT32, and I'm confused"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by Wafflesrevenge on 2007-02-28
Hi, my name is WafflesRevenge and I've been using the Internet forever. Windows died last week and after taking inventory I realized there are no programs I use that keep me attached to it. So after LiveCD'n it I did an install, things went well when I finally forced grub to end up on the right drive (I disconnected my IDE drives during install). But now, I cannot get my old NTFS drives to mount...at all.

This is what fdisk -l shows

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        8950    71890843+   7  HPFS/NTFS
/dev/hdb2            8951       19457    84397477+   b  W95 FAT32

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4314    34652173+  83  Linux
/dev/sda2            4315        4500     1494045    5  Extended
/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris


Also I don't know if this will help but heck, here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=acad8806-1394-4208-a7e3-42c873073c74 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=21a1c726-0f04-44ad-afdf-c15f2bc8c358 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


As you can see, I have three drives, primary boot drive and Ubuntu install is the sda, hda1 and hdb1 both contain valuable media information I want to retain (my mp3/anime/personal files/etc)

My ultimate goal is to get all of the data easily accessible and shareable across my network as the next computer I have to fix is my Powerbook G4 and I will want to load it up with all of my tunes, right :)

So, lets see...I'll get into that FAT32 drive first

sudo mount -a /dev/hdb2 /mnt/hdb2

I go into file browser and check on this one, sure enough /mnt/hdb2 shows 80gigs of free space which is the size of /dev/hdb2, it also shows a directory path of /mnt/hdb2/hdb1 & /mnt/hdb2/hdb2 Furthermore, I cannot place files there, so neat I think I mounted something, but too bad I can't do anything with it.

I don't understand what is going on here, thats ok with me and I'll try something else the meantime...  [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

So I've run through this tutorial, its actually pretty good, I did copy and paste AND read...but
this command:

sudo apt-get install ntfs-config

returns this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config

Now, I also get this error from both mirrors, so I don't know what is going on, apparently I won't be able to mount my NTFS drives until I can get ntfs-config so while I have all this hard drive space and an exquisite mp3 collection, I can't use any of it.

Maybe it is just me but this feels far to complicated in order to just access some disks, but then again I am a newbie in Ubuntu. I really want to get over this hurdle because afterwards I see a bright future with linux, but I can't sit at my PC without my music collection

Thank you in advance, I hope I can find this thread when I come back from the bar :) (I found the instant email notification option)


*EDIT* I'm using 6.10 (edgy) dunno if that helps

---

### Post by Yoooder on 2007-02-28
Wow!  You've managed about 5 questions in 1, so let my try to answer one or two of them.

First: a comment.  

> So, lets see...I'll get into that FAT32 drive first

sudo mount -a /dev/hdb2 /mnt/hdb2

I go into file browser and check on this one, sure enough /mnt/hdb2 shows 80gigs of free space which is the size of /dev/hdb2, it also shows a directory path of /mnt/hdb2/hdb1 & /mnt/hdb2/hdb2 Furthermore, I cannot place files there, so neat I think I mounted something, but too bad I can't do anything with it.

You have my head spinning with this command.  mount -a will mount all filesystems listed in your fstab, I've never used it with a device and folder appended to it.

After looking at your /etc/fstab file I'm not seeing either your /dev/hdb listed anywhere, so I presume it is taking it from your command arguments.  However, you should end up with /dev/hdb2 mounted to /mnt/hdb2.  **I am really confused about why you would be seeing /mnt/hdb2/hdb1 and /mnt/hdb2/hdb2.**  The only situation that would cause this is if your /dev/hdb2 partition contains 2 folders, name hdb1 and hdb2

Here is a short run down of what you can try.
 1 - Make sure to unmount /dev/hda1 /dev/hdb1 and /dev/hdb2
 2 - Let's try to mount your FAT32 partition first.  Try > mount -t  vfat /dev/hdb2 /mnt/hdb2 That should make the contents of your FAT32 partition available to you from the /mnt/hdb2 folder.  Here's one catch: Fat32 doesn't support user permissions, and as such if you wish to have write access to the drive you will need to mount it under your user id (basically saying your user owns that partition).  If you want to assign this partition to the user you created during install then that userid should be 1000.

To find out for sure, run this:
> cat /etc/passwd | grep $USER 
which will give you a line like "steve:x:1000:1000:Steve,,,:/home/steve:/bin/bash"

The first number (1000 in this case) is your uid (user-id), the second (also 1000) is your gid (group-id)

Anyways, the command you will most likely need **to mount your hdb2 partition with write access by the user you setup during installation** is:
> mount -t vfat -o uid=1000 /dev/hdb2 /mnt/hdb2

With that you should have access to your FAT32 partition with write permissions.

Here's the commands to mount your ntfs partitons Read-Only.  I can't help you with their write permissions, I've never played with it.  But this should at least get you access to their contents:

> mount -t ntfs /dev/hda1 /mnt/hda1

and

mount -t ntfs /dev/hdb1 /mnt/hdb1

---

### Post by Wafflesrevenge on 2007-02-28
Yooder, that was it. I just needed to include the "-o uid" string. Can I set this up so that it automatically loads these drives at startup?

Again, thank you a million! I feel like I've recovered my life :)

---

### Post by Yoooder on 2007-03-01
> **Wafflesrevenge said:**
> Yooder, that was it. I just needed to include the "-o uid" string. Can I set this up so that it automatically loads these drives at startup?

Again, thank you a million! I feel like I've recovered my life :)

Yep, you can get these to load on boot quite easily...

Here's your current fstab: 
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=acad8806-1394-4208-a7e3-42c873073c74 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=21a1c726-0f04-44ad-afdf-c15f2bc8c358 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

You'll need to add a new line to the end for each partition to mount.

For your FAT32:
> /dev/hdb2 /mnt/hdb2 vfat uid=1000 0 0

And for your NTFS partitons (remember, one for each, just fill in the X's):
> /dev/hdXX /mount /hdXX ntfs user 0 0

I think those should take care of you.  You should do some reading into fstab entries, as there's quite a few different options that you can try using with them.

---

### Post by xTonyx on 2007-03-06
Sorry to butt in, I think this should help with a FAT32 mounting problem I have, cheers!!

Just wondered if instead of making a user the owner of the drive with "-o uid=1000" command is it possible to make a group the owner, to allow read write access to a number of users in the same group? at a guess say replacing it with "-o gid=1000" ?

---

