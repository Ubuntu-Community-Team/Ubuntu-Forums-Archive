---
title: "noob upgrade failed how do I reinstall old version??"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by aundapenner on 2010-05-05
I posted over in the install probs forum but only received one response ... now I can't even get to a login screen.
 
Short(ish) version: 
 
I attempted to upgrade yesterday to 10.4 and *right* after I clicked upgrade I thought to myself I shoulda backed up.  
 
I am on an Asus Eeeeeee
 
All was well, so I walked away.  Came back to a black screen.  Not sure if my netbook went into sleep mode (it usually doesn't) but pushing on keys didn't help.  
 
So I rebooted.  
 
Ugh.
 
Now I can't get into my computer at.all.
 
The most common message I get is:
 
fsck from util-linux-ng 2.17.2
/dev/sda1: clearn, # of files, # of blocks
udevd[2800]: specified user "usbmux" unknown <== who is usbmux???
 
* Starting AppArmor profiles
 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5 [ OK ]
 
Rather than invoking init scripts through /etc/init.d, use the service(8) utility , e.g. service S49console-setup start
 
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S49console-setup start: Unknown job: S49console-setup
 
* Speech-dispatcher configured for user sessions
*Starting Common Unix Printing System: cupsd [ OK ]
* PulseAudio configured for per-user sessions [ OK ]
*Checking battery state. . . [ OK ]
 
and then nothing.
 
nothing.
 
I use my netbook primarily for internet and pictures of my kiddoes.  I am not afraid to use code but don't know how.
 
Can someone please help????
 
Thank you!!!

---

### Post by Temposs on 2010-05-05
What I'd recommend is for you to make a LiveUSB and choose to try before installing. Then, open up your hard drive from there and back up all your important files to somewhere, maybe another usb drive or something.

Once you're sure everything is safe, then choose to do a fresh install. This is a more sure-fire way to have a working system than doing an upgrade, so I don't think you'll have the same problems as you had with the upgrade.

---

### Post by aundapenner on 2010-05-05
Okay.  I finally had a chance to try to create a liveusb.
 
Following the instructions on the upgrade notes [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
 
I typed in lsb_release -a
 
This is what I got:
 
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.04LTS
Release: 10.04
Codename: lucid
 
What does it mean that there are no LSB modules available?

---

### Post by Temposs on 2010-05-05
This is not what I said to do...

You are not going to be upgrading anything. You are going to do a fresh install after you backup your files. Have you backed up your important files yet?

---

### Post by aundapenner on 2010-05-05
Now I have created a LiveUSB with 10.4 and have "tricked" my eee into reading the usb.
 
I get the following message:
 
Could not find kernel image: linux
boot: 
 
????

---

### Post by aundapenner on 2010-05-05
Sorry, I was looking around and saw that as a command to figure out which version I was running ... 
 
Okay.
 
No, I haven't backed up my data because I don't know how to access it.  All I get is a black screen with white print that lets me enter commands but I don't even know how to see that my files are all there.

---

### Post by aundapenner on 2010-05-05
(fingerscrossed) I seem to be starting to run from the usb ... hopefully I can get in enough to see if my files survived, back them up then do a fresh install!!!

---

### Post by aundapenner on 2010-05-05
So if I am in but there are no files on my hard drive, is all lost???:-(

---

### Post by akand074 on 2010-05-05
> **aundapenner said:**
> So if I am in but there are no files on my hard drive, is all lost???:-(

Yes but it is unlikely that any of your data is lost, make sure to TRY WITHOUT INSTALLING, if you do install, then yes all will be lost. You want to boot into the Live USB (so you'll be booted into Ubuntu only through the USB/RAM without touching your hard disk). Then what you want to do is find all your important stuff and copy/paste them onto another external drive. Once you have everything saved, do a fresh install of Ubuntu.

---

### Post by aundapenner on 2010-05-05
Right now, I am running ONLY from the USB and there are no files, no pictures, no nothin'.
 
I have found a program called ubuntu-rescue-remix ... will this help me find my files?  and if so, can I run that from the same usb as the usb-running ubuntu, yes?

---

### Post by aundapenner on 2010-05-05
Duh.  I can connect to the internet from my netbook.  
 
the birds have begun singing (it's 5am now here) 
 
I have begun the rescue-remix onto my netbook (while running ubuntu from a usb)
 
please oh please work!!!

---

### Post by akand074 on 2010-05-06
> **aundapenner said:**
> Duh.  I can connect to the internet from my netbook.  
 
the birds have begun singing (it's 5am now here) 
 
I have begun the rescue-remix onto my netbook (while running ubuntu from a usb)
 
please oh please work!!!

Did it work? There are other ways to restore data, but when you were in the live USB did you mount the drive your data was in and looked there? If the partition still existed then it should still be there. Though if not you can always try to recreate them. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is a pretty good one I used it to recover my partitions. As well as all the data in them.

---

