---
title: "Newbie asks: What are the limitations of pendrive install?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by NUboon2Age on 2010-05-14
Total newbie question: 
I'm trying to play with Ubuntu 10.4 on a pendrive before installing it on a hard disk, but have been running into difficulties with getting a driver to work.  But to ask a question even more basic than that, are there any limitations to a pendrive install that I should be aware of, or does it work just as if I'd installed it to a (small) hard drive.  Obviously space is a limit, but for instance if I successfully use synaptic to install a package, should I be surprised if I reboot and don't see it there on the menu as it was before?  Also I don't see my browsing history in firefox.  Is there something funky about a pendrive install to cause this?

When trying to straighten out the driver problem I did an apt-get and config sequence where I ran out of room and some dpkg operations were interrupted... is this the likely culprit or is it something about a pendrive itself???

---

### Post by Paqman on 2010-05-14
How did you install? Did you run the normal Ubuntu installer and just install to the USB stick like you would to a hard drive? Or did you use the USB Startup Disk Creator? Or Unetbootin?

---

### Post by NUboon2Age on 2010-05-14
I used USB Startup Disk Creator.  I also have Unetbootin available.  Thank you for your help!

---

### Post by Paqman on 2010-05-14
Well, if you elected to devote some space on the drive for persistence, then you can install software and store files on there. If you didn't devote some space to persistence, then you've basically got a LiveCD, every time you reboot it will reset itself.

---

### Post by NUboon2Age on 2010-05-14
Ok,that's interesting.  The way it was worded I thought that it divided it into system space and other software and that the system space would include any updates that I installed so I gave most of it to that.  I gave a a half a gig to other programs.  So are you saying that the system space is not updatable?

---

### Post by NUboon2Age on 2010-05-14
To get the effect I'm looking for (so its just basically a small hard drive and not a 'live disk' that resets each time), how should I do it?

---

### Post by marshmallow1304 on 2010-05-14
> **NUboon2Age said:**
> To get the effect I'm looking for (so its just basically a small hard drive and not a 'live disk' that resets each time), how should I do it?

You could do one of these:

1) Using USB Startup Disk Creator, put the disc image on the USB drive, remembering to select "Stored in reserved extra space" and setting the slider all the way to the right.  AFAIK, the persistence file will be limited to 4 GB since the Startup Creator uses FAT32.  Technically, this won't be the same as a regular install, but it will be similar: you will be able to install programs and keep files.

2) Go through the installation procedure but select the USB drive instead of a regular hard drive.  You will need to have another installation medium (e.g. CD or another USB drive from which to start the install).  There are two things to mention here: a) Be very careful when selecting the installation drive and selecting whether to install the bootloader so as to avoid installing anything to an internal hard drive.  It is advisable to disconnect all drives other than the USB drive.  b) Avoid creating a swap partition on the USB drive.  Swap, if put into use, involves a lot of read and write operations, which will be detrimental to the lifespan of the USB drive.

---

### Post by NUboon2Age on 2010-05-14
So it sounds like Startup Disk Creator (and Unetbootin) always create a system space that won't be upgradeable?  So then if I want an upgradeable system I have to do  #2?

Also if I do #2 is it okay to do it from a live CD or will it do something to my internal HD (which I can't very well disconnect as you advise)?  I don't want to mess with my internal HD yet.  The whole idea was to experiment on a pen drive so I could see if it would work and then if so I  can install to my internal HD

---

### Post by NUboon2Age on 2010-05-14
In USB Disk creator the choice that I guess Marshmallow1304 was talking about says 
"When starting up from this disk, documents and settings will be *Stored in reserve space".  

So I guess it doesn't allow me to not have of having any updatable system that won't just go back to the way it was before the changes I made.

Is Unetbootin the same in requiring this unchangeable space?  It's interface web site is terse and I can't figure out the answer to my question.  Your help is appreciated.

---

### Post by marshmallow1304 on 2010-05-14
To the best of my understanding, it works something like this.  The base image (you called it "system space") is read-only, as if it were on a CD.  The persistence file can hold anything on top of that.  This includes upgraded packages, newly installed packages, and user files.  The difference is that when upgrading, packages will not be "replaced" in the "system space" but loaded from the persistence file instead.  As a warning, this can fill up the persistence file quickly.

As far as I know, Unetbootin does not support the creation of persistence space.


If you go with number 2, it is OK to do it with a live CD.  If you're not comfortable with opening your computer and disconnecting the hard drive, you will just have to be very careful not to install to the internal hard drive.  Go slowly, review all the advanced options, and make sure that you don't install the boot loader to your internal drive.

---

### Post by NUboon2Age on 2010-05-14
> **marshmallow1304 said:**
> To the best of my understanding, it works something like this.  The base image (you called it "system space") is read-only, as if it were on a CD.  The persistence file can hold anything on top of that.  This includes upgraded packages, newly installed packages, and user files.  The difference is that when upgrading, packages will not be "replaced" in the "system space" but loaded from the persistence file instead.  As a warning, this can fill up the persistence file quickly.

Okay please be patient with me and tell me if I'm understanding this correctly:  There is what you called the 'base image' (the original .iso image?) which is read only  and then there's the 'persistence' space which would include any drivers added or upgrades and is read/write.  

**BUT** if the base image remains unchanged/unchangeable, won't it continue to boot in the same condition even if you've added other things and upgraded, so that even if the additions are in the persistence space they won't be used on the new boot up?

If so I guess the only way to do what I want to do is option #2?

---

### Post by NUboon2Age on 2010-05-14
Okay, here's an update on what I've learned so far: 

Edit 1.: Totally edited to reflect my current knowledge

1. In order to have an updateable system and one that you can save things to the pen drive you need create some "persistent space" otherwise it will be just like a 'LiveCD'  On **Startup Disk Creator**, creating this space is simple -- just move the slider to create this space (usually you'd want to set it all the way to the right.)  **Unetbootin** is more complicated and requires you add some persistence files to the drive, and apparently you only have three choices of the size of persistence space... see [this link]("https://help.ubuntu.com/community/LiveCD/Persistence") for more on this.  [**MultiBoot**]("http://liveusb.info/dotclear/") is really cool and allows you all kinds of options, and mostly seems to work. :-)

2. Yes you can do a regular install to a pendrive where it will treat the drive as just a regular (small) hard drive **BUT BIG CAUTION** if you use a regular install then you must physically disconnect the internal hard drive or {insert other possible methods here such as possibly if you unmount the internal drive} or **Grub WILL reconfigure itself to overwrite** any previous version of Grub on your hardrive (possibly missing OSs that are there) and to **assume that the pendrive is always plugged in**.  So if you remove the pendrive prior to bootup, Grub will fail and you'll arrive at the Grub recovery prompt.

I did the install from the opening option liveCD without unplugging the internal drive hoping that the installer would be discerning enough to allow me to treat the pendrive alone without involving the internal drive.  No such luck.  It gave me the impression it would, but actually no.  It might have worked the way I wanted it to if I'd proceeded to the 'try Ubuntu' option, unmounted the internal hard drive and then run the install from the desktop, but I only thought this up later.  Lesson learned.  

Future lesson to learn: resetting Grub.  In the meantime I'm back to the original problem: getting my wireless Broadcom b43 driver to work under 10.4.  I'm stuck for the time being having to have the pendrive stuck in, but I'll suffer with that for the time being, because as soon as I figure out have to make it work I'll just reinstall over everything on the internal disk with 10.4 which was my original goal (the pendrive is just an way to figure out how to get wireless working before committing to it.

---

### Post by C.S.Cameron on 2010-05-14
You should be able to use a persistent install to get your wireless working.
You should be able to use your persistent install to fix grub on your internal drive.

---

### Post by NUboon2Age on 2010-05-14
> **C.S.Cameron said:**
> You should be able to use a persistent install to get your wireless working.

I wish I could figure out how.  Using Startup Disk Creator it seems like any fixes I make are not incorporated in the next boot up.  Any tips?

> You should be able to use your persistent install to fix grub on your internal drive.

Any tips?

---

### Post by C.S.Cameron on 2010-05-15
What version of grub is on your desktop? here is a link to restoring the old version.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Following is an alternate method of making an usb-greator install persistent:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by NUboon2Age on 2010-05-16
> **C.S.Cameron said:**
> What version of grub is on your desktop? here is a link to restoring the old version.

 Please post that link again.  Thank you for all your good info.

---

### Post by NUboon2Age on 2010-05-16
> **C.S.Cameron said:**
> What version of grub is on your desktop? here is a link to restoring the old version.


C.S. Cameron wrote in private message:

Oops:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

