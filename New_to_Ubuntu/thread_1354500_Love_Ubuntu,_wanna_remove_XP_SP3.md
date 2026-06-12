---
title: "Love Ubuntu, wanna remove XP SP3"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by kitcarson61 on 2009-12-13
How do I go about completely wiping out Windows and all associated MS products on my machine and devoting all of it to Ubuntu?      Or, where can I find this info?
     OK, go easy on me.  I'm not only a newbie, but, having NO CLI experience, a complete GUI kind of guy.  I've been trying out Ubuntu more due to philosophical reasons than due to any real dissatisfaction with XP.  I just really can't stand monopolies and what they do to progress in general.
     So far, I've been more than pleased with Ubuntu 9.10 (installed via WUBI) and find myself RARELY booting up XP.  I'm conviced that it's time to get rid of Windows and all of the associated MS mess.  That is, unless someone out there can think of a good reason not to switch entirely to a Linux system.
     I'm sure I'll spend another month or so using Ubuntu only, just to be _absolutely_ sure, but would like to find out what it's gonna take to remove MS completely first.  I'm one of those people who look into and think about things a long while before I take any action.  And that action is usually taken just before all of the needed info comes in.  I don't want to do that this time.
Thanks in advance to any and all who might respond.
Trevor
TB

---

### Post by Redache on 2009-12-13
You'll need to burn a Live CD to disk and install Ubuntu using the live CD installer rather than WUBI. There is no way to uninstall XP and have WUBI as a standalone that I know of ( I would assume this would be very difficult if not impossible considering the way WUBI Works.) Once you install Ubuntu with the default settings it should reformat your Hard Disk and leave you with only Ubuntu installed.

---

### Post by jbrown96 on 2009-12-13
There's not a great way to remove XP if you have installed via Wubi. Basically, you are going to need to burn the Ubuntu disk (or put it on a flash drive with unetbootin -- available in Ubuntu and Windows) and do a clean installation. Basically, you need to backup your data (your home folder) and get a find the programs that you have installed. Then do a clean installation and replace your data and programs. 

One thing that I would highly recommend when you do a clean install is to use a separate partition for /home in the future. / needs 10GB at most, so set the rest for /home. If you have questions about that, don't hesitate to post them.

---

### Post by kitcarson61 on 2009-12-14
> **Redache said:**
> You'll need to burn a Live CD to disk and install Ubuntu using the live CD installer rather than WUBI. There is no way to uninstall XP and have WUBI as a standalone that I know of ( I would assume this would be very difficult if not impossible considering the way WUBI Works.) Once you install Ubuntu with the default settings it should reformat your Hard Disk and leave you with only Ubuntu installed.
Wow, that was fast!!!
Thanks very much.  
Is it really that easy?

---

### Post by kitcarson61 on 2009-12-14
> **jbrown96 said:**
> There's not a great way to remove XP if you have installed via Wubi. Basically, you are going to need to burn the Ubuntu disk (or put it on a flash drive with unetbootin -- available in Ubuntu and Windows) and do a clean installation. Basically, you need to backup your data (your home folder) and get a find the programs that you have installed. Then do a clean installation and replace your data and programs. 

One thing that I would highly recommend when you do a clean install is to use a separate partition for /home in the future. / needs 10GB at most, so set the rest for /home. If you have questions about that, don't hesitate to post them.
Thank you so much for the FAST response.
All docs, pics, personal info, etc., has already been saved to my wife's laptop, so that's not a problem.  Thank you for the reminder.  As for the / and /home partitions, I'll take your word for it since I have no idea what they are.
Again, thanks for the quick response.

---

### Post by SPazzo on 2009-12-14
> **kitcarson61 said:**
> Wow, that was fast!!!
Thanks very much.  
Is it really that easy?

It's very easy.  Read this page:  [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)  It provides links to all the pages on how to install Ubuntu.  I'd suggest reading them *before *you try to install it.

---

### Post by Redache on 2009-12-14
/ is the root folder(or partition) that stores all of the System Files. If you separate / and /home then if your system dies and you need to reinstall your /home data is preserved. 

/home is where your user data is stored (your home folder) and also contains config files for most of the software that you use (stuff like Firefox configs and .bashrc and so on).

You can also go further and have a /boot but it's not necessary to go that far.

---

### Post by kitcarson61 on 2009-12-14
> **Redache said:**
> / is the root folder(or partition) that stores all of the System Files. If you separate / and /home then if your system dies and you need to reinstall your /home data is preserved. 

/home is where your user data is stored (your home folder) and also contains config files for most of the software that you use (stuff like Firefox configs and .bashrc and so on).

You can also go further and have a /boot but it's not necessary to go that far.
And these are options that will come up during a new and complete installation?

---

### Post by lisati on 2009-12-14
I'd recommend making a set of recovery disks for your machine if you haven't already done so. My Compaq (HP) desktop (XP) and Toshiba laptop (Vista) both came with software to help in the process.

*** Appreciative blurb begins ***
I can appreciate people being frustrated with XP SP3 - I had an "adjectives deleted" series of moments with it yesterday before I twigged that there might be a hardware problem at play - clues included a BSOD mentioning a pagefault while running a non-destructive system recovery, BIOS not always recognizing all the RAM in my machine, BIOS getting stuck (sometimes beeping and sometimes not, mad dash to Google to get the meaning) and a half-remembered error message from a [Lubuntu]("http://en.wikipedia.org/wiki/Lubuntu") live CD
*** end of blurb ****

---

### Post by Redache on 2009-12-14
> And these are options that will come up during a new and complete installation?


It's something you have to do manually I'm afraid. In the Partition part of the Installer it will ask you whether you want to install Ubuntu to the whole of the Drive (which won't separate partitions) or to Manually Configure. If you select Manually Configure then you can specify how your partitions should be set up.

You do this by specifying a size (so / should be say 15gb, Swap should be 2GB*this is subjective to how much ram your system actually has* and /home would be the rest).

It'll ask you to put in the size of the partition and then the mount point, which is either / or /home. For Swap you would set the size and choose swap from the FileSystem list. 

I'd recommend using Ext4 for / and /home as it's speed improvements are quite nice.

---

### Post by The_Pirate_King on 2009-12-14
> **kitcarson61 said:**
> And these are options that will come up during a new and complete installation?
Not necessarily, I would not worry about that stuff until later.  Just burn a live CD and install from that in order to get a full-time Ubuntu install.  I recommend selecting "Use entire disc" when prompted to choose what part of the disc to use, because that will erase XP and install Ubuntu in one fell swoop.  
Actually, if you want to keep most of your WUBI settings, you can copy the "home" folder to a thumb drive, then paste it into the root file system on your new install, replacing the "home" folder on the new install, that should allow you to keep most of your Firefox, IM, and other data so that it will automatically get things set up the way they were on WUBI.

---

### Post by kitcarson61 on 2009-12-14
Thanks to all for the responses.  I really am so appreciative of them all.

Oh, absolutely!  I've got the originals that came with the computer, but will most assuredly set up new ones also.  Even though I'm hoping never to go back to anything with the Microshaft logo on it ever again.  
     I know, never say never, but it sure sounds good, don't it?

---

### Post by mosaic2s on 2009-12-14
Ubuntu is good - where it stops me from removing windows completely.

When I want to use banking websites - some of them ask for IE only. Or stock trading sw. or CAD files. For these, one can use virtualbox within ubuntu and manage quite well.

However, what stops me from removing other OS - i am unable to install some printers on 9.10 - they worked fine thru 8.04 LTS version.

So check all your hardwares like networking, scanners, cameras, phones, sound cards, printers etc. All these issues are best tried out by installing ubuntu. For which you have enough advise. And ubuntu is very user friendly for beginners. I stay with it for that reason.

All the best.

---

### Post by kitcarson61 on 2009-12-14
> **mosaic2s said:**
> Ubuntu is good - where it stops me from removing windows completely.

When I want to use banking websites - some of them ask for IE only. Or stock trading sw. or CAD files. For these, one can use virtualbox within ubuntu and manage quite well.

However, what stops me from removing other OS - i am unable to install some printers on 9.10 - they worked fine thru 8.04 LTS version.

So check all your hardwares like networking, scanners, cameras, phones, sound cards, printers etc. All these issues are best tried out by installing ubuntu. For which you have enough advise. And ubuntu is very user friendly for beginners. I stay with it for that reason.

All the best.
Hadn't thought about the "other websites" issue.  So far, all that I've gone to have worked just fine, but I guess I'd better be pretty thorough checking that out.  
Another reason to procrastinate.
As for hardware, within two days of the first install I had downloaded from and to all the cameras, printed, scanned, card read, played music and videos, cds, dvds, networked into and out of the computers of both the boy and she-who-must-be-obeyed, checked the web cam, microphone, can't think of anything else.  Everything worked perfectly.  A couple of application downloads were needed, but...
I love it!  It works!!!

---

### Post by kitcarson61 on 2010-10-02
OK, so thanks again to all who contributed and helped with my decisions last December (2009).  It's been ten months now that I've been running Ubuntu 9.10 on this old pc and I've never known so much trouble free use from any computer!  OK, so occasionally I'll need some plugin or codec or new software, but this OS not only lets me know I need it, but will find one or more, suggest them and install with just a click or two.  For a program user and gui guy, this is wonderful.  I've now converted my wife's and son's computers to Ubuntu also.  She's running the netbook edition (UNR) and the boy's running 10.4 and Puppy.  Ya, I've been trying them all on for size and have yet to be disappointed with any of them.
Thanks again to all who've helped me and to all those out there volunteering their time to those of us who need the help.  Thanks for the help and the patience!

---

