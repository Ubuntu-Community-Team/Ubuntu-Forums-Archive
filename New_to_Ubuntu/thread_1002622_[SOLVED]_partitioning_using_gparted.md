---
title: "[SOLVED] partitioning using gparted"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-05
file:///home/nigel/Pictures/Screenshot.png
 the above screenshot (i hope it has worked)  shows my partition/file system on GParted.  i see that when i hilight eg sda2   vista  and then select partition/format to  i get a range of destinations such as 
ext2  ext3 linux swap etc.  am i right in believing that by selecting eg  ext3 the space currently used by for example vista would be transferred and formatted so it is included as a part of that destination?  so the file space currently occupied by vista wold be formatted clean and the ext3 space which currently has about 50GB of which just over half is used up would gain all this space - become a bigger 'linux' drive.  can i use this to add nearly all of the drives currently occupied by vista/winre and maybe also data (i suspect this is all windows data) to the linux areas as if that is how it was originally partitioned?
would you mind making any answer you may be able to give as simple and point and click as possible, otherwise i will find it hard to understand and its pretty difficult as it is.
thanks loads for any help you can offer
nigel

---

### Post by OldGrey on 2008-12-05
Nigel, cannot seen the screenshot. Am I right in thinking that you want to wipe Vista from you disc and expand the linux partition to fill the space?

---

### Post by capnthommo on 2008-12-05
1.  sorry you cant see the screenshot - it seems to work sometimes, but getting that sorted is a lower priority.
yes thats exactly what i want to do: ny suggestions?
thanks
nigel

---

### Post by unutbu on 2008-12-05
Please open a terminal and type
```

sudo fdisk -l
```

(minus lowercase L). Post the output. This will give us information about what your partitions currently look like.

Is there any data on these partitions that you want to preserve?

Then describe what partition you want to end up with. For example:
```

Partition    
1             Vista OS          20 GB
2             Linux OS          20 GB
3             Data              Rest
4             Linux swap space  1 GB
...

```

Given this information, we can tell you how to use GParted to achieve the goal.

---

### Post by capnthommo on 2008-12-05
hi unutbu  here it is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193        4701    36218542+   7  HPFS/NTFS
/dev/sda3            4702       10632    47640757+   7  HPFS/NTFS
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris
nigel@nigel-laptop:~$ 

what i want to do is get rid of the windowsre/vista currently on sda 1 and 2, and also the windows data which i believe is on sda3.  what i want to do is turn over the whole disk to ubuntu and get rid of windows totally - i havent used any for days now and see minimal likelihood of wanting to.  if i need windows i will use the family desktop.
thanks
nigel

---

### Post by capnthommo on 2008-12-05
also sda 4,5 and 6 have a key icon next to them on the GParted screen, does this mean access is restricted?
nigel

---

### Post by capnthommo on 2008-12-05
sorry, i wasn't all that clear was i?
what i want to achiev is something like
sda1     ubuntu/linux   60 (ish)  GB
sda2     data           rest
sda3     swaps           3 or 4 GB

thanks again
nigel

---

### Post by Elfy on 2008-12-05
If you are not in the livecd you will not be able to touch the linux partitions - if you are in the livecd then at the moment you see the padlock because swap is being used.

Right click sda6 and swapoff - once it has refreshed the lock should be gone.

You'll now be able to do as you wish.

Your existing sda4,5,6 will always be known as such afaik unless you delete and start again - which is a lot of work.

You can delete the ntfs partitions and then resize the extended partition to include it, you can also move partitions about - but that will likely take a _long_ time to accomplish.

Much the simplest thing to do, and I would do so in your position, would be to just create a new ext3 partition in the unallocated space once ntfs is gone and then mount that in your install as a data partition.

The choice is yours :)

One last thing - if you have data you can't afford to lose makes sure you have working backups - you are going to be working on partitions and accidents can happen.

---

### Post by capnthommo on 2008-12-05
okay so you suggest deleting ntfs partitions.  dont let my highly fluent techy talk fool you, i am really as unskilled as a particularly dim block of wood.  do you mean delete these as in hilight and click on the trashcan at the top of the GParted screen?
and create a new ext 3 partition and mount it as a data platform?  im not clearwhat this means.  also this does not allow me to increase the space available for system and apps does it - because i still cant increase the size of sda4 or 5.
can you help me here?
nigel

---

### Post by mariane_08 on 2008-12-05
> **capnthommo said:**
> okay so you suggest deleting ntfs partitions.  dont let my highly fluent techy talk fool you, i am really as unskilled as a particularly dim block of wood.  do you mean delete these as in hilight and click on the trashcan at the top of the GParted screen?
and create a new ext 3 partition and mount it as a data platform?  im not clearwhat this means.  also this does not allow me to increase the space available for system and apps does it - because i still cant increase the size of sda4 or 5.
can you help me here?
nigel

Nigel,

Forest Pixy/others will have to answer the first part, I cant quite remember the exact steps.

BUT.. all I can say is when I used GParted it was very easy and self evident. No problems what so ever!

Mounting the free space as a data partition obviously wont allow you to increase the size of existing partitions but you can store all your personal files there, will be readable from the other and if you have to reinstall or change your installion they wont be touched

---

### Post by capnthommo on 2008-12-05
thanks to everybody, i managed to put together somthing that i think has worked.  my partitions are now as follows

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris

Partition table entries are not in disk order,

i hope this works.  at least i now look to have reclaimed the space sacrificed to windows systems.  if it doesnt work then i suppose its a complete ubuntu reinstall and enter it all manually.  anyway, i'm going to bite the bullet and reboot now, see if it all works.  wish me luck
thanks again for the help
nigel):P

---

### Post by capnthommo on 2008-12-05
right.  i'm back.  no problems with anything (fingers X'd) and i dunno, but it seems a bit quicker with loading up apps and things - just gnerally snappier.  i now have two mountable media 'drives'of arond 50 GB each in my places menu though what i do with them i am uncertain at present.  would like one linked to the 'system' side of it for running software and so on and the other linked up as data storage.  that seems to be the most logical but now i need to think how to do it.  suggestions welcome anyone.
anyhow, thanks again to evryone who helped, i now have shot of windows/vista so hey ho for the wide blue yonder.
cheers peeps
nigel
:guitar:

---

### Post by unutbu on 2008-12-05
Congratulations on your successful repartitioning, capnthommo!

On thing you could do with the extra partitions is migrate data to one of them.

For example,

If you have music in /home/user/Music, then you could:

copy /home/user/Music to /media/disk/Music 
delete /home/user/Music
make a symlink from /home/user/Music to /media/disk/Music

This transfers the data to your new partition, and at the same time allows you to access it through /home/user/Music, so there is no essential change in how you access or write to the directory.

To make the symlink from the command line:
```

ln -s /media/disk/Music /home/user/Music
```

To make a symlink using nautilus, see [http://linux.about.com/library/gnome/blgnome6n6l.htm](http://linux.about.com/library/gnome/blgnome6n6l.htm).

Once you migrate all your home data over, you will have a data partition.
There are a number of advantages to having a separate data partition:

[list]
[*]you can then install a new operating system on sda5 without losing your data
[*]you can install a second operating system on sda2 and link it up to the data on sda1 and thus have 2 operating systems sharing the same data files.
[*]you can easily back up your data:
```
sudo rsync -a /media/disk/ /media/disk-1/
```
This would copy everything in /media/disk to /media/disk-1.
[/list]


If you would like to change where the new partitions get mounted (from say /media/disk to /data for example), then post the output of 
```

blkid 
```

and
```

cat /etc/fstab
```

and we can tell you how to do that too.

---

### Post by capnthommo on 2008-12-05
yes i spoke too soon.  i find i cant save any text files to the new 'drives' i think since they are called media and media1 that they are for eg music and photo files.  it would be best to have them one as media and the other for text (word process and spreads - open office etc)  i shall postyou the out put and see how to go from there.  i presume the drives (is that the right term?) were default formatted for media files.  i shall just go and check save a music track and report back later.  perhaps i sholdn't have marked the thread closed quite so early,  thanks again
nigel

---

### Post by capnthommo on 2008-12-05
yes i cant save music or image files either.  i shall look into this and raise another thread if i cany get around it.  strangely i seem to be openind in dolphin now too.  wasnt before.  odd.  time to go away and do some checking , i think.
nigel

---

### Post by Elfy on 2008-12-05
Best would be to allow them to mount on boot - you need to do 2/3 things to get them working properly.

1 - make directories to mount folders in
2 - edit fstab to include you 2 new drives
3 - edit permissions

This is a post from a similar thread that I helped on - [http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

This is  athread on fstab, detailed indeed which covers the same ground - it's where I went fro my information in the first place - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by capnthommo on 2008-12-05
thanks yet again.  i shall look at those threads cos at the moment i  have just got two big empty boxes which i cant put anything in.  not a problem at present as i have plenty of space but it will run short one day.  and if there is one thing i loathe it is slow computers.  just want the thing to work logically and intuitively instead of the windows way - i have watched the desktop slow down progressively over twoyears despite whatever i did to maintain it.  thanks again for the advice
nigel

---

### Post by Elfy on 2008-12-05
Just do it logically step by step and you should be fine - stop if you get problems and ask then rather than just plough on regardless.

Nice to not be reading a panic got to do it yesterday thread for a change :)

If all goes as it should then the task itself shouldn't take any longer than 5 minutes once you are ready.

---

### Post by capnthommo on 2008-12-08
can you help me some more?  i have got to the point where i have removed vista from my system and reclaimed the disk space and created 2 new partitions from the space where windows used to be.  this gives me a lot more room but i need some help in making it actually usable.
here is a copy of how my partitions are at the moment:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x939aab47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6238       12525    50508360   83  Linux
/dev/sda2               1        6237    50098671   83  Linux
/dev/sda4           12526       19457    55681290    5  Extended
/dev/sda5           12526       19168    53359866   83  Linux
/dev/sda6           19169       19457     2321361   82  Linux swap / Solaris

Partition table entries are not in disk order

this is what these actually are
                   directory      type
SDA1 is listed as /media/disk-1   ext3
SDA2 is listed as /media.disk     ext3
SDA5 is listed as /               ext3
the first 2 of these are the new partitions created under GParted

i have tried and am not able to save or move data to either /media/disk-1 or /media/disk 
i would like to achieve 3 things, ideally,  
1. to expand the space available for installation and running of apps/programmes/system.
2. expand the space available for data/media storage and storage of backup data (i am not sure where to put this. i do not want it clogging up my system but want it available and usable if needed - some sort of 'off machine' storage would be ideal but my attempts to create disks that actually work have not been successful so far)
3. ensure that backups are running correctly and most importantly able to restart and restore my system and data files if the worst should happen.
i am afraid i have been pretty long winded again here - sorry. 


what do i need to do now.  remember, i am not very familiar with command line operation so it will need to be explained in simple terms. sorry.
i feel like i'm so near to what i want and yet so far!
thanks a lot
nigel

---

### Post by unutbu on 2008-12-08
Here is what I suggest: 

```
sda2 (47.8 GiB)    /data
sda1 (48.2 GiB)    /backup
sda5 (50.9 GiB)    /
sda6  (2.2 GiB)    (swap)
```

/data would hold your Music, Pictures, Documents, etc. Everything that is important enough to need backing up should be put in /data. This would satisfy your Goal #2.

/backup can be used to backup /data. The command to do so (as mentioned previously) is super-simple:
```

sudo rsync -a /data/ /backup
```

Backing up your data satisfies 90% of Goal #3. It backs up the data, but not your operating system. To my way of thinking, backing up the OS is not critical, because reinstalling Ubuntu only takes about 30 minutes from a LiveCD, and installing extra packages is easy. If you keep notes on changes you make to the system, it is not difficult to reproduce them in the future if you need to. If you had a third empty partition it would be possible to backup the OS as well, but as you become more familiar with Ubuntu, I think you will find that it is not necessary.

By moving all of your home data off of sda5 (/) and on to sda2 (/data), you will have 50.9 GiB for your operating system. That should be plenty of space to satisfy your Goal #1.

If this is what you'd like, then I can help you through all the steps it would take.
The first step would be to mount your sda1 and sda2 at /backup and /data. 
For us to give you explicit instructions on how to do so, please post the output of 
```

blkid
```
and
```

cat /etc/fstab
```

---

### Post by Elfy on 2008-12-08
```
sudo blkid
``` :)

(if blkid fails on it's own)

---

### Post by unutbu on 2008-12-08
Hi forestpixie! Is "sudo blkid" really necessary? On my machine "blkid" and "sudo blkid" return the same results...

---

### Post by Elfy on 2008-12-08
Last time I tried blkid it failed miserably without sudo, unless I was in recovery mode.

Just checked and seen that it's working without - now I'm left wondering what's happened here ;)

---

### Post by capnthommo on 2008-12-08
hi unutbu and forestpixie, good to have you back again since you both have been involved on this one before.  here are the results of the instructions you suggested
nigel@nigel-laptop:~$ blkid
/dev/sda1: UUID="E438053038050372" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="9EE40838E40814E5" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="DE040C06040BDFFF" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="8cd3e712-cd87-4d00-8ca3-691f3c3a5ad4" TYPE="ext3" 
/dev/sda6: UUID="55bd85f1-5b61-4c73-a979-cde9d2ce028d" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
nigel@nigel-laptop:~$ 
nigel@nigel-laptop:~$ 
nigel@nigel-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8cd3e712-cd87-4d00-8ca3-691f3c3a5ad4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=55bd85f1-5b61-4c73-a979-cde9d2ce028d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
nigel@nigel-laptop:~$ 
probably one for another time, but i also did another backup using sbackup and now sda5 seems to be 80% used - should i worry?
thanks for the help
nigel

---

### Post by unutbu on 2008-12-08
Notice that the output of blkid says
```

/dev/sda1: UUID="E438053038050372" LABEL="WinRE" TYPE="ntfs"
/dev/sda2: UUID="9EE40838E40814E5" LABEL="Vista" TYPE="ntfs"

```
This means that sda1 and sda2 have (if anything) ntfs filesystems inside the partitions.
To make faithful backups of sda5, which has an ext3 filesystem, we will need to format sda1 and sda2 to be ext3 as well.

So the first step is to run

```
sudo mkfs.ext3 -m 0 /dev/sda1    # makes an ext3 filesystem on sda1 with 0 reserved blocks
sudo tune2fs -i 1m /dev/sda1     # This is optional. fscks the partition once a month 
sudo mkfs.ext3 -m 0 /dev/sda2    # makes an ext3 filesystem on sda2 with 0 reserved blocks
sudo tune2fs -i 1m /dev/sda2     # This is optional. fsck the partition once a month
```

Since sda1 and sda2 are data partitions, there is no need for reserved blocks. Only operating systems need reserved blocks. 

fsck'ing is done to check the filesystem for errors. By default partitions are fscked every 22 mounts or so. If you reboot a lot this becomes rather too frequent I think. But this is a matter of personal taste. 

After running the commands above, please post the output of 
```

blkid 
```
one more time.
> 
probably one for another time, but i also did another backup using sbackup and now sda5 seems to be 80% used - should i worry?

I've seen two posts on the forums regarding machines becoming completely full due to sbackup making too many backups. 
There are probably many more who have encountered this. So be sure you know how often sbackup makes a full backup, where the backups are kept, and how you plan to get rid of old backups.
I believe the backups are kept in /var/backup.

PS. I'm not particularly enamored of sbackup. I think rsync is a better way to go in your situation.

---

### Post by capnthommo on 2008-12-08
hi unutbu, thanks, i shall get onto this as soon as i have dealt with the family (they will keep wanting attention - so tedious) and let you know the results.  i did wonder about the vista/winre in he text but wasnt sure.  this seems to fit with what i suspected.  thanks again, i hope this can take me forward.  i hink the sbackup copies are in /var and i am not sure how to get rid of old copies.  but that is a matter for another thread/day.
cheers - backlater
nigel

---

### Post by capnthommo on 2008-12-08
hi unutbu.  i entered the commands and it went through various processes.  blkid gets me the following

nigel@nigel-laptop:~$ blkid
/dev/sda1: UUID="E438053038050372" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="9EE40838E40814E5" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="DE040C06040BDFFF" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="8cd3e712-cd87-4d00-8ca3-691f3c3a5ad4" TYPE="ext3" 
/dev/sda6: UUID="55bd85f1-5b61-4c73-a979-cde9d2ce028d" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
nigel@nigel-laptop:~$ 

it still says "WinRE"  ntfs etc.  is this right or is there still something else to do?
cheers
nigel

---

### Post by unutbu on 2008-12-08
Okay, this might have to do with the system's cachefile (/etc/blkid.tab) not being updated yet. 

What is the output of 
```

sudo vol_id /dev/sda1
sudo vol_id /dev/sda2
```

---

### Post by capnthommo on 2008-12-08
okay here it is
nigel@nigel-laptop:~$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=813f96fb-dc06-4ad7-8de2-d21f289428ee
ID_FS_UUID_ENC=813f96fb-dc06-4ad7-8de2-d21f289428ee
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
nigel@nigel-laptop:~$ sudonvol_id /dev/sda2
bash: sudonvol_id: command not found
nigel@nigel-laptop:~$ sudo vol_id /dev/sda2
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=307461ee-720e-4db8-89a7-1cf51843d4a8
ID_FS_UUID_ENC=307461ee-720e-4db8-89a7-1cf51843d4a8
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
nigel@nigel-laptop:~$ 
 
thanks 
nigel

---

### Post by unutbu on 2008-12-08
```
gksu gedit /etc/fstab

```
Add these two lines to the bottom
```

UUID=307461ee-720e-4db8-89a7-1cf51843d4a8 /data ext3 relatime,errors=remount-ro 0 2
UUID=813f96fb-dc06-4ad7-8de2-d21f289428ee /backup ext3 relatime,errors=remount-ro 0 2
```

Save and exit gedit.

Now run
```

sudo mkdir /data
sudo mkdir /backup
sudo mount -a
```

You should now see your partitions mounted at /data and /backup.
Now we copy your entire home directory onto /data:
```

sudo rsync -a /home/nigel/ /data/nigel
```

Use nautilus to check out /data/nigel. Try to make sure that it is a faithful copy of your /home/nigel directory, because next we are going to delete /home/nigel:
```

sudo rm -rf /home/nigel
```

Now we make a symlink, to "hook up" your home directory to /data/nigel
```

sudo ln -s /data/nigel /home/nigel
```

And finally, to backup your new home directory to /backup:
```

sudo rsync -a --delete /data/nigel/ /backup/nigel
```

The --delete flag means that if there is a file in /backup/nigel that is not in /data/nigel, then it should be deleted.
This is a useful option when doing backups since you don't want old files (that you've deleted from /data/nigel) lying around.

Once a week, or whenever the feeling moves you, you can run the rsync command again to backup your data. If you want it automated so it will run say, once a week, we can give you instructions on how to set that up too.

Okay, let us know how it goes.

---

### Post by capnthommo on 2008-12-08
okay. i did what you said, copied and pasted in fstab, saved and quit and got as follows

nigel@nigel-laptop:~$ gksu gedit /etc/fstab
nigel@nigel-laptop:~$ sudo mount -a
mount: mount point /data does not exist
mount: mount point /backup does not exist
nigel@nigel-laptop:~$ 

cheers
nigel

---

### Post by unutbu on 2008-12-08
Bah. My mistake.
```

sudo mkdir /data
sudo mkdir /backup
```

(I'm editing my previous post in case anyone else tries those instructions...)

---

### Post by capnthommo on 2008-12-08
okay, i have tried that but cant see data or backup on 'places' but present on system monitor so went ahead. this what i got
nigel@nigel-laptop:~$ sudo mount -a
mount: mount point /data does not exist
mount: mount point /backup does not exist
nigel@nigel-laptop:~$ sudo mkdir /data
nigel@nigel-laptop:~$ sudo mkdir/backup
sudo: mkdir/backup: command not found
nigel@nigel-laptop:~$ sudo mkdir /backup
nigel@nigel-laptop:~$ sudo mount -a
nigel@nigel-laptop:~$ gksu gedit /etc/fstab
nigel@nigel-laptop:~$ sudo rsync -a home/nigel /data/nigel
rsync: change_dir "/home/nigel/home" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ sudo rsync -a /home/nigel/ /data/nigel
rsync: readlink "/home/nigel/.gvfs" failed: Permission denied (13)

what now?

---

### Post by capnthommo on 2008-12-08
ok i tried once more just to ensure i didnt mistype anything and what i got was pretty much the same result.
nigel@nigel-laptop:~$ gksu gedit /etc/fstab
nigel@nigel-laptop:~$ sudo mkdir /data
mkdir: cannot create directory `/data': File exists
nigel@nigel-laptop:~$ sudo mkdir /backup
mkdir: cannot create directory `/backup': File exists
nigel@nigel-laptop:~$ sudo mount -a
nigel@nigel-laptop:~$ sudo rsync -a /home/nigel/ /data/nigel
rsync: readlink "/home/nigel/.gvfs" failed: Permission denied (13)
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ 
notice it seems to think the /data and /backup files exist, and when i enter "sudo mount -a" it seems to have done it (at least it gives me a $prompt anyway) but there doesnt seem to be any evidence of either on the desktop or places menu although when i open the 'system monitor' app there they are - taunting me with their 90GB of space.  and when i enter the 'rsync' command it all kinda falls apart.  do i need to do something simple like reboot ?
cheers
nigel

---

### Post by unutbu on 2008-12-08
Okay, let's do a sanity check.
Reboot the machine.
Then open a terminal and type
```
gksu nautilus
```
This will give you a file browser with root privileges. 
Navigate to /data and look inside. Is there a directory called nigel there?

Furthermore, try copying a file into /data. Does that work?

Please report back what you see.

---

### Post by capnthommo on 2008-12-09
hi,  this is what i got from gksu nautilus

nigel@nigel-laptop:~$ gksu nautilus
Initializing nautilus-share extension

** (nautilus:6808): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

it did actually open a file - root browser and this is what was displayed

the 'address' bar showed buttons for 'root' and 'desktop' and indicated that 'root' was selected - in the large window only an icon for desktop and  gparted+details.htm were displayed.
in the left hand window headed places it showed root, desktop, file system, network, cdrom0, deleted items, with root hilighted. 
when i select desktop from the list it shows the right hand window as empty.

file system shows a whole range from backup (folder) through to file vmlinuz.old including data, bin, boot, var, home, 25 folders in all, what looks like an archive folder and 3 (archive?) files.
when i select the folder 'data' from this window it displays two more folders 'lost and found' (empty)  and nigel containing desktop, documents, examples, flash player 10, music, photos, pictures, public. templates, videos.  any of these that are supposed to contain data (eg photos) appear to be ok - they have the photos in them and will display.

this seems a bit like the places menu on the desktop from which i used to be able to access folders etc but which now seems to have empty places and to have lost pats of the system eg media and media1.
my data seems to still be here and accessible but the system around it has changed.
thanks for your patience, this one has become much more complicated than i expected.  
nigel

---

### Post by unutbu on 2008-12-09
There seem to be some configuration issues on your machine:
[list]
[*]```
** (nautilus:680: WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
```

[*]> lost pats of the system eg media and media1.
[/list]

The first one has to do with sharing files with windows through Samba. Do you share files with a networked windows machine? If so, you might find out how to fix the problem here: [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide). Unfortunately, that's all I know about Samba.

The second problem seems relevant to the changes we've been making. What are media and media1? I know your sda1, sda2 partitions were mounted at /media/disk and /media/disk-1. Is this the media you refered to? But then what is media1?

How about we try this:
Open a terminal and type:
```

sudo mv /home/nigel /home/nigel_old
```

This renames your nigel directory as nigel_old. 
```

sudo ln -s /data/nigel /home/nigel
```

This creates a symlink from /home/nigel to /data/nigel.
When you access files in /home/nigel, the computer will automatically look in /data/nigel for the files. It sounds from what you've written that all the files were successfully copied except for .gvfs. I believe this is a special directory that GNOME creates when you log in. So I think it is okay that it did not get copied. 

Now reboot. Check out your home directory. Does everything look okay?
Your old home is still safe at /home/nigel_old if there is any problem, so we can revert if necessary.

If when you boot up there is any complaint about you being homeless, take notes on everything you see and do. Then to revert you simply reboot, select "Recovery Mode" or "Single User" from your GRUB menu. This will give you a root command line. Here you simply type 

```
rm /home/nigel                    # this deletes the symlink to /data/nigel
mv /home/nigel_old /home/nigel    # This restores your old home dir.
```

Then reboot, and please post your notes so we can hopefully fix the problem. I don't think you should have any problems, but I'm including this just in case.

---

### Post by capnthommo on 2008-12-09
hi there, when i typed the mv command this is what i got
igel@nigel-laptop:~$ sudo mv /home/nigel /home/nigel
[sudo] password for nigel: 
mv: cannot move `/home/nigel' to a subdirectory of itself, `/home/nigel/nigel'
nigel@nigel-laptop:~$ 
it didnt do anything did it?
nigel

---

### Post by capnthommo on 2008-12-09
sorry, not alert yet.  i typed a wrong command.  this is what i get when i do it right

nigel@nigel-laptop:~$ sudo mv /home/nigel /home/nigel_old
nigel@nigel-laptop:~$ 
it didnt ask for a password, is that right?

---

### Post by unutbu on 2008-12-09
Some of these commands (like rsync) are very particular. It could be a bit dangerous if you make typing errors. Perhaps use copy and paste.
```
sudo mv /home/nigel /home/nigel_old
```

Edit: Oops, I didn't see your second post. Yes, that's right.
And sudo only asks for your password the first time. Then you've got 15 minutes when sudo will not ask for your password again.

---

### Post by capnthommo on 2008-12-09
hi again, i rebooted and got the following
after username password i got
"your home directory listed as '/home/nigel' but does not appear to exist. do you want to log in with the /(root) directory.  it is unlikely anything will work unless you use a failsafe session"
ENTER
"$HOME/.dmre file being ignored. prevents default session and language being....(cant read my writing here.... file should be owned by user and have 644 permissions.  £HOME directory must be owned by user and not writable by others."
ENTER
could not update ICEauthority file /.ICEauthority
CLOSE
there is a problem with configuration server
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256
CLOSE

"cannot create dir "/home/nigel/.gnome2/share/fonts
needed to allow changes to mouse pointer theme"

"error startup screensaver. failed to change directory "/home/nigel" no such file or directory
now it went to wallpaper and nothing else
it is here that i rebooted and selected recovery mode and after many screens of data got the following
recovery menu
resume
clean
dpkg
fsck
root
xfix

ok        cancel
that is where i am now and not sure where to go from here.
whatever is causing this it is pretty certain to be some chanfge i have made in the last 4/5 days whilst trying to get my head round backing up and restoring.  if necessary i can do a comp[lete re install and re add the applications i have added.  no problem with any data files as i have them all on dvd or in other places.  it would just be a matter of loading eg Gnucash and re install/configure Wine to suit. so if that is an easier way to go i dont mind doing that.  i still have the original cd from which i installed in the first place.  would be nice to sort it from here though - it would be almost an admission of defeat otherwise.
thanks for all the help, you are being far more patient than i am sure i would be
cheers
nigel

---

### Post by unutbu on 2008-12-09
Hi capnthommo, thanks for your patience. As you pointed out, there are two options:

[list]
[*]Option 1: Reinstall Ubuntu. This has two advantages:
[list]
[*]In Step 4 ("Prepare partitions"), you can do a Manual install. Then, using the GUI, you can set sda2 to be /home, and sda5 to be / (where Ubuntu will be installed). By doing so, everything will be set up for you out-of-the-box. 
[*]Reinstallation takes 30 minutes -- definitely quicker than playing thread-post-tag.
[/list]
[*]Option 2: Forge ahead! :)
If you'd like to do so, I'll try my best to help you.
The first step would be to select "root" at that recovery menu. This will drop you to a root shell. Then type 

```
rm /home/nigel                    # this deletes the symlink to /data/nigel
mv /home/nigel_old /home/nigel    # This restores your old home dir.
init 2                            # This will get you back to the gdm login screen
```

Login, then type
```

ls -ld /data 
ls -ld /data/nigel 
cd /data/nigel
find . -maxdepth 1 -wholename "./.*" \( -type f -exec ls -l {} \; \) -o \( -type d -exec ls -ld {} \; \)
cd /home/nigel
find . -maxdepth 1 -wholename "./.*" \( -type f -exec ls -l {} \; \) -o \( -type d -exec ls -ld {} \; \)
```

Then please post the output.
The big "find" commands list all the so-called "dot-files" in your /home/nigel and /data/nigel directories. It will show us the ownership and permissions on the files.
[/list]

I'm happy with whichever option you choose. I'd just like to see you with a working system as quickly as possible.

---

### Post by capnthommo on 2008-12-09
hi again
what i get is as follows
rm /home/nigel
cannot remove /home/nigel no such file or directory

if i try the next command
mv /home/nigel_old /home/nigel
i get
bash: /home/nigel_old: is a directory

---

### Post by unutbu on 2008-12-09
Please post
```

ls -l /home
ls -l /data 

```

---

### Post by capnthommo on 2008-12-09
hi there - sorry, i jumped straight in last time.  i think a couple mopre tries at getting this one running would be good before i throw in the towel, so here we go
ls -l /home gets 
drwxr-xr-x 58 nigel nigel 4096 Dec 9 12:13 nigel_old
drwxr-xr-x 3 root root 4096 Dec 4 22:42 remastersys
drwx------ 3 root root 4096 Dec 3 01:33 tmp_nC10G
drwx------ 3 root root 4096 Dec 2 22:42 tmpqHTf-Z

and ls -l /data gets
total 20
drwx------ 2 root root 16384 Dec 8 21:30 lost+found
drwxr-xr-x 57 nigel nigel 4096 Dec 8 21:37 nigel

cheers
nigel

---

### Post by unutbu on 2008-12-09
While booted into Recovery Mode (and having selected "root" to get to a root shell prompt), type
```

ln -sf /data/nigel /home/nigel
ls -l /home

```
You should see something like this as output:
```

lrwxrwxrwx  1 root   root     14 2008-12-09 14:06 nigel -> /data/nigel/
```

If you don't see this, or get some error message, please post back with the output.

If you get the output above, then type

```
init 2
```

This should take to to the gdm login window. Try to login.

---

### Post by capnthommo on 2008-12-09
> **unutbu said:**
> While booted into Recovery Mode (and having selected "root" to get to a root shell prompt), type
```

ln -sf /data/nigel /home/nigel
ls -l /home

```
You should see something like this as output:
```

lrwxrwxrwx  1 root   root     14 2008-12-09 14:06 nigel -> /data/nigel/
```

If you don't see this, or get some error message, please post back with the output.

If you get the output above, then type

```
init 2
```

This should take to to the gdm login window. Try to login.
hi there, thanks, i tried that and got something similar to what i posted last time but the init 2 command took me to the logon screen and permitted me to logon.  it has given me internet access and a simple desktop.  i dont know however, if it will stay if i logoff so i will stay on afor the present. i shall now revert to working on the laptop as it is significantly quicker etc.  also it is the machine i am actually trying to use.  thanks for the help.  i shall be back shortly
nigel

---

### Post by capnthommo on 2008-12-09
okay, now i'm back on the laptop (my main machine and the one i use ubuntu on - the machine on which i currently have the problem i'm trying to fix)  now i can work considerably faster (the desktop just takes an age to do anything at all).  i have the desktop i had before.  the system monitor application from System>Administration still shows a total of about 147GB split between:
device  /dev/sda5   directory  /         type  ext3
device  /dev/sda1   directory  /backup   type  ext3
device  /dev/sda2   directory  /data     type  ext3
cheers
nigel

---

### Post by unutbu on 2008-12-09
> the init 2 command took me to the logon screen and permitted me to logon.

This sounds like great news. This means the machine was able to find /home/nigel.
Let's check: please post 
```

ls -l /home
```

Please show me the output of terminal commands -- as much as you can. It helps me understand the state of the computer.

---

### Post by capnthommo on 2008-12-09
hi, yes great news so far - though it seems a little wobbly (eg firefox just greyed out on me when i was doing the terminal thing but one step at a time hey?).  anyway, here is the result of the command
nigel@nigel-laptop:~$ ls -l /home
total 16
lrwxrwxrwx  1 root  root    11 2008-12-09 20:08 nigel -> /data/nigel
drwxr-xr-x 58 nigel nigel 4096 2008-12-09 12:13 nigel_old
drwxr-xr-x  3 root  root  4096 2008-12-04 22:42 remastersys
drwx------  3 root  root  4096 2008-12-03 01:33 tmp_nC10G
drwx------  3 root  root  4096 2008-12-02 22:42 tmpqHTf-Z
nigel@nigel-laptop:~$ 

cheers
nigel

---

### Post by unutbu on 2008-12-09
Okay, your machine put up a valiant fight, but I think we beat it. :)

You are now using /data/nigel for your home directory. So now you have about 50GB dedicated to your home directory. 

Type
```

sudo rsync -a --delete /data/nigel/ /backup/nigel
```

Make sure you type a forward-slash at the end of "/data/nigel/". With the forward-slash
rsync will copy /data/nigel to /backup/nigel. Without the slash, you get /backup/nigel/data/nigel. 

From now on, that's all you need to do to backup your home directory.
We can make that into a double-clickable launcher if you wish, or set it up to run in the background once a week if you wish. Let me know if either or both interest you.

I suggest you do not delete /home/nigel_old for a while. Use the laptop for at least a week. Try to make sure that there are no files missing from your new /home/nigel. Then, when you are comfortable, you can free space by deleting /home/nigel_old:
```

rm -rf /home/nigel_old
```

Use the terminal instead of Nautilus for this, so nothing ends up in the Trash directory.

---

### Post by capnthommo on 2008-12-09
okay, not entirely successful ithink, what happened was this.  i copy/pasted the command
nigel@nigel-laptop:~$ sudo rsync -a --delete /data/nigel/ /backup/nigel
[sudo] password for nigel: 
rsync: readlink "/data/nigel/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
sudo rsync -a --delete /data/nigel/ /backup/nigel
sudo rsync -a --delete /data/nigel/ /backup/nigelrsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ sudo rsync -a --delete /data/nigel/ /backup/nigel
rsync: readlink "/data/nigel/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ sudo rsync -a --delete /data/nigel/ /backup/nigel
rsync: readlink "/data/nigel/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ 

is it possible i entered a password error? i am pretty sure i didn't but would it be worth trying again?  also i am sorry if it has muddied things here but i tried a second time when it failed the first.  i am going to try typing manually just to be sure, ok?  i'll let you know the result
cheers
nigel

---

### Post by capnthommo on 2008-12-09
no, same result as before

nigel@nigel-laptop:~$ sudo rsync -a --delete /data/nigel/ /backup/nigel
rsync: readlink "/data/nigel/.gvfs" failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
nigel@nigel-laptop:~$ 

thanks
nigel

---

### Post by unutbu on 2008-12-09
That error might not be so bad. .gvfs is a special directory used for mounting virtual filesystems. It does not need to be backed up.

Type ```
ls -la /backup/nigel
```

This should list the files and directories in the top level of /backup/nigel. If you want to see all your files, you could type
```

ls -laR /backup/nigel | less
```
(Press 'q' to quit the pager, spacebar to page forward, 'b' to go back.)

If you see your files (besides .gvfs) then the rsync command succeeded.

---

### Post by capnthommo on 2008-12-09
okay, i composed a quick reply but i think i must have timed out.  anyway i now have access to 'home folder' in places without a non existent file error message - yes there is actually stuff there! i still cant see the /data and /backup on the 'places' list or desktop, but could that be that they are now 'part of' / and so integral anyway?  i am just about to try a reboot to see if i logon ok, and will get back with the result.  tonight if successful or tomorrow if not.
just to say thanks more than you know.  i had no idea where to go with this one.  i shall get in touch about the options on backing up etc that you suggested another time.
and thanks yet again - wish me luck.
nigel

---

### Post by capnthommo on 2008-12-09
okay then unutbu.  i'm back.  so i think you can chalk this one up as a success.  
as you advised, we will see how it performs over the next week or so. 
just out of interest, two folders have appeared on my desktop since the repair - entitled 'untitled folder' and 'untitled folder 2' - do you have any idea what these are?
thanks, i'm up and running, i shall get rid of the sbackup applications forthwith, and see if i cant find out how to get rid of any backups they have left and try to clear out any data from abortive attempts over the past few days.  this all came about due to my concerns over the disk filling up with 'stuff' at a phenomenal rate every time i tried to backup.  in future i shall keep a dvd and do some more research on backing up - i noted what you suggested earlier.
anyhow
thank you very much for the help, you have stuck with this one long after i would have given up with a shrug of the shoulders.
thanks so much
nigel:p

---

### Post by unutbu on 2008-12-09
I'm glad it worked out. Enjoy Ubuntu.

---

