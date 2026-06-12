---
title: "Windows on internal drive, Ubuntu on external"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by oldstutz on 2010-07-23
First of all, I've been reading through these forums and everyone seems very helpful. I was hoping someone could point me in the right direction.

Situation:

I have a laptop that runs Windows 7, and my goal is to be able to run Ubuntu off of an external hard drive (which is bootable), but have the option to run Windows 7 without needing the external hard drive to be connected. 

My Understanding/What I've Done:

Using my desktop (XP) and an external drive as practice, I've installed Ubuntu onto the external drive using a liveCD. With the ext. drive connected I get the nice Grub list giving me the option to load Ubuntu or XP--from this location both load and run smoothly. My problem arises when I want to load XP without having my external drive connected--it simply won't load. My understanding is you should disconnect the internal drive during the installation so the Windows MBR won't be overwritten. Is there a way that doesn't involve physically removing the internal hard drive? I'd prefer to not have to take apart my laptop.

Any help would be greatly appreciated! Also, I am new to Linux :D

---

### Post by matrixblue on 2010-07-23
Hey,

Can you post your current grub configuration found in "/boot/grub/grub.cfg" or "/boot/grub/menu.lst" if you're using an older version of Ubuntu?

It seems that grub has installed to the Master Boot Record on your internal drive.

What you will first need to do is use the Windows 7 DVD to run startup repair which will erase the MBR and replace it with the Windows one. After this you'll need to install grub to the MBR of your external drive without erasing the MBR on your external.

Most people recommend removing the internal drive because its the easiest method. After you install Ubuntu then you would just configure in your BIOS which hard drive to boot from. You can even set the external drive to higher priority so that Ubuntu boots automatically when you start the machine with the external drive plugged in.

The hard drives on most laptops are really easily removed.

However, if you REALLY don't want to go that route then you can install grub to the external drive by booting from a LiveCD then running 

sudo grub-install dev sdX

Where X is the drive letter for your external drive (it should be b if your internal is plugged in but its best to verify)

---

### Post by Golem XIV on 2010-07-23
What I did was something like this:
Connect external drive
Boot live CD
Install to external HD (VERY carfully since both internal and external are the same size).
# This is the critical part #
At the end of the installation (the last window) click on Advanced and set GRUB to boot from /sdb or whatever your external drive is

Go to BIOS, put external drive as 1st boot priority

Now to boot to windows, just turn off and/or unplug the external drive and turn on system.  To boot to Ubuntu, plug in and/or turn on external drive and turn on system.

---

### Post by oldstutz on 2010-07-23
Thank you very much for the feedback! I'm in the middle of trying to install, but this time dictating where the GRUB is installed. I'll let you know!

---

### Post by matrixblue on 2010-07-23
> **oldstutz said:**
> Thank you very much for the feedback! I'm in the middle of trying to install, but this time dictating where the GRUB is installed. I'll let you know!

You'll still want to use the Windows 7 startup repair to ensure that XP boots without the external plugged it. To be safe unplug the external when doing this.

---

### Post by oldstutz on 2010-07-23
Working perfectly thank you both!

---

