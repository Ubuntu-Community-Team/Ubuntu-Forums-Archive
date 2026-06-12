---
title: "how do I make live usb memory stick"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by david senior on 2009-10-30
[SIZE=2]         I have a new Dell Inspiron Mini 10V and am having some problems (which I may come back to later) but, basically, I want to be in a position to re-install the original operating system (and try others). I have an installation DVD from Dell but would like to not have to buy an external DVD reader. I do have an old computer running Linux which can "burn" iso files to CD and can run the "dd" command in a terminal window to usb memory. Can I simply "dd" the DVD to a usb stick and boot from this? Also are ther other option?

Probably elementary stuff but if you could just direct me in the right direction...[/SIZE]

---

### Post by alphaniner on 2009-10-30
I think Ubuntu provides a tool but I've never used it.  I use [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by Hyporeal on 2009-10-30
You can do this in
System->Administration->USB Startup Disk Creator.

You can use this tool to make a startup USB disk out of either an existing compact disc or an .iso file.

---

### Post by frank cox on 2009-10-30
> **david senior said:**
> [SIZE=2]         I have a new Dell Inspiron Mini 10V and am having some problems (which I may come back to later) but, basically, I want to be in a position to re-install the original operating system (and try others). I have an installation DVD from Dell but would like to not have to buy an external DVD reader. I do have an old computer running Linux which can "burn" iso files to CD and can run the "dd" command in a terminal window to usb memory. Can I simply "dd" the DVD to a usb stick and boot from this? Also are ther other option?

Probably elementary stuff but if you could just direct me in the right direction...[/SIZE]

What do you mean by live? If all you want is to have the live cd on a stick go to system-administration -USB creator. If you want it to be persistent [to save files to it-add softweare etc,} just unplug your hard drives, boot of a live cd , plug in your USB stick and install just like it was any other drive. I am a complete newbie but I have done both of these with no problem.

---

### Post by humphreybc on 2009-10-31
> **frank cox said:**
> What do you mean by live? If all you want is to have the live cd on a stick go to system-administration -USB creator. If you want it to be persistent [to save files to it-add softweare etc,} just unplug your hard drives, boot of a live cd , plug in your USB stick and install just like it was any other drive. I am a complete newbie but I have done both of these with no problem.

I think he wants to burn the DELL dvd to a USB Pen Drive using Ubuntu - not create an Ubuntu LiveCD.

I'm not so sure this will work to be honest. I know that in the case of the Ubuntu iso files, the USB Creator tool doesn't just "burn" it directly to the pen drive, but has to do some other modifications to allow the computer to recognize it as a bootable file system.

---

### Post by david senior on 2009-10-31
Thanks for the replies so far.

What I basically need is to create a USB stick that will enable me to reinstall the the operating system in my Dell Inspiron Mini Notebook. I have the recovery DVD supplied with it and the recovery instructions say "use an external optical drive or any external storage device..", then describe how to set the bios to boot from this, then say "follow the instructions on the screen". I have an old desktop computer with a CD and a DVD drive, and USB slots, on which I can run "live disk" Linux versions such as Knoppix and Puppy. My idea was to use this transfer the recovery DVD to a USB stick.

From what has been said, I gather that it might not be as simple as creating an exact copy of the DVD on the USB stick since these devices may have different boot requirements, but that using the "create recovery USB" (or something like this) facility may get round this. I do not yet know if I have this available but will endevour to get it somehow (or an equivalent).

---

### Post by jrrader on 2009-10-31
Make an ISO image from the dvd:
[http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/)

Then use unetbootin to add the iso to a USB stick.

To boot from it you'll have to go into bios and change the boot order.  Usually your USB stick will be listed as a hard drive so if you look at something along the lines of "hard drive order" you'll be able to move the usb drive above the internal hard drive.

---

### Post by werecatomega on 2009-10-31
1. get iso file and usb
2. go to system/Administration/USB Startup Disk creator
3. select where the iso file is and have it burn to the usb
4. wait for it to finish :popcorn:

---

### Post by david senior on 2009-11-01
Many thanks to all - I now have a better understanding of the situation and plenty to try. This may take some time! so I will close the thread for now.

---

### Post by frank cox on 2009-11-29
> **humphreybc said:**
> I think he wants to burn the DELL dvd to a USB Pen Drive using Ubuntu - not create an Ubuntu LiveCD.

I'm not so sure this will work to be honest. I know that in the case of the Ubuntu iso files, the USB Creator tool doesn't just "burn" it directly to the pen drive, but has to do some other modifications to allow the computer to recognize it as a bootable file system.


I installed Ubuntu to  a memory stick and all I did was install it just like you would to a hard drive and it works fine.  It works better than using the program for doing it in Ubuntu.

Puppy is much faster though and if all it is for is to have an emergency boot or isolate yourself when using someone else's machine to check email it works fine.

---

