---
title: "Can't boot up without a boot disk."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by dumonttim on 2008-12-18
This morning I installed Ubuntu (on the recommendation of a friend) and everything worked fine at first.  I was running Windows Vista.  So I got it installed and rebooted from Vista into Ubuntu.  Things were running great until I tried to reboot again.  I get a plain black screen with a blinking cursor.  I can't do anything from there except try to reboot again.  I'm currently running off of an Ubuntu boot disk just so that I can get online to type this.  How can I get Ubuntu off of my computer so that I can just get back to windows and start over fresh?  Any help would be GREATLY appreciated.

---

### Post by taurus on 2008-12-18
How did you install Ubuntu?  Did you have a separate partition for Ubuntu or did you install it from windows?

From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by dumonttim on 2008-12-18
I have no idea what any of this means... but if it can help you to help me I will love you forever. Haha

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef34d5e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18797   150986871   27  Unknown
/dev/sda2           18798       19457     5301450    5  Extended
/dev/sda5           18798       19457     5301418+  82  Linux swap / Solaris

---

### Post by taurus on 2008-12-18
> **dumonttim said:**
> This morning I installed Ubuntu (on the recommendation of a friend) and everything worked fine at first.  I was running Windows Vista.  So I got it installed and **_rebooted from Vista into Ubuntu_**.  Things were running great until I tried to reboot again.  I get a plain black screen with a blinking cursor.  I can't do anything from there except try to reboot again.  I'm currently running off of an Ubuntu boot disk just so that I can get online to type this.  How can I get Ubuntu off of my computer so that I can just get back to windows and start over fresh?  Any help would be GREATLY appreciated.

Sounds to me like wubi!

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by dumonttim on 2008-12-18
I think that is what I installed.  But I can't get back into Windows to uninstall it.  If I have managed to "break" my computer I'm going to have hell to pay.  I go to school online any my wife uses the computer for her school work (she is a teacher) a lot.  How can I get back to booting up without the boot CD?

---

### Post by appi2012 on 2008-12-18
Can you post what is in the boot.ini file on your windows partition? (C://boot.ini)?

---

### Post by unutbu on 2008-12-18
dumonttim, I think what appi2012 means is for you to open a terminal and type
```

sudo mount /dev/sda1 /mnt
cat /mnt/boot.ini
```

---

### Post by dumonttim on 2008-12-18
I have no clue how to run this operating system.  I'm a complete noob when it comes to things other than windows.  How would i check what is in the boot.ini file on my windows partition?  How do I find my windows partition... or get to it... or whatever?

---

### Post by appi2012 on 2008-12-18
Click on Places on the top menu bar. There should be some thing that has an icon looking like a hard drive. Click on that to open your windows files. boot.ini should be right there.

---

### Post by dumonttim on 2008-12-18
when I go to the hard drive it shows absolutely no files.  Please tell me I haven't reformated my hard drive somehow.

---

### Post by dumonttim on 2008-12-18
I have no idea what you want me to do.  I copied and pasted that code into the terminal and this is what I got...

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ cat /mnt/boot.ini

---

### Post by kansasnoob on 2008-12-18
I'm curious, did the install procedure look like this:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

or this:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

I don't want to see you manipulate the drive too much until we know for sure! It sounds like you have data you'll want to recover if bad goes to worse!

---

### Post by appi2012 on 2008-12-18
what does typing this return:
```
ls /media/
```

---

### Post by dumonttim on 2008-12-18
To kansasnoob:

It looked like the first one.  It was a nice graphical interface right in windows.

To appi2012:

ubuntu@ubuntu:~$ ls /media/
disk

---

### Post by appi2012 on 2008-12-18
okay

now type:
```
ls /media/disk/
```

---

### Post by kansasnoob on 2008-12-18
> **dumonttim said:**
> To kansasnoob:

It looked like the first one.  It was a nice graphical interface right in windows.

To appi2012:

ubuntu@ubuntu:~$ ls /media/
disk

OK, I called in some help. It's caljohnsmith, if he's available!

I just don't want you to do anything radical!

Hang on.

---

### Post by dumonttim on 2008-12-18
Hey appi,

Nothing happens when I type that.

---

### Post by cariboo on 2008-12-18
It looks like you wiped out your windows partition and didn't format any of the partitions. I would suggest you get out your Windows install disk and reinstall windows, before you do anything else.

Jim

---

### Post by kansasnoob on 2008-12-18
BTW, there is a separate Wubi section:

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

But honestly lets see if caljohnsmith is available.

If not I'll message meierfra.

---

### Post by kansasnoob on 2008-12-18
> **cariboo907 said:**
> It looks like you wiped out your windows partition and didn't format any of the partitions. I would suggest you get out your Windows install disk and reinstall windows, before you do anything else.

Jim

NOOOOOOOOOOOOOOO!

At the absolute worst the op can recover some (if not all) of the Windows files!

---

### Post by appi2012 on 2008-12-18
I'm sorry to say, but that most likely means your windows partition is empty... :-({|=

---

### Post by dumonttim on 2008-12-18
So i seriously wiped my hard drive?  You've got to be kidding...  This is REALLY bad.

---

### Post by kansasnoob on 2008-12-18
My guess is that Vista is now "unrecognizable" but still there in tact and can be recovered completely!

If I googled for hours I could probably figure it out but both meierfra and caljohnsmith know this stuff inside out!

---

### Post by kansasnoob on 2008-12-18
> **dumonttim said:**
> So i seriously wiped my hard drive?  You've got to be kidding...  This is REALLY bad.

I doubt it! I'll also message meierfra!

---

### Post by unutbu on 2008-12-18
dumonttim, at this point, given the evidence we've seen, I think there is a very good chance that your files are intact.

Your partition table may be a little screwy, but testdisk should be able to fix that. Your MBR almost certainly needs fixing too. Unfortunately, I don't know much about fixing Windows boot problems. Let's see what caljohnsmith or meierfra says.

In the mean time, would you please try the following?

Open a terminal (Applications>Accessories>Terminal) and type
```

mount
ls -l /media/disk
cat /media/disk/boot.ini
```
Post the output.

---

### Post by dumonttim on 2008-12-18
how can i contact these guys?

---

### Post by dumonttim on 2008-12-18
Unutbu:  Here is the result

ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /mnt type vfat (rw)
ubuntu@ubuntu:~$ ls -l /media/disk
total 0
ubuntu@ubuntu:~$ cat /media/disk/boot.ini

---

### Post by kansasnoob on 2008-12-18
> **unutbu said:**
> dumonttim, at this point, given the evidence we've seen, I think there is a very good chance that your files are intact.

Your partition table may be a little screwy, but testdisk should be able to fix that. Your MBR almost certainly needs fixing too. Unfortunately, I don't know much about fixing Windows boot problems. Let's see what caljohnsmith says.

In the mean time, would you please try the following?

Open a terminal (Applications>Accessories>Terminal) and type
```

mount
ls -l /media/disk
cat /media/disk/boot.ini
```
Post the output.

Agreed! Chill for a few moments!

Unutbu may know this as well as either caljohnsmith or meierfra, I don't know. Just don't panic and make things worse!

---

### Post by kansasnoob on 2008-12-18
> **dumonttim said:**
> how can i contact these guys?

I already did!

Unutbu may also be able to get you through this.

I'm just familiar with the aforementioned folks and there outcomes! 99.9% positive! Unutbu has to be doing something right based on the number of times he's been thanked!

Just DO NOT reformat or anything that extreme!

---

### Post by dumonttim on 2008-12-18
I'm not going to reformat.  I am waiting on more info before that.  I'm a noob to ubuntu but I'm not a noob to computers.  My father has rescued corupted files from hard drives before.  I'd probably be able to get something off of my hard drive even under the worst of circumstances.  But I do need to get this taken care of as quickly as I can.  I also want to formally thank you all for you quick, considerate, and easy to understand replies.

---

### Post by kansasnoob on 2008-12-18
> **dumonttim said:**
> I'm not going to reformat.  I am waiting on more info before that.  I'm a noob to ubuntu but I'm not a noob to computers.  My father has rescued corupted files from hard drives before.  I'd probably be able to get something off of my hard drive even under the worst of circumstances.  But I do need to get this taken care of as quickly as I can.  I also want to formally thank you all for you quick, considerate, and easy to understand replies.

Good! Hopefully one of these folks will be available. In the meanwhile I'm googling so please be patient.

---

### Post by unutbu on 2008-12-18
The following instructions on using testdisk should have no harmful side-effects, and it may help us understand what to do next: 

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6284607&postcount=3](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6284607&postcount=3)

---

### Post by kansasnoob on 2008-12-18
Do you have your Vista install discs? Just curious. For instance I've found this to be helpful:

[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

Just don't jump at this point and do anything. Let's give meierfra and caljohnsmith a chance if they're available.

I also found this in the Wubi guide:

> How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

but it would only help you with Ubuntu (kind of). It might or might not get Vista booted, but I suggest waiting for a bit to see if the pros have some better answers.

At this point everything we try and fail at is liable to make things worse!

---

### Post by kansasnoob on 2008-12-18
I'm going to try something just out of curiosity (I don't care if I break my machine) but it'll take a while.

Hopefully by then someone else will have this solved.

---

### Post by dumonttim on 2008-12-18
Would it be worth it for me to download the program "PhotoRec", hook up an external hard drive, recover the files, and re-install Vista?  (Don't worry, I'm not going to do this unless it seems like a unanimous approval from you guys the "ubuntu brain trust".)

---

### Post by kansasnoob on 2008-12-18
I still hope we can get the real pros involved here but just to see how it worked I did this:

[http://www.zimbio.com/Ubuntu+Linux/articles/296/Use+Ubuntu+Live+CD+Backup+Files+Dead+Windows](http://www.zimbio.com/Ubuntu+Linux/articles/296/Use+Ubuntu+Live+CD+Backup+Files+Dead+Windows)

Same here:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

And if that fails there is:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

But I doubt it comes down to that! I think you can fix the Vista boot! I'm just not sure how1

---

### Post by kansasnoob on 2008-12-18
> **dumonttim said:**
> Would it be worth it for me to download the program "PhotoRec", hook up an external hard drive, recover the files, and re-install Vista?  (Don't worry, I'm not going to do this unless it seems like a unanimous approval from you guys the "ubuntu brain trust".)

I'd really like to see what either caljohnsmith or meierfra have to say first!

---

### Post by meierfra. on 2008-12-18
Your windows partition has the wrong type and does not have a  boot flag. So lets fix that:

```
sudo sfdisk -c /dev/sda 1 7

sudo sfdisk -A1 /dev/sda
```
 

I doubt that this will be enough to let you boot into Vista, but give it a try.

If it did not work,  follow  unutbu's  advice  from post 32 and post the results from testdisk.

---

### Post by kansasnoob on 2008-12-18
> **meierfra. said:**
> Your windows partition has the wrong type and does not have a  boot flag. So lets fix that:

```
sudo sfdisk -c /dev/sda 1 7

sudo sfdisk -A1 /dev/sda
```
 

I doubt that this will be enough to let you boot into Vista, but give it a try.

If it did not work,  follow  unutbu's  advice  from post 32 and post the results from testdisk.

Thanks for popping in old friend!

I'm sure where this was a Wubi install that all is not lost!

I'll butt out and let you do the awesomeness you do!

Many, many thanks!

---

### Post by kansasnoob on 2008-12-18
Wow, I guess that either worked or the op's wife killed him, eh?

---

### Post by dumonttim on 2008-12-18
Wife didn't kill me... but almost.  And no I haven't gotten it working yet.  I need to try that test program still.  I'll have more time tomorrow to work on it.  I'll keep everyone posted.

---

### Post by kansasnoob on 2008-12-18
Well, what I find sad and maddening about this is that the more often I call on folks to help with a problem and things don't fall in place I end up being the "little boy that cried wolf"!

So maybe I won't cry "wolf" anymore!

I'll just let people reformat and lose their stuff!

Good luck!

---

### Post by dumonttim on 2008-12-19
Kk... I'm going to run test disk right now... but first here are the results to the command you asked me to run.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef34d5e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18797   150986871   27  Unknown
/dev/sda2           18798       19457     5301450    5  Extended
/dev/sda5           18798       19457     5301418+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA Hitachi HTS54251 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  155GB  155GB   primary   fat32        boot 
 2      155GB   160GB  5429MB  extended                    
 5      155GB   160GB  5429MB  logical   linux-swap      


I'm about to run testdisk now.  Lets see how that goes.  Thanks again to everyone for all their help.

---

### Post by dumonttim on 2008-12-19
So far here is what I have to post:

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Sys=27                   0   1  1 18796 254 63  301973742
 2 E extended             18797   0  1 19456 254 63   10602900
 5 L Linux Swap           18797   1  1 19456 254 63   10602837

Here are the deep search results:

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0   1  1  1019 254 58   16386232 [NO NAME]
D FAT32 LBA                0  32 33  1274 241 55   20480000 [PQSERVICE]
D HPFS - NTFS           1020   0  1 11175 254 63  163156140
D HPFS - NTFS           1274 241 56 10366 150 24  146057216 [ACER]
D HPFS - NTFS          10366 150 25 19457  21 20  146038784 [DATA]
D FAT32 LBA            11176   0  1 19456 254 30  133034232 [DOS]
D Linux Swap           18797   1  1 19456 254 42   10602816






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 8389 MB / 8001 MiB


Hope this helps you help me.  LoL.  Thanks again.

---

### Post by caljohnsmith on 2008-12-19
> **dumonttim said:**
> 
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0   1  1  1019 254 58   16386232 [NO NAME]
D FAT32 LBA                0  32 33  1274 241 55   20480000 [PQSERVICE]
D HPFS - NTFS           1020   0  1 11175 254 63  163156140
D HPFS - NTFS           1274 241 56 10366 150 24  146057216 [ACER]
D HPFS - NTFS          10366 150 25 19457  21 20  146038784 [DATA]
D FAT32 LBA            11176   0  1 19456 254 30  133034232 [DOS]
D Linux Swap           18797   1  1 19456 254 42   10602816
```

Dumonttim, how about using the up/down arrow keys to select each of the FAT and NTFS partitions above, and press "p" to get a directory listing. It looks like the ones marked "ACER" and "DATA" are your most promising as far as getting your Windows back. I hope you are running testdisk version 6.9 or 6.10, because previous versions usually crash when you try to list the directories in an NTFS partition. Let us know which of those FAT/NTFS partitions above give a directory listing and we can all work from there.

---

### Post by dumonttim on 2008-12-19
Hey.  Under the ACER partition I can see all my files!  Yay, they still exist!  My wife is very happy too lol.  So where do I go from here?

P.S.  I am running version 6.9 of testdisk

---

### Post by caljohnsmith on 2008-12-19
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]D[/COLOR] FAT32                    0   1  1  1019 254 58   16386232 [NO NAME]
[COLOR="Red"]P[/COLOR] FAT32 LBA                0  32 33  1274 241 55   20480000 [PQSERVICE]
[COLOR="Red"]D[/COLOR] HPFS - NTFS           1020   0  1 11175 254 63  163156140
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1274 241 56 10366 150 24  146057216 [ACER]
[COLOR="Red"]P[/COLOR] HPFS - NTFS          10366 150 25 19457  21 20  146038784 [DATA]
[COLOR="Red"]D[/COLOR] FAT32 LBA            11176   0  1 19456 254 30  133034232 [DOS]
[COLOR="Red"]D[/COLOR] Linux Swap           18797   1  1 19456 254 42   10602816
```
OK, that's great news, hopefully once you recover the partition with testdisk most of your data will be intact. :) Go ahead and select each partition again, but this time move the right/left arrow keys to change the partition markings as I've shown above highlighted in red. Once you are sure all the partitions are marked exactly as shown above, press enter to get to the next screen, and then select the option to write the new partition table. It would be a good idea to reboot, and then post the new output of:
```
sudo sfdisk -luS
sudo parted /dev/sda print
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
And we can work from there. :)

---

### Post by dumonttim on 2008-12-19
You fixed it!!!!!!! I'm typing this in windows right now and my wife is VERY excited.  Thank you SO much!

Do you still want me to go back into ubuntu to post that data, or is there no reason now?

---

### Post by caljohnsmith on 2008-12-19
That's great news, I'm so glad to hear that everything in Windows seems to be intact. As long as it's working OK, there's no reason to post the output of those commands. Hopefully your marital harmony is now also restored to its fullest. Cheers, and we hope you don't have any other bad experiences like this with Ubuntu again. :)

---

### Post by dumonttim on 2008-12-19
I really can't thank you guys enough.  You aren't getting paid, and yet you've been more helpful than ANY tech support I've ever worked with.  Three Cheers for Ubuntu users!  Huzzah! Huzzah! Huzzah!

If I ever want to play with Ubuntu again i'll make sure to just use the disk and run it off of there.  None of this installing it stuff lol.  Thanks again!

Tim DuMont

---

