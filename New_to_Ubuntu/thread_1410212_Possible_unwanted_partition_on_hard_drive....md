---
title: "Possible unwanted partition on hard drive..."
date: 2010-02-18
forum: New to Ubuntu
---

### Post by SilverSilk on 2010-02-18
Hello everyone!  This is my first post after downloading the new version of Ubuntu.  I made a persistent usb thumb drive boot-up from the download, thinking  that it would be a completely separate environment from my hard drive.   However, I think in the process of installing Ubuntu, I think it created  a permanent partition on my hard drive.  Even though the usb thumb  drive is removed from the usb port, everytime I reboot I get a dark  screen with a menu on it.  This is exactly what it says:

                                                     Gnu Grub Version  1.97 beta 4

                              Ubuntu, Linux 2.6.31-14-generic
                              Ubuntu, Linux 2.6.31-14-recovery mode
                              Memory Test (memtest 86t)
                              Memory Test (memtest 86t),serial console  115200
                              Windows 7 (loader) (on/dev/sda1)
                              Windows 7 (loader) (on/dev/sda2)
                              Windows Vista (loader) (on/dev/sda3)

I have been choosing the first Windows 7 option....I hit enter....and it  boots up to Windows 7.  It seems to be running okay.
My questions are:

                              Can you explain what this menu is?
                              Did I somehow screw up my computer?
                              How do I remove this menu so it starts  right up to Windows 7?
                              If there is a partition there, how do I  remove it from my hard drive?

Hope I'm not being a pain in the butt.  Thank you for  your consideration.

---

### Post by bodhi.zazen on 2010-02-18
Sounds as if you installed grub on your hard drive.

Boot Ubuntu and either open gparted and post a screen shot or post the output of:

```
fdisk -l
```

---

### Post by mikewhatever on 2010-02-18
> **SilverSilk said:**
> 
.......
Can you explain what this menu is?

These are all the boot options available.

> Did I somehow screw up my computer?

Unlikely.

> How do I remove this menu so it starts  right up to Windows 7?


So you are done with Ubuntu and don't want to boot it anymore?

In Ubuntu, open Applications->Accessories->Terminal and post the output of the following command:

sudo fdisk -l

---

### Post by undecim on 2010-02-18
> **mikewhatever said:**
> So you are done with Ubuntu and don't want to boot it anymore?
I think he just wants to use Ubuntu from his thumb drive, and only boot it when he chooses to via the BIOS.

> **bodhi.zazen said:**
> Sounds as if you installed grub on your hard drive.

Boot Ubuntu and either open gparted and post a screen shot or post the output of:

```
fdisk -l
```

bodhi.zazen is correct.

But if this menu shows up even when you do not have the thumb drive in when you turn on the computer, then you've installed Ubuntu to your hard drive (Otherwise you would get a "sh:grub>" prompt when your thumb drive isn't in)

If you want just a persistent thumb drive, you can use the USB Startup Disk creator from your Ubuntu system before removing it from your hard drive. 

If your thumb drive is larger than 4GB though, you will only be able to use about 4GB persistent of storage. On the other hand, any space that isn't reserved for persistent storage can be used to store files from other computers, so you should decide if you want to install Ubuntu to the thumb drive, or use a persistent isntall.

In my experience the persistent install has less problems when used on several different computers. The regular install is good if you are only ever going to use it on one computer.

Once you have a proper USB installation, you can use that to put your hard drive back like it was.

---

### Post by mikewhatever on 2010-02-21
> **undecim said:**
> I think he just wants to use Ubuntu from his thumb drive, and only boot it when he chooses to via the BIOS.


Guess we'll never know.:)

---

### Post by SilverSilk on 2010-02-23
> **mikewhatever said:**
> Guess we'll never know.:)

Oh yes...all you guys WILL know!  First off, please accept my apology for not answering all of you sooner.  I was checking, but it seems that all these kinds replies came at once.
To mikewhatever...you are correct, Windows is not Linux.  I sure know that now. I really didn't know Linux existed til recently.  I became interested in a certain software that was based in Linux so I began to do a little research.  Came across a suggestion stating that the best way to learn Linux is by learning Ubuntu. I was very surprised to see how wonderful this new operating system seemed to be.  I was just about to teach somehow how to use Windows, then decided to turn them on to Ubuntu instead!  Never new about the "open source" concept.  And no, I an not giving up on Ubuntu...I know a good thing when I see it.:D
Thank you for taking the time to answer my questions.  I do appreciate it!

To undecim...you are correct! I just wanted it on a usb thumb drive so I could take it with me and let others know about it.  And yes, only choose to use it in the Bios when I wanted to.  At the time, I didn't know anything about it.  Just wanted to test it out and if I didn't like, I could just delete it. Since then, I have read the Ubuntu Reference Guide (just once).
Thank you very much for your detailed explaination...I definitely will follow your directions
The usb thumb drive I'm using is 8GB, from what I was told would be the minimum storage for an ISO cd download.  Since I still have that on the thumb drive, would I still have to go to USB Startup disk creator and make another copy?

Also, shoutout to  **bodhi.zazen...thank very much for the answer too.  I appreciated it.**

---

### Post by bodhi.zazen on 2010-02-23
IMO, for what you want, I suggest unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Or you can use the USB creator.

[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

---

### Post by undecim on 2010-02-23
> **SilverSilk said:**
> The usb thumb drive I'm using is 8GB, from what I was told would be the minimum storage for an ISO cd download.  Since I still have that on the thumb drive, would I still have to go to USB Startup disk creator and make another copy?

According to your first post you are presented with the Grub menu even if your thumb drive is no plugged in. This is correct? If so, that indicates that Grub is reading config files from your Ubuntu installation, which must be on your hard drive, rather than your thumb drive.

So without your thumb drive plugged in, choose "Ubuntu, Linux 2.6.31-14-generic" from the menu and log into Ubuntu. Put your thumb drive in, and go to System -> Administration -> USB Startup Disk Creator

Select your thumb drive, and find the ISO file on your hard drive (if you have the ISO file on your windows partition, it will likely be somewhere in the "Users" or "Documents and Settings" folder on your windows partition, which is usually called something similar "50.0 GB Volume" in Ubuntu). You may need to format the drive, so copy everything on it you don't want to lose somewhere else if that is the case. Next select the "Stored in reserved extra space" option, and slide the slider to the left to reserve space for the persistent install. And finally, press the "Make Startup Disk" button.

Once that is done, test your install by booting from your thumb drive (you may have to edit some bios settings, but I'm sure you've read all about booting thumb drives by now)

Also, just FYI: You should be using an i386 iso for the live USB drive, even if you have a 64-bit computer, because i386 will run on any computer, but amd64 will only run on 64-bit computers.

Once you have all that done, there is a topic on removing Ubuntu here: [http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959) Take a look at post #2 there for details. Though instead of using partition magic as he suggests, you could use your new live USB and run GParted from System -> Admin -> GParted.

If you have any questions on any of this, don't hesitate to ask.

---

### Post by egalvan on 2010-02-23
> **undecim said:**
> 

If your thumb drive is larger than 4GB though, **you will only be able to use about 4GB persistent **of storage.


Where does this limit come from?

---

### Post by SilverSilk on 2010-02-23
> **undecim said:**
> According to your first post you are presented with the Grub menu even if your thumb drive is no plugged in. This is correct? If so, that indicates that Grub is reading config files from your Ubuntu installation, which must be on your hard drive, rather than your thumb drive.

So without your thumb drive plugged in, choose "Ubuntu, Linux 2.6.31-14-generic" from the menu and log into Ubuntu. Put your thumb drive in, and go to System -> Administration -> USB Startup Disk Creator

Select your thumb drive, and find the ISO file on your hard drive (if you have the ISO file on your windows partition, it will likely be somewhere in the "Users" or "Documents and Settings" folder on your windows partition, which is usually called something similar "50.0 GB Volume" in Ubuntu). You may need to format the drive, so copy everything on it you don't want to lose somewhere else if that is the case. Next select the "Stored in reserved extra space" option, and slide the slider to the left to reserve space for the persistent install. And finally, press the "Make Startup Disk" button.

Once that is done, test your install by booting from your thumb drive (you may have to edit some bios settings, but I'm sure you've read all about booting thumb drives by now)

Also, just FYI: You should be using an i386 iso for the live USB drive, even if you have a 64-bit computer, because i386 will run on any computer, but amd64 will only run on 64-bit computers.

Once you have all that done, there is a topic on removing Ubuntu here: [http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959) Take a look at post #2 there for details. Though instead of using partition magic as he suggests, you could use your new live USB and run GParted from System -> Admin -> GParted.

If you have any questions on any of this, don't hesitate to ask.

Wow.. you are too kind!  Can't tell you how much this means to someone just starting out.  A million thanks!! I will follow your directions and tell you how things turned out. Take care my friend.

---

### Post by undecim on 2010-02-23
> **egalvan said:**
> Where does this limit come from?

It's because syslinux, which loads the live USB (similar to grub) uses the FAT32 filesystem, which has a maximum file size of 4GB.

The persistent storage is all in one file that the live USB treats like a drive (that way it can use file permissions and other goodies that FAT doesn't have)

This is done so that the drive is still compatible with Windows and Mac without reformatting. Should the user decide he doesn't want Ubuntu taking up all that space, he can just stick it in any computer, delete the files, and be on his way, or just delete the file with the persistent information and have a plain, non-persistent live USB, but with a little more free space.

There are ways to get around this. Most of them require some tinkering and break Windows/Mac compatibility. Of course, you could always just store files in the remaining space on the drive (especially files you would like to use on a Windows computer later)

---

### Post by SilverSilk on 2010-02-23
> **SilverSilk said:**
> Wow.. you are too kind!  Can't tell you how much this means to someone just starting out.  A million thanks!! I will follow your directions and tell you how things turned out. Take care my friend.

Your directions were great, but ran into some difficulty.  I'm using a SanDisk Cruzer 8GB usb thumb drive.  I formtated first before using it.  No space occupied.  I get to the " Make Start-up Disk " menu, found the iso download in the download section...entered it... and underneath it says:


Disk to Use:                  Capacity        Space
/deb/sdb                       7.5 GB

The device needs to be formatted for use.      FORMAT

Once I hit format prompt comes up and says:

"Unable to mount 8.0 GB Filesystem"

Once I click "OK" it says:

"There is not enough free space for this image"

The section "Make Start-up Disk" is greyed out.


The iso is only 690MB, so I'm not sure what's up? any thoughts Undecim? I know my 500GB hard drive is partitioned in half.  Could the Disk Maker be trying to copy half of my hard drive?

---

### Post by undecim on 2010-02-23
@SilverSilk: Try formatting it manually. Jut right click on the device from a file manager and make sure to choose "vfat" (or "fat" or "fat32"... whatever that particular dialog calls it) as the filesystem type. Then just use the creator again and you shouldn't have to format.

I'd be more specific, but I'm using a different desktop environment, so I can't check it myself.

Just make sure that you are doing this to your thumb drive, and not your windows partition - I've been careless and made a similar mistake before. It sucks

---

### Post by SilverSilk on 2010-02-24
> **undecim said:**
> @SilverSilk: Try formatting it manually. Jut right click on the device from a file manager and make sure to choose "vfat" (or "fat" or "fat32"... whatever that particular dialog calls it) as the filesystem type. Then just use the creator again and you shouldn't have to format.

I'd be more specific, but I'm using a different desktop environment, so I can't check it myself.

Just make sure that you are doing this to your thumb drive, and not your windows partition - I've been careless and made a similar mistake before. It sucks




Got it to a persistent thumb drive.  Well, haven't checked if it saved my last changes, but it did boot up fine from the bios section.  I guess it is not possible to set it up for one user with a username and password (or root powers) on the thumb drive...it seems that only can happen if you actually install it to the hard disk?  Ubuntu seems to run better from the hard disk than the usb thumb drive.I'm trying to decide if its better to use it from the hard drive or the thumb drive.  I'm not to thrilled about  all the extra space taken up by ubuntu partition.  About to read the post you suggested for removal from hard drive.

---

### Post by undecim on 2010-02-24
> **SilverSilk said:**
> I guess it is not possible to set it up for one user with a username and password (or root powers) on the thumb drive...it seems that only can happen if you actually install it to the hard disk?

The default user on the persistent install is "ubuntu", but you should be able to add your own user to a persistent install via System -> Admin -> Users and Groups, and then configure the login screen at System -> Admin -> Login Window to either automatically log that user in or to require a password.

---

### Post by SilverSilk on 2010-02-27
[QUOTE=undecim;8875008]The default user on the persistent install is "ubuntu", but you should be able to add your own user to a persistent install via System -> Admin -> Users and Groups, and then configure the login screen at System -> Admin -> Login Window to either automatically log that user in or to require a password.[/QUOT

Undecim...Fantastic!  Everything worked out the way you said it would.  Great help and directions!  Persistant usb is just great!  Now I can show people what Ubuntu is about!

I read the removal post.  I actually love the Ubuntu operating system and I plan to keep for awhile. But because of my stupidity, I failed to make a back up copy of Window 7.  Sure would hate to pay for a copy...maybe customer service could help since I just bought the computer 6 weeks ago.  But...after restoring back from Windows cd you said to use my new Ubuntu live usb boot-up thumb drive and go into Systems-Administration-Gparted?
I don't see "Gparted" among the choices.  Could it be called something else?

Also in the post...did the guy who removed the partition from his hard drive mean to say he "only" used his live Ubuntu cd to change or remove the partition? Or did he use that in addition to the Window XP live cd?

---

### Post by undecim on 2010-02-28
> **SilverSilk said:**
> I read the removal post.  I actually love the Ubuntu operating system and I plan to keep for awhile. But because of my stupidity, I failed to make a back up copy of Window 7.  Sure would hate to pay for a copy...maybe customer service could help since I just bought the computer 6 weeks ago.  But...after restoring back from Windows cd you said to use my new Ubuntu live usb boot-up thumb drive and go into Systems-Administration-Gparted?
I don't see "Gparted" among the choices.  Could it be called something else?

Also in the post...did the guy who removed the partition from his hard drive mean to say he "only" used his live Ubuntu cd to change or remove the partition? Or did he use that in addition to the Window XP live cd?

Did you do something to bork your Windows install? If you can still get to it from the boot menu, then it's still fine. The only thing we are "fixing" is the Ubuntu partition that you didn't want on it.

Removing an Ubuntu installation consists of two steps:

1: Removing the Ubuntu Partitions 

2: Restoring the windows MBR so that windows can boot without the help of Ubuntu's GRuB bootload. (usually done with a windows recovery disk)

These can actually be done from either Ubuntu or Windows if you have to correct tools, but it's easiest (and safest) to use GParted from the live CD to remove the partition. And the Windows recovery disk to fix the Windows MBR.

If you can't find GParted, you can boot back into windows and use the windows partition manager to delete your Ubuntu partition and expand your windows partition back to its original size.

After that, you will need your windows recovery disk to restore Windows MBR.

> **SilverSilk said:**
> Now I can show people what Ubuntu is aboutAlways good to hear that we have another voice out there! Just do yourself and everyone else a favor and remember the golden rule of spreading the word: [Don't preach, mention]("http://ubuntuforums.org/showthread.php?t=865750")

---

### Post by SilverSilk on 2010-02-28
> **undecim said:**
> Did you do something to bork your Windows install? If you can still get to it from the boot menu, then it's still fine. The only thing we are "fixing" is the Ubuntu partition that you didn't want on it.

Removing an Ubuntu installation consists of two steps:

1: Removing the Ubuntu Partitions 

2: Restoring the windows MBR so that windows can boot without the help of Ubuntu's GRuB bootload. (usually done with a windows recovery disk)

These can actually be done from either Ubuntu or Windows if you have to correct tools, but it's easiest (and safest) to use GParted from the live CD to remove the partition. And the Windows recovery disk to fix the Windows MBR.

If you can't find GParted, you can boot back into windows and use the windows partition manager to delete your Ubuntu partition and expand your windows partition back to its original size.

After that, you will need your windows recovery disk to restore Windows MBR.

Always good to hear that we have another voice out there! Just do yourself and everyone else a favor and remember the golden rule of spreading the word: [Don't preach, mention]("http://ubuntuforums.org/showthread.php?t=865750")

Hello undecim!
Thanks again.  I found out that I have a recovery cd on my hard drive (Windows 7 side) that I can burn to a DVD, then use it to recover Windows 7.  According to the customer service guy, once I put in the recovery DVD it will delete everything on the hard drive including Ubuntu and the partition.  Does this guy know what he is talking about?  Am I wrong in assuming that you're trying to tell me I need both the Windows7 recovery dvd AND the live usb to delete the Ubuntu partition?  Are you saying that the Windows 7 recovery dvd will NOT remove the Ubuntu partition?  I'm a little slow so please don't get annoyed...I'm trying to make extra sure I understand.:D

As far as not being able to find "GParted", I was referring to Ubuntu on my hard drive now...not the live usb I just made.  I have not checked the live usb yet for the GParted section in Systems.....but I cannot find it in the System>Administration section on my computer now.  Is GParted only in the live cd or live usb?


Also, I read your blog and really liked it.  I was not sure if you  would be back here so I sent you an email to ask you another question on  a different subject.  Was that okay?

---

### Post by undecim on 2010-02-28
GParted must be run from the Live USB. It's not on the default Ubuntu installation, and will cause problems if you try to delete the partition while running an OS from it.

You will need to use the Windows recovery CD to fix the MBR. For a bit more detail, look at #7 at [http://articles.techrepublic.com.com/5100-10878_11-6031733.html](http://articles.techrepublic.com.com/5100-10878_11-6031733.html) (I would describe it myself, but it's been a long time since I've had to do this, so I'm a little fuzzy on the details)

If you can get into your current windows install, you should be able to remove Ubuntu from there using Windows built-in partition manager, or by using GParted from the Live USB.

You don't have to reinstall Windows for this, and the tech support was probably telling you this either because it's much quicker to explain, or because they don't know how to fix this. Just make sure you only use "fixmbr", and not some automated recovery.

---

### Post by SilverSilk on 2010-03-01
> **undecim said:**
> GParted must be run from the Live USB. It's not on the default Ubuntu installation, and will cause problems if you try to delete the partition while running an OS from it.

You will need to use the Windows recovery CD to fix the MBR. For a bit more detail, look at #7 at [http://articles.techrepublic.com.com/5100-10878_11-6031733.html](http://articles.techrepublic.com.com/5100-10878_11-6031733.html) (I would describe it myself, but it's been a long time since I've had to do this, so I'm a little fuzzy on the details)

If you can get into your current windows install, you should be able to remove Ubuntu from there using Windows built-in partition manager, or by using GParted from the Live USB.

You don't have to reinstall Windows for this, and the tech support was probably telling you this either because it's much quicker to explain, or because they don't know how to fix this. Just make sure you only use "fixmbr", and not some automated recovery.

Great to see you again!  Man, I have been reading my butt off!  It finally became apparent to me that GParted is a software that can partition hard drives...and iso that is downloaded to a cd or usb.  And you are correct...as usual...about deleting the partition first.  I read that could prevent me from booting up leading to a black screen...grub is first in line for booting up.  

I search for the "Windows Partition Manager" in my start section (in Windows 7)..I think I found it. However, it does not have instructions, that I can see, to delete partitions. No worries...Gparted will do.  I found out that there are 3 dvds (each 4.7GB) that I have to use to restore Windows 7.  Don't know if the MBR is one or all 3 dvds, but yeah the guy said to use all three.

However, you're saying that Gparted will simply give me the ability to resize Windows 7 back to the original size or any size I want after I reset the MBR...right? And I think you're also saying that by returning the partition back to the original size will automatically erase all of Ubuntu? 

I must say, I like Ubuntu better than Windows.  And I see how having 2 Operating Systems is a great advantage.  Thanks for schooling me.  Also, thanks to you, I've got 3 people trying Ubuntu right now!!

Now Undecim...I've got another question about Ubuntu but a different subject.  I don't know if this place is appropiate to talk about since its a different topic.  Its about aircrack-ng in Ubuntu...boy could I use your suggestions!!!

---

### Post by undecim on 2010-03-01
@SilverSilk: You should be able to use fixmbr from any recovery cd with a recovery console (the first one?). When you resize the partitions, you will need to delete Ubuntu's partitions first, then resize your Windows partition.

Or, you could just leave it like it is. Like you said, there are advantages to having more than one OS (for example, if one of them goes south). It's your computer, so you can make that decision.

If you find you need a little more space on either side, GParted can fix that (although make sure your backups are up to date, becuase a if something goes wrong, it can mess up your partitions)

As for using aircrack-ng and its related utilities on Ubuntu, you will probably need to patch your wireless drivers to capture or inject any WiFi packets (and even then some wireless cards don't support that kind of low-level manipulation). It's probably easiest just to get a copy of BackTrack 4 and use it, because it has all those patches built in.

I don't use it much though, so it would probably be best to start a new topic about so that someone with more experience with it can find you.

And of course, make sure you have permission to be doing whatever it is you're doing with it. If you are trying to prove to someone that they need to upgrade from WEP to WPA, that's good and all, but make sure you have their okay to do so.

---

### Post by SilverSilk on 2010-03-01
Thanks! I now have a clear picture on that topic...now I can pass that along.  People will now have very little reason NOT to try Ubuntu when I show it to them.  To a newcomer, the term "partitioning the hard drive" is scary! Knowing how to change it back will encourage people to try it.  Also, this OS has instruction booklets that are pretty good for new people.

---

