---
title: "ubuntu 9.10 can t detect external hdd"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by iruormen on 2010-01-27
hello everyone,
no need to tell you that i am an absolute 0 beginner;), and that i have not been doing my homework ](*,)
so, ubuntu cannot detect my external hdd. it was working just fine only few hours ago. i hooked it to another machine, win vista, and it told me that i have to format it before i can use it.
 i have some critical data on that hdd, thanks in advance for any help.

peace

---

### Post by halitech on 2010-01-27
with the device plugged into the Ubuntu machine, can  you post the output of
```
lsusb
```and```
sudo fdisk -l
```thats a lower case L, not the number 1

---

### Post by iruormen on 2010-01-27
thanks for the prompt response.
here is what "lsusb" gives:
[COLOR=DarkRed]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1004:605e LG Electronics, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]

and here is what "sudo fdisk -l" gives:

[COLOR=DarkRed]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3834    30796573+   7  HPFS/NTFS
/dev/sda2            5750        7296    12426277+   c  W95 FAT32 (LBA)
/dev/sda3            3835        5506    13430340   83  Linux
/dev/sda4            5507        5749     1951897+   5  Extended
/dev/sda5            5507        5749     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41fe77f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156295361    7  HPFS/NTFS

[/COLOR]the hdd in question is not mentioned at all. 
thanx again for your time.

---

### Post by phillw on 2010-01-27
> **iruormen said:**
> hello everyone,
no need to tell you that i am an absolute 0 beginner;), and that i have not been doing my homework ](*,)
so, ubuntu cannot detect my external hdd. it was working just fine only few hours ago. i hooked it to another machine, win vista, and it told me that i have to format it before i can use it.
 i have some critical data on that hdd, thanks in advance for any help.

peace

Hi, and welcome to the forums ...

When Win Vista said you had to format the drive before you could use it - Did you ?

Phill.

---

### Post by phillw on 2010-01-27
> **iruormen said:**
> [COLOR=DarkRed]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156295361    7  HPFS/NTFS

[/COLOR]the hdd in question is not mentioned at all. 
thanx again for your time.


That is your external hard drive, noted by the fact sda is the first actual physical hard drive and sdb is the next one ...

---

### Post by halitech on 2010-01-27
so how many drives do you have? I'm seeing 2 drives so far, a 60gig and a 160gig. How big is the drive in question?

---

### Post by iruormen on 2010-01-27
no i did not format it :-)

---

### Post by iruormen on 2010-01-27
yep, the external hdd i am concerned with is the 160gb.

---

### Post by halitech on 2010-01-27
well if the 160 is your external then yes it is mentioned

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41fe77f7

Device Boot Start End Blocks Id System
/dev/sdb1 1 19458 156295361 7 HPFS/NTFS
```

Looks like most of the drive is NTFS

---

### Post by phillw on 2010-01-27
Please, please..... say you didn't format it 

Phill.

---

### Post by phillw on 2010-01-27
Save cross over, I'll leave you with halitech. If you didn't format it, your data is safe :D

Regards,

Phill.

---

### Post by halitech on 2010-01-27
stick around, I may need the help

---

### Post by iruormen on 2010-01-27
yes, i could see that after my smart remark :-) 
anyway, that's my 2nd or 3rd week with ubuntu and linux. knew only NTFS before. 
being able to detect it with a command, why wouldn't it be able to mount it? the last time i could access that drive was under ubuntu.
it s 2am here, i ll be off for some hours.
thx again and best regards.

---

### Post by iruormen on 2010-01-27
thanx

---

### Post by phillw on 2010-01-27
> **halitech said:**
> stick around, I may need the help


<< lurking  ;)

/edit - I'll subscribe to the thread - I'll get email when we all wake up, it's also 12:48am here !!!

Phill.

---

### Post by iruormen on 2010-01-27
allright, i ll be here for an hour or so

---

### Post by Sylslay on 2010-01-27
Connect to usb and run Windows from dual boot.
Close Windows and start linux again and see if is mounted.

Becouse sometimes when You unplug Yours HDD from other machine (with is on), than its set some Flags , and than linux can't mount it.

---

### Post by Monotoko on 2010-01-27
hmmm, not sure if this will work, but its worth a shot:

```
mkdir /media/exthd
```

then

```
sudo mount -t ntfs /media/exhd /dev/sdb1 
```

If it doesnt work itl at least give an error ^.^

---

### Post by phillw on 2010-01-27
Boot into Ubuntu, without the drive plugged in.

Let ubuntu get to the main screen, then plug the drive in - If it does not auto-mount after about 30 seconds (and I mean 30, not 10 !!), click on **Places** and see if it is listed there - if it is, select it.

Let me know how that goes.. I'll be about for a while longer, also.

Regards,

Phill.

---

### Post by iruormen on 2010-01-27
nothing happened

---

### Post by iruormen on 2010-01-27
permission denied to create directory upon:
mkdir /media/exthdand at:
sudo mount -t ntfs /media/exhd /dev/sdb1



ntfs-3g: Failed to access volume '/media/exhd': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

---

### Post by halitech on 2010-01-27
the first command should have been
```
sudo mkdir /media/exthd
```

---

### Post by Monotoko on 2010-01-27
Yeah, sorry my mistake ^.^

---

### Post by iruormen on 2010-01-27
now it can t create the directory because the file exists. :-)
off for some hours, thank you all for your time and efforts; makes one feel in the right place with the right people under the right OS.
regards

---

### Post by phillw on 2010-01-28
> **iruormen said:**
> now it can t create the directory because the file exists. :-)
off for some hours, thank you all for your time and efforts; makes one feel in the right place with the right people under the right OS.
regards

<< also back from sleep :-)

```
 sudo rmdir /media/exthdand 
```Now, one of these will give an error and one will work - The reason I'm doing it this way is that I do not like telling people to **sudo rm-r**  It **WILL** completely wipe a system if issued in the wrong place (a typo can have devastating results, also)
```
sudo rm /media/exthd
sudo rmdir /media/exthd
```Now we know the file or directory has gone we can create it and mount your drive...

```

sudo mkdir /media/exthd
sudo mount -t ntfs /media/exthd /dev/sdb1
```Regards,

Phill.

---

### Post by iruormen on 2010-01-28
[FONT=monospace]sudo rmdir /media/exthd
sudo mkdir /media/exthd
sudo mount -t ntfs /media/exhd /dev/sdb1
[COLOR=DarkRed]ntfs-3g: Failed to access volume '/media/exhd': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

[COLOR=Black]by the way, if you re still out there, what can possibly be the problem in your opinion?? theoritically speaking ;-)
take care
[/COLOR][/COLOR][/FONT]

---

### Post by halitech on 2010-01-28
looks like a typo to me

here you tell it to make the directory /media/exthd but then you are telling it to mount in /media/exhd. try mounting it in the directory you made
```
sudo mount -t ntfs /media/exthd /dev/sdb1
```

---

### Post by phillw on 2010-01-28
> **halitech said:**
> looks like a typo to me

here you tell it to make the directory /media/exthd but then you are telling it to mount in /media/exhd. try mounting it in the directory you made
```
sudo mount -t ntfs /media/exthd /dev/sdb1
```

A thousand apologies --- Bad typo !!! - Now you know why i don't use rm -r !!!!:oops:

Phill.

---

### Post by iruormen on 2010-01-28
hello again my friends,
so i tried and typed the commands correctly this time :-P
now i m having this kind of help menu with commands and their expected output, what should i do next?? 
[COLOR=DarkRed] sudo mount -t ntfs /media/exthd 
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
For many more details, say  man 8 mount .[/COLOR]

ps: finished my day, waiting for your assistance, cheers.

---

### Post by phillw on 2010-01-28
You'll kick your-self for this ...

>  [COLOR=DarkRed] sudo mount -t ntfs /media/exthd [/COLOR]

Err, no - you haven't told mount *what* to mount ;)

```

sudo mount -t ntfs /media/exthd /dev/sdb1
```

Regards,

Phill.

---

### Post by iruormen on 2010-01-28
:-D what about telling me what to read, a quick 101 tutorial; if you know of any. it ll be a good boost to my selfesteem ;-)

---

### Post by iruormen on 2010-01-28
same old "Error opening '/media/exthd': Is a directory" and failed to mount. :'(

---

### Post by phillw on 2010-01-28
::SIGH::

Now I know why i don't use the terminal to mount things !!!

```
sudo mount /dev/sdb /media/exthd
```

Serves me right for not checking it on my system !!!

Phill.

---

### Post by phillw on 2010-01-28
> **iruormen said:**
> :-D what about telling me what to read, a quick 101 tutorial; if you know of any. it ll be a good boost to my selfesteem ;-)

In the stickies at the top this forum, go to > **[B]Sticky:**[/B] 			                         [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Free Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1052065") [2]("http://ubuntuforums.org/showthread.php?t=1052065&page=2")  [3]("http://ubuntuforums.org/showthread.php?t=1052065&page=3")  ... [Last  Page]("http://ubuntuforums.org/showthread.php?t=1052065&page=78")) 		  		  		 			 			 				

And get it :-)

As you get time, read the next two stickies below it, as well.

Regards,

Phill.

---

### Post by VernonA on 2010-01-28
Hi Phil,
You got the order of device and directory right, but now I think you forgot the "-t ntfs" part;)
You need to sleep more at night!
Cheers
Vernon

---

### Post by phillw on 2010-01-28
> **VernonA said:**
> Hi Phil,
You got the order of device and directory right, but now I think you forgot the "-t ntfs" part;)
You need to sleep more at night!
Cheers
Vernon
>  -t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, smbfs, sysv, tmpfs,  udf,  ufs,  umsdos,
              usbfs,  vfat,  xenix,  xfs, xiafs.  Note that coherent, sysv and
              xenix are equivalent and that xenix and coherent will be removed
              at  some  point  in  the future — use sysv instead. Since kernel
              version 2.1.21 the types ext and xiafs  do  not  exist  anymore.
              Earlier,  usbfs  was  known as usbdevfs.  Note, the real list of
              all supported filesystems depends on your kernel.

              For most types all the mount program has to do is issue a simple
              mount(2)  system call, and no detailed knowledge of the filesys&#8208;
              tem type is required.  For a few types however (like nfs,  nfs4,
              cifs,  smbfs,  ncpfs)  ad  hoc code is necessary. The nfs, nfs4,
              cifs, smbfs, and ncpfs have a separate mount program.  In  order
              to  make  it possible to treat all types in a uniform way, mount
              will execute the program /sbin/mount.TYPE (if that exists)  when
              called  with  type TYPE.  Since various versions of the smbmount
              program have different  calling  conventions,  /sbin/mount.smbfs
              may have to be a shell script that sets up the desired call.

              **If  no  -t  option  is  given,** or if the auto type is specified,
              mount will try to guess the desired type.  Mount uses the  blkid
              or  volume_id  library for guessing the filesystem type; if that
              does not turn up anything that looks familiar, mount will try to
              read  the  file  /etc/filesystems,  or,  if that does not exist,
              /proc/filesystems.  All of the  filesystem  types  listed  there
              will  be tried, except for those that are labeled "nodev" (e.g.,
              devpts, proc and nfs).  If /etc/filesystems ends in a line  with
              a single * only, mount will read /proc/filesystems afterwards.

              The auto type may be useful for user-mounted floppies.  Creating
              a file /etc/filesystems can be useful to change the probe  order
              (e.g.,  to  try vfat before msdos or ext3 before ext2) or if you
              use a kernel module autoloader.  Warning:  the  probing  uses  a
              heuristic  (the presence of appropriate `magic'), and could rec&#8208;
              ognize the wrong filesystem  type,  possibly  with  catastrophic
              consequences.  If  your  data  is  valuable,  don't ask mount to
              guess.

              More than one type may be specified in a comma  separated  list.
              The list of file system types can be prefixed with no to specify
              the file system types on which no action should be taken.  (This
              can be meaningful with the -a option.)


Or, put simply, mount is pretty smart at working out what the file system is :-)

I mounted my usb memory stick using that command - that's how i realised the 1st answer was actually wrong - more fool me for not checking on my own system !!

Regards,

Phill.

Regards,

Phill.

---

### Post by iruormen on 2010-01-28
sorry to disappoint you all, but what about a piece of software that could fix the problem?? does ubuntu have any??
thank you phill for the hint to the pocket guide, i m sure my weekend will be very instructive :-)

best regards

---

### Post by phillw on 2010-01-28
Yes, you can do it via the GUI (Menu) - That's what I use - hence being rusty on the command line !!

System --> Administration --> Synaptic Package Manager

Type in pysdm and click the box. Select Mark for Installation. Then Click on Apply.

Once that is done, you can close Synaptic.

Plug in the Hard Drive.

You will have a new option under System --> Administration --> Storage Device Manager

From that you should be able to select sdb, ?Assistant and put a check in the box Mount at Boot time. You *may* need to press the Mount Button  First.

There's a good over-view of the topic here --> [http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

Regards,

Phill.

---

### Post by iruormen on 2010-01-28
thanx a lot, i ll give it a try and let you know (y)

---

### Post by Ftech on 2010-01-31
Hello Phill,
I have been having what seems to be the same issue as iruormen, however once i opened the storage device manager and select sdb everything is grayed out and I can not click any of the buttons. It is the same for sda. My drive is connected via firewire if that matters.

---

### Post by Cheezespread on 2010-02-01
> **Ftech said:**
> Hello Phill,
I have been having what seems to be the same issue as iruormen, however once i opened the storage device manager and select sdb **everything is grayed out **and I can not click any of the buttons. It is the same for sda. My drive is connected via firewire if that matters.

Seems like you have opened the same as a user and not root ( not sure if advised to ) .I may be wrong too.  Try ```
sudo pysdm 
``` and let us know if you still have the issue.

---

### Post by phillw on 2010-02-01
Hi, and welcome to the Forums,

I've never had a FireWire drive connected to a Ubuntu Installation. I recall from my windows days, that a fire-wire drive had to be set up as the master drive in the housing - I don't know if this is the case for Ubuntu. There was a bug in Ubuntu with Firewire drives with 9.10  but that has been long fixed :\

Sorry I can't help you further, nor can i find any threads on it.

Regards,

Phill.

---

### Post by phillw on 2010-02-01
> **Cheezespread said:**
> Seems like you have opened the same as a user and not root ( not sure if advised to ) .I may be wrong too.  Try ```
sudo pysdm 
``` and let us know if you still have the issue.


If you're wanting to use a grapical interface, issuing sudo can cause problems.

use ```
gksudo pysdm
```  If you get into the habit of using gksudo for things with a GUI (a window, as opposed to only command line), it'll stop you breaking something that is really picky about it (like FireFox !!)

Regards,

Phill.

---

### Post by Ftech on 2010-02-01
Dear Phill and Cheeze,
 I have tried both methods and all options are still grayed out besides refresh, close, and apply. 

Perhaps 9.10 just doesn't like firewire NTFS?

---

### Post by phillw on 2010-02-02
> **Ftech said:**
> Dear Phill and Cheeze,
 I have tried both methods and all options are still grayed out besides refresh, close, and apply. 

Perhaps 9.10 just doesn't like firewire NTFS?

Hi,

If sdb is being listed, then it seems that Ubuntu can see it.. Try ..

```

sudo mkdir /media/exthd
sudo mount -t ntfs /dev/sdb1 /media/exthd 
```

Regards,

Phill.

---

### Post by Ftech on 2010-02-02
This error message shows up when I try that:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

 any ideas?

---

### Post by egalvan on 2010-02-03
> **phillw said:**
> Hi, and welcome to the Forums,

I've never had a FireWire drive connected to a Ubuntu Installation.
 I recall from my windows days, that a fire-wire drive had to be set up as the master drive in the housing - I don't know if this is the case for Ubuntu.
 There was a bug in Ubuntu with Firewire drives with 9.10  but that has been long fixed :\

Phill.

I use FireWire on an HP laptop running Hardy.
PATA drive mounted in an Adaptech USB/Firewire enclosure.
No problems ever, I see no difference from USB, other than more efficient throughput.

I will be updating Hardy to Lucid 10.4 LTS about a month after it debuts... I like stability on this machine.
Hopefully no Firewire problems.

Furhter...
the enclosure driver chip-set determine if the drive needs to be MASTER or SLAVE or CABLE-SELECT.
USB and Firewire don´t have Master/Slave settings...

---

### Post by phillw on 2010-02-03
> **Ftech said:**
> This error message shows up when I try that:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

 any ideas?


You can always try ```

sudo mount -t ntfs /dev/sdb /media/exthd 
```

Phill.

---

### Post by phillw on 2010-02-03
> **egalvan said:**
> 
Furhter...
the enclosure driver chip-set determine if the drive needs to be MASTER or SLAVE or CABLE-SELECT.
USB and Firewire don´t have Master/Slave settings...

On the carriers I have used, the hard disk jumpers set whether it is slave are master - and for F/wire housings I have had with F/wire for Win and Mac it is required to be set to master.

I don't have a FireWire Card for my current Laptop.... well, I do have one - I just haven't seen it for a few months !!  On the subject of 8.04 - be on 8.04.4 ready for the jump to 10.04 ... Lucid is looking real good :D

Phill.

---

### Post by phillw on 2010-02-03
Here's a couple of threads to have a peruse through - Whilst not 'for' FireWire, as the rule in the Linux is that everything's a file ;) They are worth having a read through to see if you have the errors they are seeing.

[http://ubuntuforums.org/archive/index.php/t-961598.html](http://ubuntuforums.org/archive/index.php/t-961598.html)

and

[http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/](http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/)

Regards,

Phill.

---

### Post by Ftech on 2010-02-03
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Still no luck :/

---

### Post by phillw on 2010-02-03
Hi, 

if it is working okay with a Win installation, then I'm at a loss - I don't have Firewire on my laptop. If it is not okay with Win, then have a read of threads at post #50.

I *may* have access to a firewire PCMIA card next week - that's all I can do.

Sorry,

Phill.

---

### Post by Ftech on 2010-02-04
It's alright, thanks anyway for your help :) It does work on my windows partiton so I'll keep trying things.

---

### Post by Camaguey on 2010-02-06
I have the same problem, except I'm trying to mount my external hdd through USB. I've come to believe that we are not unmounting the hdd from windows before trying to mount on Linux, effectively locking the drive. I'm sure there's a way to force mount it, but that risks the data.

Even NTFS configuration tool has not worked for me, but maybe you'll have better luck.

---

### Post by phillw on 2010-02-06
> **Camaguey said:**
> I have the same problem, except I'm trying to mount my external hdd through USB. I've come to believe that we are not unmounting the hdd from windows before trying to mount on Linux, effectively locking the drive. I'm sure there's a way to force mount it, but that risks the data.

Even NTFS configuration tool has not worked for me, but maybe you'll have better luck.

Hi and welcome to the forums,

Thanks for the information. It sorta rings a bell - I've not run Windows for too long !!!
I am due over to where the FireWire Card is, also where my USB (Win) Hard Disk is (It's out on loan) Early next week - So, Should be able to have a play. I'll pick up a spare hard drive as well, as the carrier for the Mac here has both FireWire & USB connections, but I cannot risk that disk - it's got accounts backup on :p

/edit - having had a dig a bit further & you reminding me about the locking of disks ... This may be worth a read ...

[http://ubuntuforums.org/archive/index.php/t-1109332.html](http://ubuntuforums.org/archive/index.php/t-1109332.html)

Regards,

Phill.

---

### Post by Camaguey on 2010-02-07
I solved my mounting problem by hooking up my external hdd to a friend's windows box and "Safely Removing the Hardware" or whatever, now it works like a charm :p.

If you last connected it to windows, try it. Don't bother with virtual box though, apparently if the base OS (Ubuntu) can't access the drive, then the windows OS I had going in virtual box couldn't do it either.

---

