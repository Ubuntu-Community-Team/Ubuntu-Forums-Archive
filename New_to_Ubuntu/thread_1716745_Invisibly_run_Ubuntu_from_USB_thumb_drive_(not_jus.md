---
title: "Invisibly run Ubuntu from USB thumb drive (not just Live)"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by 0b3ron on 2011-03-28
Hi all, 

I just got a new laptop from work and I've noticed that I can make it boot from USB. Which means I could set it up with a dual-boot, but that would probably get me fired. 

Is there any way that I can just run my own Ubuntu OS from my USB stick without changing the computer's boot loader or local hard drive? I know I can run "Ubuntu Live" but I want to be able to install programs, store files, etc on the USB itself as though it were the systems primary drive while booted from USB.

If the USB drive isn't connected, I want the computer to boot into XP exactly like it does now.

Is this possible?

---

### Post by Vu1kan on 2011-03-28
It's completely possible.  When you build your live usb stick, simply build it with persistence.  This allocates blank space on the drive to software installs, documents, etc. Personally, i find unetbootin to have the easiest gui to navigate for this task, but there are plenty of other methods to achieve the same result.

---

### Post by Zanderist on 2011-03-28
Bring up the BIOS, and select which device to boot into.

---

### Post by Da_Gopherboy on 2011-03-28
Yep its one of the finer things with Ubuntu.  You can completely try out the OS without fear of being tracked, converting your system or any of the other negatives normally associated with this type of endevor.  I've got a 16gig USB thumb drive I picked up from a buddy and I keep it on my key chain so I always have a copy of my system to go.  Now with all of the positives with this, there is one thing to keep in mind.  Ubuntu will NOT be as fast running from a USB device with persistence as it would be via a normal installation.  That is about the extent of the limitations I've found, you can install packages, update, download, and make it all disappear with a quick pull of the wrist.

Hope you like Ubuntu like so many of us have.  For more information on how-to setup the Ubuntu you want for the USB check out the download section @ ubuntu.com.  Its got a whole walkthrough process for creating the drive your asking about.

-G

---

### Post by bodhi.zazen on 2011-03-28
> **0b3ron said:**
> Hi all, 

I just got a new laptop from work and I've noticed that I can make it boot from USB. Which means I could set it up with a dual-boot, but that would probably get me fired. 

It is possible, but it does not sound as if you should be doing this kind of thing with property that does not belong to you.

It should not be *that* difficult to buy your own machine, build one if you must ;)

---

### Post by 0b3ron on 2011-03-29
Woah. That's way cool! My laptop has an external SATA port. If I buy an external SATA drive and install Ubuntu Live on it with space for persistance, will I get a full speed Ubuntu system?

---

### Post by oldfred on 2011-03-29
If you have an external drive you do not want the installer version with persistence but a full install. But with a full install you have to be very careful to make sure grub's boot loader is installed to the external drive's MBR. It will want to default to sda which is usually the internal drive. You have to use manual partitioning.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

But as mentioned above, if it is not your computer you should not be messing with it. With Ubuntu you can see and screw up the windows install as Ubuntu does not hide the parts of windows that windows normally hides. Only mount your internal drive as read only if you must do this.

---

### Post by 0b3ron on 2011-03-29
Hey Oldfred, 

What if I use my own laptop to set up grub on the external drive's MBR to make sure nothing goes wrong during installation? Later when when I plug in the drive to the work laptop, can I make Ubuntu auto-unmount the internal HDD on the laptop so neither I nor Ubuntu will do anything to it?

Thanks kindly,

Tommy

---

### Post by oldfred on 2011-03-29
I think I know how for permanently mounted internal drives with fstab, but that will not work with a external drive as fstab will not see it all the time and give boot errors.

Ubuntu will automount it. You may be able to do a small script to auto umount it and hide it or mount read only, but I do not know details. It may be possible if you have unique labels on every partition so you script can work on labels.

---

### Post by QLee on 2011-03-29
@oldfred How about fstab with the option, noauto.

0b3ron, I agree with bodhi.zazen. Is this something you want to do on the company's computer? It is reasonable to expect that there is some company policy about using unapproved software on the company's equipment. (which you probably signed at some point in the hiring process, even if you didn't read it.) I suggest you get IT department approval in writing before trying it or you may end up even getting blamed for some problem that you didn't cause. What you propose shouldn't cause a problem but don't be convinced that the IT department won't notice.

---

