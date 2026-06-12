---
title: "my vista drive is no longer recognised and seems it cant be repaired"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by daveyllennod on 2009-08-01
how do,

here's my situation,

I was recommended onto ubuntu yesterday, tried it for a few hours and thought it was great. so as i know little about software just the basics I got my friend to do it, one thing led to another and he couldnt finish the unmountin seting up of partitions or something to that effect so i was left to do it,

I assummed that I had had done it eventually, proceeded to install ubuntu, and when it came to the partition bit of the installation I clicked use free space rather than deleting windows as was the first option,

NOw, 

I cant access my files through ubuntu,

tried to boot vista and it said the drive needed to be repaired

I downloaded a repair file and booted it up and when it got to the part where i select the drive didnt come up on the list,

when i run ubuntu from disc i only get the option to format the vista drive, when i click information on it it says its unmounted despite that it says that it is mounted in the list of partitions

currently the vista partition is taking up 30.3 GiB of my 40GiB hardrive and basically i would be happy to delete it but i need the files in there first

so here are the questions

1. Can I get my files back?
2. If I install ubuntu with the option of delete windows will that erase my current ubuntu installation and basically start from scratch
3. does ubuntu have the necessary drivers to run my wireless card, keyboard, sound blah blah blah if it was to operate without vista on my system just incase at the moment vista is still playing a role or is it basically dead space having no input in the running of my laptop?

couple of points that have already been made to me before anyone suggests them as i dont want to waste anybodys time:

i cannot get onto safe mode, I do not have an installation disc for windows,

I need all the files on my computer as they are related to my business and a forthcoming event and basically disaster and alot of time wasted if i cannot get them back, plus university coursework due pretty soon aswell

If theres anybody who can let me know what to do I'd really appreciate it as this is getting a bit desperate now,

cheers
daveyllennod

---

### Post by f37u5g0d on 2009-08-01
This is a very loaded question.  Let's start from the beginning.  If ubuntu is reporting the windows vista takes up 30Gb of space then the data on that drive is recoverable.

Step 1:  Mount your windows partition.
Find some storage device (second HDD, USB key, etc) where you can copy all of your files to so that you don't have to worry about them during this installation.

Step 2: I suggest simply reinstalling ubuntu and using the entire disk.  It is the easiest way to install.  Make sure though that you have your data somewhere else.  This option WILL erase everything on the disk.

There are multiple ways to solve your problem.  Other people will probably post here and suggest other ways of doing it.  My suggestion is probably the simplest way to solve your issue but it might not be the best.

To answer your 1 2 3...
1: Yes you can get your files back.  Ubuntu is fully capable of reading the NTFS file system

2:If you are running the ubuntu installer then you are "starting from scratch"

3: Whatever hardware works / doesn't work on the live CD is going to be the same in the actual install.

---

### Post by daveyllennod on 2009-08-01
right,

that all sounds grand, it was basically my last resort and thanks for clearing that up

However,

mounting the vista is the main problem, i dont get the option to do so anywhere in ubuntu, ive tried adding the mounting drivers option to the taskbar and when I mount and dismount I can see where the files are supposed to be COMPUTER/USERS etc but the files contain nothing,

I've tried running the cd for ubuntu so I can edit partitions in the partition editor but again theres no option to mount or dismount but theres an option to format, again wiping the drive clean,

I can do the rest no bother and it will sort out the computer but the files are still inaccessible

davellennod

---

### Post by LookTJ on 2009-08-01
When you are in ubuntu.

Look for your vista partition in the output of:```
sudo fdisk -l
```Once you found it, Try doing a fsck:```
sudo fsck.ntfs /dev/sd**x**
```

---

### Post by SuaSwe on 2009-08-01
[[COLOR="BLUE"]This thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1228419") contains info about data recovery should you not be able to mount the drive for whatever reason. Good luck!

---

### Post by daveyllennod on 2009-08-01
i've tried tping in the code there or copy and paste rather as I dont seem to have that final symbol on my keyboard,

however When I do that it asks me for my password and when i try typing it, the terminal cuts me off saying sorry incorrect password attempt?

Is my terminal not working or is my password not set properly, i assume its the password I set when i first installed

daveyllennod
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7717579") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7717579")

---

### Post by NOTAGEEK on 2009-08-01
Password is case sensitive...

---

### Post by louieb on 2009-08-01
thats a lower case L at the end.
```
sudo fdisk -l
```

When entering your password nothing is displayed - thats the Unix/Linux way.
Just enter your user password and press enter.

---

### Post by LewRockwell on 2009-08-01
I think I'd be inclined to try a SuperGrubDisk and see what it comes up with

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

.

---

### Post by HiImTye on 2009-08-01
it sounds as though there's an invalid entry to fstab. I would download 'Storage Device Manager' from add/remove (main menu > add/remove..), select your vista partition and then set it to 'default'. Storage Device Manager will be in System > Administration once it's installed.

also, if an NTFS partition isn't shut down correctly (in windows), you will get an error message when trying to mount it. it should pop up a box if this is the case. if it does, click more information and it will tell you -the exact text- you should enter into a terminal to mount your partition.

---

### Post by HotShotDJ on 2009-08-01
> **f37u5g0d said:**
> I suggest simply reinstalling ubuntu and using the entire disk.  It is the easiest way to install.  Make sure though that you have your data somewhere else.  This option WILL erase everything on the disk.I tend to agree with this suggestion.  While dual-booting has its benefits, those benefits are rapidly decreasing.

I, too, need to keep Windows around for certain things regarding work and school.  Fortunately, my University provides staff and faculty with a free copy of Windows XP, MS Office, and various other software that we need, so running Windows costs me nothing more than a rather large bruise to my F/OSS principles.

I do not, however, dual-boot.  I use VirtualBox, which allows me to create a virtual machine to run WindowsXP on my preferred Ubuntu desktop (I have done this with Vista as well, but Vista is a RAM hog, and is very sluggish because I can only allocate 1G RAM to it on my sub-optimal 2 Gig laptop).  If your system hardware is sufficient (2G ram is sufficient -- 4G is optimal; A CPU that supports hardware virtualization would be optimal, but not necessary; and enough hard drive space to support a virtual drive -- remember, your virtual drive doesn't have to be much larger than 20 GIG (XP) or 30 GIG (Vista) because you can share your native linux folders, eliminating the need to keep your personal files and data on the virtual drive), that is what I would recommend that you do.  My system is sufficient -- 2G RAM, no hardware virtualization, 90G /home partition -- but by no means optimal.  Yet, I have been pleased with the results using VirtualBox to run Windows XP and Vista (ok.. I am not pleased with having to have Windows at all, but that has nothing to do with the performance of VirtualBox :neutral: )

IMPORTANT:  You must have the actual installation media for your Windows operating system in order to install it in VirtualBox.  Most "System Recovery" discs will NOT work. There may be a way around this limitation, involving a fresh hardware installation of Windows and using PartImage from a liveCD, but I have never tested this hypothesis, since I have never had a system that belongs to me available with a native installation of Windows on which to experiment.  But I have used PartImage liveCD's within VirtualBox to make images that were successfully restored within another VirtualBox VM.

One caveat:  If you are a "gamer," some games may give you problems in a virtualized environment.  OpenGL is well supported in VirtualBox, but Direct3D is still in the experimental stage (as of VirtualBox 3.0.2).  I've heard that while many games run well under VirtualBox, others are problematic.  You may need to do some experimentation to find out if VirtualBox will work for you.  Since I'm not a gamer, I can offer no further guidance on this issue.

---

### Post by lkraemer on 2009-08-02
davey,
Here is what I would try.

I'd suggest first getting your hands on a second hard drive, and use
Clonezilla to Backup the Drive to the second drive just in case
something goes wrong.  You can then do the testing on the imaged drive
to see if you can repair it, or recover what you need.  Just in case
something goes wrong, you will still have the original drive safe.
Or you could just image the Vista Partition to a backup drive as
this is the only information you are wanting to recover.

You might want to checkout [http://www.ubcd4win.com/](http://www.ubcd4win.com/)
I just ran across it after making this post.


1. Download the "Vista Boot CD" (for your version ...32 or 64 bit)
   by searching for it with Google.
   [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
   Burn the ISO IMAGE as Disk at Once (DAO) and at a SLOW speed. (I use K3B)

2. Try booting the Vista Boot CD, and let it repair the Vista install.
   If it should work, then you are back in business. If not go to
   #3 below.
 
3. If it doesn't work, I'd find another machine and download a copy of
   Supergrub and burn the ISO.
   [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
   Then boot the CD and see if SuperGrub will replace the Master Boot
   Record (MBR) of Vista.  Then see if Vista will boot.  If it doesn't
   boot yet, try #1 again, then go to step #4.
 
4. If Vista isn't booting by now, then I'm out of suggestions.

5. To recover your Vista files I'd try the following.
   Boot from a Ubuntu LiveCD.  Plug in a USB External Drive.  It should
   Mount. Use SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER
   to install Testdisk.  (This installs Testdisk & Photorec.)
   Run Testdisk to see if you can recover the files you need.
   If testdisk fails then I'd try Photorec.  (As a good test before
   you actually work with your Vista partition, plug in a USB Media
   reader, and insert a Media card from a Camera that you have erased 
   the Photo's from, and see if you can recover any of those files
   using Photorec. That way you will learn how the Photorec software
   works, and won't overwrite any of the files on the Vista Partition.)
   This answers your Question #1.

6. Once you have all of the files you need from Vista saved,
   and want to blow away Vista, just boot a LiveCD of Unbuntu, run
   Gparted, and delete all the partitions.  I typically also create new
   partitions and format them.  Then Boot the Ubuntu LiveCD and install
   Ubuntu.  I always run Gparted from the LiveCD and setup my partitions
   manually before starting the install.  Just my preference!
   This answers your Question #2.

7. If you get Ubuntu Version 9.04 or CrunchBang 9.04 most likely
   everything will work, including Wifi.....But, I like 8.04.3 LTS.
   If everything works on the LiveCD it should work on an install.   
   This answers Question #3.

Good Luck!

lkraemer

---

