---
title: "Hardware or Software issue?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-11
I just noticed that I cannot get my CD-station to open. I mean the actual physical slide-out-tray won't slide out. Could it be drivers or could it be that the darn thing just broke up within last 10 hours.(Yeah, it was last used approximately 10h ago to install Ubuntu 9.10 to this very computer and it worked like charm.)

The thing doesn't even have the tiny hole thing with which you could "force" it open.

What to do?

---

### Post by jimingkui on 2010-02-11
did you try linux command **eject -t** to open it.

---

### Post by umoreno_89 on 2010-02-11
Please post what is the make and model of the CD drive.

Before blaming software, just check if the cables from the computer are properly
secured to the drive.

If the CD drive doesn't open, then it could be possibly be the hardware or
the software. From the info you posted, i say it's the software because it the 
CD-drive might be new and not be supported by ubuntu.

---

### Post by lockalidiot on 2010-02-11
> **jimingkui said:**
> did you try linux command **eject -t** to open it.
 
Not yet. I intend to when I get back home.
 
 
 
@umoreno_89:
I'll check the make and model also when I get back home. The computer is new Packard Bell iXtreme.

---

### Post by darkmire on 2010-02-11
> **lockalidiot said:**
> I just noticed that I cannot get my CD-station to open. I mean the actual physical slide-out-tray won't slide out. Could it be drivers or could it be that the darn thing just broke up within last 10 hours.(Yeah, it was last used approximately 10h ago to install Ubuntu 9.10 to this very computer and it worked like charm.)

The thing doesn't even have the tiny hole thing with which you could "force" it open.

What to do?

Usually CDs won't eject if for some reason the system is keeping it mounted and thinking that the drive is in use.   If you are only conversant with the GUI then right click on the desktop icon or on the drive entry in Places in Nautilus and you there have an Eject command. There's also an Eject button next to the CD drive entry in Nautilus as well. You may find that you need to click Unmount first which should terminate anything still running.

---

### Post by patchwork on 2010-02-11
If you can safely reboot, try the physical eject button on the drive during bios initialization (before the grub menu or before the kernel loads).  If the tray opens, it is almost certainly a software issue.  If it doesn't, it is almost certainly not.

---

### Post by LowSky on 2010-02-11
Actually the newest version of Ubuntu will not allow the disk to eject if the button on the drive is pressed. You must issue the command from the OS

Some options inclued

right click on the drive icon and choose eject

Using a media keyboard's eject button (mine has one, maybe yours does too).

openig a terminal windows and using the eject -t command

or eject the CD during the computer's boot from the drives button.

---

### Post by durand on 2010-02-11
The newest version also tells you which programs are currently using the drive, which is nice..

---

### Post by lockalidiot on 2010-02-12
Sorry for my absence. Had some issues with panels, boot and stuff... Those are solved and I'm running like a dream again.
So, update to the situation: I can't open it from GUI (via rightclick->eject) except with "gksudo nautilus". I can open it from terminal with and without "sudo" using command "eject", the "eject -t" didn't work. I don't have a media-eject button on keyboard. I can open the tray by "Alt+F2" type:"eject" and I was able to make an application launch button on my panel which runs the command "eject" and it works fine.
The make of my CD/DVD stasion is LabelFlash*(I suppose?? Thats what reads on it*). Model: no idea I'll have to dig up my manuals to check this out....

EDIT: Still haven't got around digging up the manuals.. But I have a Packard Bell iXtreme.. Where I can view the Hardware "details"? (with not too many details like with the "lshw" command?)

---

### Post by skymera on 2010-02-12
Try unplugging the power cable from the CD drive, then plugging it back in.
Oh, make sure the PC is switched off.

Mine has a problem where i sometimes needs rto remove, replace the cable

---

### Post by lockalidiot on 2010-02-12
Thanks for the tip. I might do that this weekend, if I can gather the nerve to go messing with the insides of the box.. It's a bit out of my area of expertice...

---

### Post by audiomick on 2010-02-12
Hi.
Opening the case is not too scary if you stay sensible. The main thing to watch out for is static electricity. I can't remember very well, but I think the power points in Finland are similar to those in Germany aren't they? Where you can touch the earth pin in the socket? If so, do that before you touch anything inside the computer, to discharge yourself just to be sure.

The plugs on the back of the CD drive and hard drives can be fiddly. You often need a bit of "gentle forcefulness" to get them out. They generally can only be plugged back in the right way around, so there is little danger of getting one the wrong way.

There is no need for you to be touching the boards for anything, so avoid that.

When you are putting it back together, have a look at how the cables are lying last thing before you close the case. I have, for instance, one cable that always wants to lie across the heat sink for the GPU, which isn't that sensible...

And **pull out the power cable _before_ you undo any screws!!!**

---

### Post by mp2010 on 2010-02-12
I am a new user of Ubantu and wants to install new software which is related to Autocad designing.Please help me solving this issue.

---

