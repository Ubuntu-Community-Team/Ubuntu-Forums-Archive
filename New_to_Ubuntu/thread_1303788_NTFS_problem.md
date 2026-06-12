---
title: "NTFS problem"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by acatak on 2009-10-28
hello everyone,
i have had Ubuntu for about two weeks now, so I am a beginner.  I am having problems with my XP computer as everytime I boot XP (I'm dual booting with XP) I get the blue screen of death after 3 seconds.  I can not even boot with any of the options (safe mode ect.)  but Ubuntu works fine.  I researched on google the error and it is STOP: 0X000000024.  I don't have the XP cd, but I can get one at school.  I also read that I need to use the chkdsk utility.  This is not possible as I can not boot with command prompt.  Is there an equivilant for Ubuntu?  How can I get it?  Anyhelp is appreciated!

---

### Post by SunnyRabbiera on 2009-10-28
Its possible you might have messed up XP when setting up your dual boot.
Did you defrag before installing Ubuntu?

---

### Post by acatak on 2009-10-28
> **SunnyRabbiera said:**
> Its possible you might have messed up XP when setting up your dual boot.
Did you defrag before installing Ubuntu?
Thx for responding, I did not defrag before installing Ubuntu.  (i dont know what that is)

As i said, it worked fine for  1 week, XP and Ubunutu.  Then I was having some errors with programs, then I ran chkdsk in safemode, and it fixed the problems, now I have the blue screen of death

---

### Post by SunnyRabbiera on 2009-10-28
> **acatak said:**
> Thx for responding, I did not defrag before installing Ubuntu.  (i dont know what that is)

As i said, it worked fine for  1 week, XP and Ubunutu.  Then I was having some errors with programs, then I ran chkdsk in safemode, and it fixed the problems, now I have the blue screen of death

Ohh, ow ow no wonder why you are having issues with Windows.
Sorry to say but I think your windows side is gone, you can boot into it but you cant actually go into windows.
Before dual booting it is always advised to defrag Windows.
Can you see the windows drive on your Ubuntu partition?

---

### Post by acatak on 2009-10-28
how do you do that?

i am new to ubuntu

---

### Post by vinutux on 2009-10-28
That is not related to ubuntu and your problem is not because of installing ubuntu........... Search around google for windows forums etc....

---

### Post by SunnyRabbiera on 2009-10-28
> **acatak said:**
> how do you do that?

i am new to ubuntu

Well I am assuming you are on your Ubuntu side now, with any luck you can see the windows drive by going to the "places" menu and go to "computer"
Hopefully the windows drive might be there, if not you are pretty much screwed on your windows files...
I mean you can edit a few files here and there to make it appear but your files might be gone none the less.
This is no fault of Ubuntu's, I know its frustrating to realize that you might have totally lost your windows files but this is the danger of a dualboot, especially when you dont defrag windows.

> **vinutux said:**
> That is not related to ubuntu and your problem is not because of installing ubuntu........... Search around google for windows forums etc....

No it is related, his issue was caused by his attempt at a dual boot.
Yes its not Ubuntus fault but the original poster should have defragged.

---

### Post by acatak on 2009-10-28
> **vinutux said:**
> That is not related to ubuntu and your problem is not because of installing ubuntu........... Search around google for windows forums etc....


I totally understand that; but I have a Ubuntu question: is there a program that can be used to check the hard drive like the chkdsk utility for windows?

---

### Post by sydbat on 2009-10-28
How did you install Ubuntu? 

Did you use the wubi installation method (making Ubuntu a 'program' inside Windows)?

Or did you make a separate partition for Ubuntu after resizing your Windows partition?

Knowing this will help us help you.

---

### Post by acatak on 2009-10-28
> **sydbat said:**
> How did you install Ubuntu? 

Did you use the wubi installation method (making Ubuntu a 'program' inside Windows)?

Or did you make a separate partition for Ubuntu after resizing your Windows partition?

Knowing this will help us help you.

thx for responding, I used the wubi installation method.  I did do research about the problem, and I need to use the chkdsk utility.  The problem is taht I can't do that from Windows.  I want to know if there is a way from Ubuntu.

Thanks everyone for your help!

---

### Post by lavinog on 2009-10-28
did xp come with your computer or did you build this computer?

I don't agree with the defrag statement entirely especially if xp was working after the install.  How much free space is there on the ntfs partition?  Once you go below 10% free bad things can happen.
How old is the drive?  It could be that the drive is failing, and the limited space is compounding the problem.
Can you access the ntfs partition through ubuntu?  If so backup what you can to cd or dvd.
If your system came with xp, you should be able to get a recovery disk somewhere...find a friend that has the same brand as you and see if they have a recovery disk.

Edit: testdisk might be able to help you, but I have never used it to recover a bad partition yet.  Photorec is part of the testdisk package and it is good at recovering files on a failed disk.
> Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.
wubi installs do not require defrag prior to installing.

---

### Post by SunnyRabbiera on 2009-10-28
> **lavinog said:**
> did xp come with your computer or did you build this computer?

I don't agree with the defrag statement entirely especially if xp was working after the install.

No trust me defrag before a dual boot is very advised, especially if the user has a lot of files.
I have seen XP screw up without a defrag on a dual boot setup it was not nice.
It happened to me when I first tried to dual boot.

---

### Post by vinutux on 2009-10-28
there is** fsck** but its for linux file system i think.........

---

### Post by sydbat on 2009-10-28
> **lavinog said:**
> did xp come with your computer or did you build this computer?

I don't agree with the defrag statement entirely especially if xp was working after the install.  How much free space is there on the ntfs partition?  Once you go below 10% free bad things can happen.
How old is the drive?  It could be that the drive is failing, and the limited space is compounding the problem.
Can you access the ntfs partition through ubuntu?  If so backup what you can to cd or dvd.
If your system came with xp, you should be able to get a recovery disk somewhere...find a friend that has the same brand as you and see if they have a recovery disk.I would disagree with the "drive might be failing" idea. The OP can still run Ubuntu fine, even though it is running as a virtual OS via wubi. 

I think that the Windows file system has become corrupted and that the OP will not be able to use Ubuntu either in a short while...so backing up is the best thing to do before it all becomes an unusable mess.

---

### Post by SunnyRabbiera on 2009-10-28
> **vinutux said:**
> there is** fsck** but its for linux file system i think.........

Yeh I dont think it covers NTFS sadly.

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> thx for responding, I used the wubi installation method.  I did do research about the problem, and I need to use the chkdsk utility.  The problem is taht I can't do that from Windows.  I want to know if there is a way from Ubuntu.

Thanks everyone for your help!

If your Windows partition is ntfs and not fat32, I don't recommend trying to do any filesystem repair from Linux.

You need a Windows cd and run the repair utility. Or perhaps something like Ultimate Boot Disc has what you need.

---

### Post by lavinog on 2009-10-28
> **SunnyRabbiera said:**
> No trust me defrag before a dual boot is very advised, especially if the user has a lot of files.
I have seen XP screw up without a defrag on a dual boot setup it was not nice.
It happened to me when I first tried to dual boot.
> 
Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

Technically wubi installs are not dual boot, and since the partition exists as a file on the ntfs partition, i fail to see how defrag is needed.

---

### Post by SunnyRabbiera on 2009-10-28
> **lavinog said:**
> Technically wubi installs are not dual boot, and since the partition exists as a file on the ntfs partition, i fail to see how defrag is needed.

Yes but we dont know if he used Wubi or not

---

### Post by acatak on 2009-10-28
there is still like 30 GiB of space left, that shouldnt be the problem

the drive is about 3 years old.  Its a INSPIRON 6400, and it came with XP

I can not access the ntfs partition through ubuntu.

I will try and get a recovery disc at school

EDIT: Does wine have any thing to do with it?
A failing disc might be the problem, as my friend has the same laptop as me, and his hard drive failed.

---

### Post by lavinog on 2009-10-28
> **sydbat said:**
> I would disagree with the "drive might be failing" idea. The OP can still run Ubuntu fine, even though it is running as a virtual OS via wubi. 

I think that the Windows file system has become corrupted and that the OP will not be able to use Ubuntu either in a short while...so backing up is the best thing to do before it all becomes an unusable mess.

drive failures can start with file system corruption.

---

### Post by lavinog on 2009-10-28
> **SunnyRabbiera said:**
> Yes but we dont know if he used Wubi or not

post #10

---

### Post by vinutux on 2009-10-28
> **SunnyRabbiera said:**
> Yeh I dont think it covers NTFS sadly.

Is there is any progs like that... covering both win and linux file systems ?

---

### Post by lavinog on 2009-10-28
> **vinutux said:**
> Is there is any progs like that... covering both win and linux file systems ?

testdisk and photorec (i use photorec alot to recover lost data from other peoples computers)

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> there is still like 30 GiB of space left, that shouldnt be the problem

the drive is about 3 years old.  Its a INSPIRON 6400, and it came with XP

I can not access the ntfs partition through ubuntu.

I will try and get a recovery disc at school

Not a recovery disc, either the actual Windows install cd or something like hiram's or ultimate boot.

Most recovery cd's just restore the factory defaults, which means they format your computer and reload the factory partition. This is not what you want.

You need something that can load the Windows Repair environment, or some kind of ntfs repair tool. 

Did you use Wubi to install or did you create a separate partition for Ubuntu? You used Wubi per post #10

---

### Post by vinutux on 2009-10-28
> **lavinog said:**
> testdisk and photorec (i use photorec alot to recover lost data from other peoples computers)

wow... going 2 check that.....:D

---

### Post by acatak on 2009-10-28
> **Saghaulor said:**
> Not a recovery disc, either the actual Windows install cd or something like hiram's or ultimate boot.

Most recovery cd's just restore the factory defaults, which means they format your computer and reload the factory partition. This is not what you want.

You need something that can load the Windows Repair environment, or some kind of ntfs repair tool. 

Did you use Wubi to install or did you create a separate partition for Ubuntu? You used Wubi per post #10

yes I am sure that I used wubi

---

### Post by lavinog on 2009-10-28
Also any repair utility would need to be ran from a live cd.  You cannot use ubuntu to repair the partition that it is located in (due to wubi install)

as mentioned:
If you use a recovery disk, you might loose everything on your hd.  I would recommend to do what you can to backup everything before using a recovery disk.

---

### Post by acatak on 2009-10-28
> **lavinog said:**
> Also any repair utility would need to be ran from a live cd.  You cannot use ubuntu to repair the partition that it is located in (due to wubi install)

as mentioned:
If you use a recovery disk, you might loose everything on your hd.  I would recommend to do what you can to backup everything before using a recovery disk.

is there any way to back up the windows files?

what about ntfsfix from ntfsprogs? what are those?

---

### Post by Saghaulor on 2009-10-28
Insofar as you can still use Ubuntu, I'd say you're data is still there.

Be very careful what you do.

You should be able to mount the Windows partition from Ubuntu, and be able to read and write data to it. 

That way you can get any data you need off the partition before you do anything potentially harmful.

It might show up under Places->Removable Devices

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> is there any way to back up the windows files?

what about ntfsfix from ntfsprogs? what are those?

```
man ntfsfix
```to learn about it.

There are certainly ways to back up the files. I always use Knoppix or Ubuntu livecd to boot the computer into a live environment, and then copy the data to a removable drive.

Also, you could use Clonezilla to image the drive to a removable disk.

---

### Post by SunnyRabbiera on 2009-10-28
> **acatak said:**
> there is still like 30 GiB of space left, that shouldnt be the problem

the drive is about 3 years old.  Its a INSPIRON 6400, and it came with XP

I can not access the ntfs partition through ubuntu.

I will try and get a recovery disc at school

Yeh good luck, again sorry for any issues you have faced but yes I think your issues might have been caused by not defragging windows.
You said you dont know what defragging is, well basically it fixes issues with the NTFS filesystem.
Think like NTFS like a refrigerator, with a lot of post it notes on it.
So say the first post it note a says "Get milk on Monday" but it does not say the date that Monday is on, another post it note says "get bread Tuesday" again no date given, soon you have a whole refrigerator covered in post it notes, each one with a new message.
But what if a gust of wind comes by and knocks off those post it notes?
The information is scattered, fragmented.
This is what happens with NTFS, it has a very nasty tendency to fragment its files.
Linux filesystems on the other hand do not fragment as badly or as easily.
In NTFS as soon as you make edits to a file it fragments.
In Linux's filesystems it only fragments when there is a low amount of space.
EXT3 and 4 in Ubuntu really dont have the fragment issues of NTFS.

> **lavinog said:**
> post #10

Yeh I see it now, but yeh maybe a defrag could have helped anyhow.
If you dont know what defrag is and you used XP for a long time XP corrupts itself.

---

### Post by lavinog on 2009-10-28
> **acatak said:**
> is there any way to back up the windows files?

what about ntfsfix from ntfsprogs? what are those?

There are many ways to backup the files, but you need something to back them up to like another hd. or network storage.

again you should not try and repair the partition through wubi...you could do more damage.  You should use a live cd.  Gparted on the live cd might give you an option to check a ntfs partition for errors.

---

### Post by Saghaulor on 2009-10-28
> **SunnyRabbiera said:**
> Yeh good luck, again sorry for any issues you have faced but yes I think your issues might have been caused by not defragging windows.
You said you dont know what defragging is, well basically it fixes issues with the NTFS filesystem.
Think like NTFS like a refrigerator, with a lot of post it notes on it.
So say the first post it note a says "Get milk on Monday" but it does not say the date that Monday is on, another post it note says "get bread Tuesday" again no date given, soon you have a whole refrigerator covered in post it notes, each one with a new message.
But what if a gust of wind comes by and knocks off those post it notes?
The information is scattered, fragmented.
This is what happens with NTFS, it has a very nasty tendency to fragment its files.
Linux filesystems on the other hand do not fragment as badly or as easily.
In NTFS as soon as you make edits to a file it fragments.
In Linux's filesystems it only fragments when there is a low amount of space.
EXT3 and 4 in Ubuntu really dont have the fragment issues of NTFS.

A BSOD could be from anything.

It's likely from something new being installed, whether new hardware, new software, or even an update.

I've had repeated issues with AVG8 on one Windows machine. Every time I install it on that machine, inevitably it BSODS with some cryptic message. As soon as I safe mode and remove it, the BSODs stop.

---

### Post by acatak on 2009-10-28
> **SunnyRabbiera said:**
> Yeh good luck, again sorry for any issues you have faced but yes I think your issues might have been caused by not defragging windows.
You said you dont know what defragging is, well basically it fixes issues with the NTFS filesystem.
Think like NTFS like a refrigerator, with a lot of post it notes on it.
So say the first post it note a says "Get milk on Monday" but it does not say the date that Monday is on, another post it note says "get bread Tuesday" again no date given, soon you have a whole refrigerator covered in post it notes, each one with a new message.
But what if a gust of wind comes by and knocks off those post it notes?
The information is scattered, fragmented.
This is what happens with NTFS, it has a very nasty tendency to fragment its files.
Linux filesystems on the other hand do not fragment as badly or as easily.
In NTFS as soon as you make edits to a file it fragments.
In Linux's filesystems it only fragments when there is a low amount of space.
EXT3 and 4 in Ubuntu really dont have the fragment issues of NTFS.

thx i understand that!

i have multiple USB keys, so filestorage is not the problem; i need to just view my XP files.  how can i do that?

---

### Post by Saghaulor on 2009-10-28
> **lavinog said:**
> There are many ways to backup the files, but you need something to back them up to like another hd. or network storage.

again you should not try and repair the partition through wubi...you could do more damage.  You should use a live cd.  Gparted on the live cd might give you an option to check a ntfs partition for errors.

Gparted has always told me to defer to Windows chkdsk.

I think it uses ntfsprogs, which if you read in the manual for ntfsfix, is limited in scope of what it can do.

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> thx i understand that!

i have multiple USB keys, so filestorage is not the problem; i need to just view my XP files.  how can i do that?

Have you tried searching for the partition in Ubuntu's Places?

---

### Post by Saghaulor on 2009-10-28
Have you read this yet?

[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by lavinog on 2009-10-28
> **SunnyRabbiera said:**
> 
In NTFS as soon as you make edits to a file it fragments.

The edit needs to increase the file size by one block size (4k i believe) to cause fragmentation.

fragmentation does not cause file errors under normal circumstances.  Yes you can have problems when resizing a ntfs partition, but this has more to do with ntfs being a closed format and is not fully supported with open source tools.
I believe gparted does what it can to relocate used blocks when a ntfs partition is resized, but new features in vista breaks compatibility with this feature (xp should work fine though.)  It can also fail if there is not enough free space.  File systems are like a game of tetris, the more free space you have the easier it is to compact all the blocks.

---

### Post by lavinog on 2009-10-28
> **acatak said:**
> thx i understand that!

i have multiple USB keys, so filestorage is not the problem; i need to just view my XP files.  how can i do that?

try booting into a live cd and see if you can access the drive from that.

---

### Post by Saghaulor on 2009-10-28
> **lavinog said:**
> try booting into a live cd and see if you can access the drive from that.

My worry is, since he/she is using Wubi, he/she probably doesn't have a livecd.

So my thoughts were lets see if we can mount the ntfs partition from the wubi Ubuntu install.

If it's not showing up in "Places" then we may have to power up and use the cli.

---

### Post by lavinog on 2009-10-28
another option is systemrescuecd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
it is only 200Mb and has a bunch of tools.

---

### Post by SunnyRabbiera on 2009-10-28
> **acatak said:**
> thx i understand that!

Yeh you said you didnt know what defrag was so I broke it down into terms a normal person can understand.

> **lavinog said:**
> The edit needs to increase the file size by one block size (4k i believe) to cause fragmentation.
Believe me it dont take that long to reach that kind of filesize.
Even a small text doccument a page long can go over that.
For small tiny files its fine, but it does not take much to make NTFS fragment.

> **lavinog said:**
> another option is systemrescuecd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
it is only 200Mb and has a bunch of tools.

I was wondering when someone was going to mention that, system rescue CD is a very good suggestion

---

### Post by acatak on 2009-10-28
> **Saghaulor said:**
> My worry is, since he/she is using Wubi, he/she probably doesn't have a livecd.

So my thoughts were lets see if we can mount the ntfs partition from the wubi Ubuntu install.

If it's not showing up in "Places" then we may have to power up and use the cli.

no i dont ahve a live cd, and it does not show up on places

---

### Post by Saghaulor on 2009-10-28
> **SunnyRabbiera said:**
> Yeh you said you didnt know what defrag was so I broke it down into terms a normal person can understand.


Believe me it dont take that long to reach that kind of filesize.
Even a small text doccument a page long can go over that.
For small tiny files its fine, but it does not take much to make NTFS fragment.

+1

Windows will basically fragment just sitting there burning kilowatts. Defragging on a monthly is a good idea.

I once diagnosed a computer that seemed to have a serious malware issue, but in actuality it was so severely fragmented that the fragmentation had caused a critical performance hit. After hours and hours of defragging the machine was running "normal" again.

---

### Post by lavinog on 2009-10-28
I wonder if a vista or windows 7 recovery disk will allow you to run chkdisk:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by lavinog on 2009-10-28
is it possible that there is a recovery partition already on this computer?
Is there a message when you boot to press f12 or something to go to recovery mode?

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> no i dont ahve a live cd, and it does not show up on places

Okay, try this.

```
 sudo fdisk -l
```

Then post the results.

That will show us where your Windows partition is.

---

### Post by acatak on 2009-10-28
No, when i press f12 it gives boot options on the drives, no recovery mode

Thats what i got:
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8707    69890782+   7  HPFS/NTFS
/dev/sda3            9066        9511     3582495    c  W95 FAT32 (LBA)

---

### Post by lavinog on 2009-10-28
> **acatak said:**
> No, when i press f12 it gives boot options on the drives, no recovery mode

/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8707    69890782+   7  HPFS/NTFS
/dev/sda3            9066        9511     3582495    c  W95 FAT32 (LBA)

It looks like a recovery partition does exist. It might not be f12, it could be f10, f2, f1...etc.
Does anyone with a dell laptop know how to access the recovery partition?

---

### Post by Saghaulor on 2009-10-28
> **acatak said:**
> No, when i press f12 it gives boot options on the drives, no recovery mode

Thats what i got:
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8707    69890782+   7  HPFS/NTFS
/dev/sda3            9066        9511     3582495    c  W95 FAT32 (LBA)

Okay, so I'm assuming your partition is on /dev/sda2.

I'll try to walk you through mounting it.

But I vaguely remember using Wubi. I think the partition is already mounted and added to the Ubuntu filesystem.

Do this

```
ls -al /
```

and this

```
ls -al /media
```

print your results

---

### Post by Saghaulor on 2009-10-28
> **lavinog said:**
> It looks like a recovery partition does exist. It might not be f12, it could be f10, f2, f1...etc.
Does anyone with a dell laptop know how to access the recovery partition?

The recovery partition will likely format everything. Let's leave that alone for now.

---

### Post by acatak on 2009-10-28
total 128
drwxr-xr-x  22 root root  4096 2009-10-12 19:10 .
drwxr-xr-x  22 root root  4096 2009-10-12 19:10 ..
drwxr-xr-x   2 root root  4096 2009-10-12 19:06 bin
drwxrwxrwx   1 root root  4096 2009-10-12 19:14 boot
lrwxrwxrwx   1 root root    11 2009-09-08 21:29 cdrom -> media/cdrom
drwxr-xr-x  16 root root  3960 2009-10-28 18:32 dev
drwxr-xr-x 127 root root 12288 2009-10-28 18:33 etc
drwxr-xr-x   3 root root  4096 2009-09-08 21:35 home
drwxrwxrwx   1 root root 28672 2009-10-26 18:16 host
lrwxrwxrwx   1 root root    33 2009-10-12 19:10 initrd.img -> boot/initrd.img-2.6.28-15-generic
lrwxrwxrwx   1 root root    33 2009-09-08 21:37 initrd.img.old -> boot/initrd.img-2.6.28-11-generic
drwxr-xr-x  19 root root 12288 2009-10-15 20:29 lib
drwx------   2 root root 16384 2009-09-08 21:29 lost+found
drwxr-xr-x   3 root root  4096 2009-10-28 18:32 media
drwxr-xr-x   2 root root  4096 2009-04-13 05:33 mnt
drwxr-xr-x   2 root root  4096 2009-04-20 09:59 opt
dr-xr-xr-x 146 root root     0 2009-10-28 14:32 proc
drwx------  11 root root  4096 2009-10-17 18:19 root
drwxr-xr-x   2 root root  4096 2009-10-28 16:05 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 11:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 09:59 srv
drwxr-xr-x  12 root root     0 2009-10-28 14:32 sys
drwxrwxrwt  14 root root  4096 2009-10-28 18:33 tmp
drwxr-xr-x  11 root root  4096 2009-04-20 10:00 usr
drwxr-xr-x  15 root root  4096 2009-04-20 10:07 var
lrwxrwxrwx   1 root root    30 2009-10-12 19:10 vmlinuz -> boot/vmlinuz-2.6.28-15-generic
lrwxrwxrwx   1 root root    30 2009-09-08 21:37 vmlinuz.old -> boot/vmlinuz-2.6.28-11-generic

---

### Post by acatak on 2009-10-28
ls -al /media
total 12
drwxr-xr-x  3 root root 4096 2009-10-28 18:32 .
drwxr-xr-x 22 root root 4096 2009-10-12 19:10 ..
lrwxrwxrwx  1 root root    6 2009-09-08 21:29 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-09-08 21:29 cdrom0
-rw-r--r--  1 root root    0 2009-10-28 18:32 .hal-mtab


ill be gone for about an hour, but ill brb

---

### Post by lavinog on 2009-10-28
Many recovery partitions give you various options destructive and non-destructive.
But get the files backed up first just in case.

---

### Post by Saghaulor on 2009-10-28
I'm not sure if that was one or two commmands.

But try this

```
sudo mkdir /media/windowsrecovery && sudo mount /dev/sda2 /media/windowsrecovery
```

---

### Post by Saghaulor on 2009-10-28
Once you've done that, you can do the following "Places"->"Computer"->"Filesystem"->"Media"->"windowsrecovery" and all your Windows files should be there.

Then you can copy and paste them to your flash drives.

---

### Post by Saghaulor on 2009-10-28
When you're done with backing up your files to your flash drive, make sure to unmount the partition before shutting down Ubuntu.

```
sudo umount /media/windowsrecovery
```

---

### Post by Saghaulor on 2009-10-28
Please post if this helped or not.

---

