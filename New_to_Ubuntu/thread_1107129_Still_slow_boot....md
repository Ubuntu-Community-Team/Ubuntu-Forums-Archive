---
title: "Still slow boot..."
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Teatro on 2009-03-26
I have recently installed Intrepid Ibex on an AMD 64 system, dual boot with Windows XP. Everything is fine except that the ubuntu boot is agonizingly slow. I don't know how to interpret the boot log, but as near as I can tell the system is testing a bunch of addresses to see if drives are attached, and waiting for them to time out before testing another one.  Does anyone know how I can either fix this or record the boot log so I can post it? 

The general appearances of the slow boot messages is:
[  868069] ata1.00 status { DRDY }

or 
[   868069] res 40/00:00:00:00/00:00:00 Emask 0X4 (timeout)

---

### Post by jakupl on 2009-03-26
install bootchart

```
sudo apt-get install bootchart
```

bootchart will put a chart showing your boot sequence in /var/log/bootchart
reboot your computer and try attaching it here.

---

### Post by Teatro on 2009-03-26
> **jakupl said:**
> install bootchart

```
sudo apt-get install bootchart
```

Thanks, I'll try that! (I take it that this is a tool for logging the bootscreen- any clue as to how to solve the actual problem?)

---

### Post by cariboo on 2009-03-26
The messages indicates a hard drive problem may be in the making. I would suggest you boot from the LiveCD and run fsck manually on the drive. Once you have booted to the desktop open an Application-->Accessories-->Terminal and type:

```
sudo fsck /dev/sda2
```

the above command assumes you have Ubuntu installed on the second partition of your first hard drive.

Jim

---

### Post by Teatro on 2009-03-26
> **cariboo907 said:**
> The messages indicates a hard drive problem may be in the making. I would suggest you boot from the LiveCD and run fsck manually on the drive. Once you have booted to the desktop open an Application-->Accessories-->Terminal and type:

```
sudo fsck /dev/sda2
```

the above command assumes you have Ubuntu installed on the second partition of your first hard drive.

Jim

Thanks, Jim. The drive is band new, and windows handles it fine-  oddly enough, windows has never booted faster. I think ubuntu is in the third partition, since the Windows system has a recovery partition. What does fsck do?

---

### Post by aeiah on 2009-03-26
```
man fsck
```

yields:

> fsck is used to check and optionally repair one or more Linux file sys&#8208;tems.   filesys  can  be  a device name (e.g.  /dev/hdc1, /dev/sdb2), a mount point (e.g.  /, /usr, /home), or an ext2 label or UUID  specifier (e.g.   UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).  Normally, the fsck program will try to  handle  filesystems  on  different physical disk  drives  in  parallel to reduce the total amount of time needed to check all of the filesystems.

---

### Post by Teatro on 2009-03-26
> **aeiah said:**
> ```
man fsck
```

yields:

Thanks,aeiah. I'm not sure what all that means, but I'll give it a try.

---

### Post by Teatro on 2009-03-26
--desktop:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:00/01
1) Copy original to backup
2) Copy backup to original
3) No action

I tried fsck. It decided sda3 was zero length, didn't have anything to say about sda2, and gave the above response for sda1, but sda1 may be a windows partition. How can I tell?

---

### Post by philinux on 2009-03-26
```
sudo fdisk -l
```

will give the info

---

### Post by Teatro on 2009-03-26
> **cariboo907 said:**
> The messages indicates a hard drive problem may be in the making. I would suggest you boot from the LiveCD and run fsck manually on the drive. Once you have booted to the desktop open an Application-->Accessories-->Terminal and type:

```
sudo fsck /dev/sda2
```

the above command assumes you have Ubuntu installed on the second partition of your first hard drive.

Jim

Okay, I just looked at the 'malacious commands' thread and see this:

Block device manipulation: Causes raw data to be written to a block device. Often times this will clobber the filesystem and cause total loss of data:
Code:

any_command > /dev/sda
dd if=something of=/dev/sda



Should I be concerned about Jim?

---

### Post by philinux on 2009-03-26
No!!

sudo fdisk -l

if you want to sort your system out.

---

### Post by Teatro on 2009-03-26
fdisk -l yields :

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         859     6494008+   b  W95 FAT32
/dev/sda2   *         860       28683   210349440    7  HPFS/NTFS
/dev/sda3           28684       41345    95724720    5  Extended
/dev/sda5           28684       40824    91785928+  83  Linux
/dev/sda6           40825       41345     3938728+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


Does this get me any closer to a faster boot up?

---

### Post by philinux on 2009-03-26
> **Teatro said:**
> fdisk -l yields :

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         859     6494008+   b  W95 FAT32
/dev/sda2   *         860       28683   210349440    7  HPFS/NTFS
/dev/sda3           28684       41345    95724720    5  Extended
/dev/sda5           28684       40824    91785928+  83  Linux
/dev/sda6           40825       41345     3938728+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


Does this get me any closer to a faster boot up?

Well as jim said. Boot the **live cd** the run the command 
```
sudo fsck /dev/sda5
```
Which is your linux install.

---

### Post by Teatro on 2009-03-26
> **philinux said:**
> Well as jim said. Boot the **live cd** the run the command 
```
sudo fsck /dev/sda5
```
Which is your linux install.

So, I'm reinstalling linux? Will I then need to replace any packages I've added?

---

### Post by Teatro on 2009-03-26
Oh, and sorry if I'm being paranoid about Jim... but hey, I've been running Windows! I've learned to be paranoid.

---

### Post by philinux on 2009-03-26
> **Teatro said:**
> Oh, and sorry if I'm being paranoid about Jim... but hey, I've been running Windows! I've learned to be paranoid.

fsck checks the file system etc, think chkdsk. Not a reinstall. It must be done from live cd.

---

### Post by Teatro on 2009-03-26
Thank you- soon as I finish the stuff I'm working on I'll try it. I appreciate the explanation.

---

### Post by Teatro on 2009-03-27
okay, I did the sudo fsck /dev/sda5 from the live disk, and I got back:

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks


what does this tell me?


(I have know idea why smileys show up in the post, in the editor it's just the date, last year)

---

### Post by Teatro on 2009-03-28
Babump-  advice?

---

### Post by Teatro on 2009-03-29
Anyone?

---

### Post by philinux on 2009-03-29
Do what post 2# says. Then reboot.

It puts a file in /var/log/bootchart.

Post the file here.

---

### Post by Teatro on 2009-03-29
Okay... 
it looks like some kind of graphic file- certainly not a text file. Not sure how to post it here, but I'm attaching it. I think...

---

### Post by Teatro on 2009-03-29
Okay, apparently that didn't work. Think I got it this time...

---

### Post by Teatro on 2009-03-30
Phil? Are you there Phil?

---

### Post by jakupl on 2009-03-30
> **Teatro said:**
> okay, I did the sudo fsck /dev/sda5 from the live disk, and I got back:

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks


what does this tell me?


(I have know idea why smileys show up in the post, in the editor it's just the date, last year)

because you need to put it in **[c**ode][/code] braquets. Like this:


**[c**ode]
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks[/code]

And it will show up like this

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks
```

---

### Post by Teatro on 2009-03-30
> **jakupl said:**
> because you need to put it in **[c**ode][/code] braquets. Like this:


**[c**ode]
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks[/code]

And it will show up like this

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 129283/5742592 files, 1156934/22946482 blocks
```


Thanks for the tip, jakupl. Don't suppose you can tell me how to speed up my boot sequence? Did I at least post the right bootchart?

---

### Post by jakupl on 2009-03-30
> **Teatro said:**
> Thanks for the tip, jakupl. Don't suppose you can tell me how to speed up my boot sequence? Did I at least post the right bootchart?

Yes that was a bootchart. I don't know if it is your last bootchart (you can tell from the date. the bootcharts are named after the date and number of boot on that date)

You can try one thing that certainly won't work ;) just an idea. I will explain the commands to you so that you know that the commands are not malicious :)

first do
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

*sudo* means "super user do" so you are super user right now. (this is dangerous so always check and double check commands with sudo)

*cp* means "copy"

*/boot/grub/menu.lst* is the file that you will copy
[I]
/boot/grub/menu.lst.backup[/I] Is the name of the copy.

so this command will do a backup of the menu.lst file. just in case something horrible happens (it won't, but it is good practice to always do a backup of these important system files before messing with them).

Now do:
```

gksudo gedit /boot/grub/menu.lst
```

*gksudo* is the same as sudo, but it works better with graphical applications. 

*gedit* is the program you want to open the file with (a text editor)
[I]
/boot/grub/menu.lst[/I] is the file you will open with the text editor.


Now near the bottom of the text file, you will find something like this;

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a2ff8373-0811-4fb1-b701-ddd2e2659356 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

this is the important line line:
```
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a2ff8373-0811-4fb1-b701-ddd2e2659356 ro quiet splash
```

Now delete the "ro quiet splash" so that it looks like this:

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a2ff8373-0811-4fb1-b701-ddd2e2659356
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

Save it and reboot.

when you delete this, the fancy splash screen will not appear when you boot up ubuntu, and you will see command line stuff instead. Don't worry. that's what this line does. If it makes no difference and the boot is not faster, you can restore your previous settings by doing:
```

sudo rm /boot/grub/menu.lst && sudo mv /boot/grub/menu.lst.backup /boot/grub/menu.lst
```

*rm* means "remove". (WARNING, always be extremely careful when doing sudo and rm together. this can absolutely kill your system if not done correctly).

*/boot/grub/menu.lst* Is the file that you will remove

*&&* means "and". so basically if the first command is done without problems, then the next command is to be executed.

*mv* means "move"
[I]
/boot/grub/menu.lst.backup[/I] is the file that we will move

*/boot/grub/menu.lst* is the new location of that file.

so all in all, this command will delete menu.lst that we have messed with, and put the backup there instead.

EDIT: this is actually my only suggestion (I am really bad at this) so if it does not work, then I have no clue. There are plenty of gurus out there that know how to fix your problem, This suggestion has worked for a lot of people, but it is probably not the problem that you are facing.

---

### Post by Teatro on 2009-03-30
jakupl- Thanks for taking the time to go through all that for me. I had actually already (before posting to the forum at all) stopped the splash screen to reveal the boot sequence- I got Ubuntu from a magazine that explained how to do that (of course, the disk was corrupt, so I had to download it anyway.. but that's another story). Unfortunately the magazine is not all that informative about this particular issue. I must say, Ubuntu/linux seems to be working great except for this boot issue. Unfortunately I have some apps in Windows that I can't live without (notably Photoshop, and no, GIMP doesn't quite cut it (or, maybe it does, but I don't have the time to relearn everything I know in a new program)), so I have to switch back and forth- and this slow boot business is discouraging me from exploring linux as much as I'd like to. Anyway, I appreciate the help.

---

### Post by jakupl on 2009-03-30
> **Teatro said:**
> jakupl- Thanks for taking the time to go through all that for me. I had actually already (before posting to the forum at all) stopped the splash screen to reveal the boot sequence- I got Ubuntu from a magazine that explained how to do that (of course, the disk was corrupt, so I had to download it anyway.. but that's another story). Unfortunately the magazine is not all that informative about this particular issue. I must say, Ubuntu/linux seems to be working great except for this boot issue. Unfortunately I have some apps in Windows that I can't live without (notably Photoshop, and no, GIMP doesn't quite cut it (or, maybe it does, but I don't have the time to relearn everything I know in a new program)), so I have to switch back and forth- and this slow boot business is discouraging me from exploring linux as much as I'd like to. Anyway, I appreciate the help.

Well, don't let it beat you, a 3 minute boot time is certainly not normal, you are very unlucky. I would probably try 8.04 instead. It is more stable in my opinion, and it is a long term support edition. witch meens that it is supported until April, 2011 (longer than 8.10 and 9.04), it is actually supported until 11.04 comes out!!
I am personally a big fan of LTS editions. You don't get the newest of the newest, but well... If it ain't broken, don't fix it, and 8.04 works great for me so far.

---

### Post by philinux on 2009-03-30
> **Teatro said:**
> jakupl- Thanks for taking the time to go through all that for me. I had actually already (before posting to the forum at all) stopped the splash screen to reveal the boot sequence- I got Ubuntu from a magazine that explained how to do that (of course, the disk was corrupt, so I had to download it anyway.. but that's another story). Unfortunately the magazine is not all that informative about this particular issue. I must say, Ubuntu/linux seems to be working great except for this boot issue. Unfortunately I have some apps in Windows that I can't live without (notably Photoshop, and no, GIMP doesn't quite cut it (or, maybe it does, but I don't have the time to relearn everything I know in a new program)), so I have to switch back and forth- and this slow boot business is discouraging me from exploring linux as much as I'd like to. Anyway, I appreciate the help.

Right well if you see all the text at boot up where does it hang. Whats the last message on screen as it takes it's time to boot. I'm not a bootchart expert but knowing where the boot precess gets hung up can help.

---

### Post by Teatro on 2009-03-30
Phil, the messages that hang up look like :


[ 868069] ata1.00 status { DRDY }

or
[ 868069] res 40/00:00:00:00/00:00:00 Emask 0X4 (timeout)

There are about a dozen that look pretty similar. I would copy and paste the whole sequence here, but I don't know how. Did the Bootchart tell you anything?

---

### Post by Teatro on 2009-03-30
> **jakupl said:**
> Well, don't let it beat you, a 3 minute boot time is certainly not normal, you are very unlucky. I would probably try 8.04 instead. It is more stable in my opinion, and it is a long term support edition. witch meens that it is supported until April, 2011 (longer than 8.10 and 9.04), it is actually supported until 11.04 comes out!!
I am personally a big fan of LTS editions. You don't get the newest of the newest, but well... If it ain't broken, don't fix it, and 8.04 works great for me so far.

This sounds like sage advice. If I install 8.04, do I have to do anything special? Reformat? back up data files? uninstall 8.11?

---

### Post by philinux on 2009-03-30
> **Teatro said:**
> Phil, the messages that hang up look like :


[ 868069] ata1.00 status { DRDY }

or
[ 868069] res 40/00:00:00:00/00:00:00 Emask 0X4 (timeout)

There are about a dozen that look pretty similar. I would copy and paste the whole sequence here, but I don't know how. Did the Bootchart tell you anything?

Bootchart does indeed show a lot of hanging up time. Seeing as you dual boot, I'd back up anything in ubuntu and reinstall from a freshly burnt, and checked for defects cd. In fact seeing as you're dual booting I'd use 9.04 64bit. The beta is out and boots much faster than Intrepid.

---

### Post by Teatro on 2009-03-30
> **philinux said:**
> Bootchart does indeed show a lot of hanging up time. Seeing as you dual boot, I'd back up anything in ubuntu and reinstall from a freshly burnt, and checked for defects cd. In fact seeing as you're dual booting I'd use 9.04 64bit. The beta is out and boots much faster than Intrepid.

8.04 or 9.04??? Inquiring minds are confused.

---

### Post by jakupl on 2009-03-30
> **Teatro said:**
> This sounds like sage advice. If I install 8.04, do I have to do anything special? Reformat? back up data files? uninstall 8.11?

That's your own call really, do you have a lot of precious stuff on ubuntu? then you could just move it to your windows partition and use that as a backup. I would not backup the entire /home, because I am not sure how all the configuration files would work on 8.04.

You could also keep 8.10 and have a triple boot. That will probably mean that you will need to use the manual option when the installer gets to the partition part... and watch out... partitioning is potentially dangerous if you are not sure of what you are doing.
I have a triple boot of ubuntu 8.04, Windows and Kubuntu 8.10. without any problems.

Or do what  philinux says. get 9.04. I suspect it is a bit buggy right now, but you will then be much more up-to-date, and it is only like 24 days till 9.04 reaches its final release.

EDIT: just to make things clear. This is not a typo. I am talking about 8.04 LST, and philinux is talking about 9.04.

---

### Post by philinux on 2009-03-30
> **Teatro said:**
> 8.04 or 9.04??? Inquiring minds are confused.
[http://cdimage.ubuntu.com/releases/9.04/beta/](http://cdimage.ubuntu.com/releases/9.04/beta/)
Scroll down for torrents.

New release out Apr 23 Jaunty Jackalope 9.04
[http://news.zdnet.co.uk/software/0,1000000121,39633297,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39633297,00.htm)

---

### Post by Teatro on 2009-03-30
Okay... so maybe I should just live with the slow boot for 24 days and install 9.04. If I install 8.04 what, if anything, am I missing?
\

---

### Post by Teatro on 2009-03-30
Phil, thanks for the links. Jaunty Jackalope sounds like it does great things I don't understand!! I suspect my need for cloud computing is limited at best... but the faster boot up sounds good. Thanks again!

---

