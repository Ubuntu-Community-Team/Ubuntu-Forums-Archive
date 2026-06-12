---
title: "Help creating bootable USB"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Feline Monstrosity on 2009-12-12
Hi. I'm trying to install the Ubuntu Netbook Remix 9.10 on my new netbook using a 1GB USB disk. I downloaded the .iso and used Unetbootin to make the USB disk a bootable drive. I then restarted the computer and set the BIOS settings to boot from the USB disk, but I'm presented with the error: "Please remove disk or other media. Press any key to restart."
What's gone wrong and how can I make it work?

---

### Post by arochester on 2009-12-12
1) Check how your USB stick is formatted. It should be fat or fat16. NTFS is no good.

2) My experience is that Unetbootin is good at putting things ON but it is not good at cleaning them OFF.  Make sure there is nothing else on the stick.

---

### Post by magic8ball on 2009-12-12
Hi,

I don't know if you came across this page or not:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Among other things, they have a section for "Cannot Boot the Computer from USB?" that might help you.  Good Luck.

- Chuck

---

### Post by Feline Monstrosity on 2009-12-17
@arochester: I tried reformatting it to FAT and trying again and the same thing happened.

@magic8ball: I installed PLoP bootloader and tried to use it to boot from the USB stick and I got the following error:

> xo
Error loading operating system.

Perhaps the ISO is faulty so I'm going to try redownloading it. Any other suggestions? (Just so you know I have a Samsung N130)

Thanks for your help guys!

---

### Post by magic8ball on 2009-12-18
Hi,

I'm sorry that I don't have any specific solutions, but here is some more info that I've come across that might help you:

[http://ubuntuforums.org/showthread.php?t=1306277](http://ubuntuforums.org/showthread.php?t=1306277)

This isn't the exact issue that you're having, but maybe it is related???  They talk about an option  (choosing "discarded on shutdown, unless you save them elsewhwere") for reserved space for documents and settings on the USB drive (I guess this is making a non-persistent install, but that should be OK since you just want to install from USB to netbook and not run from USB).  I don't know if you have a similar option during your USB creation process...

- Chuck

---

### Post by celticbhoy on 2009-12-18
What OS are you using to create the USB stick?

---

### Post by Feline Monstrosity on 2009-12-19
I downloaded it from this page: [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
The ISO is called "ubuntu-9.10-netbook-remix-i386". I haven't actually checked if my architecture is i386 I just assumed it was the right file because there were no other options on the download page.

EDIT: Oh, and I'm using Windows XP. (I misunderstood the question)

---

### Post by ScottinSoCal on 2009-12-19
This may be an assumption on my part, but are you trying to boot from a USB stick that just has the ISO file copied onto it? That's the way I'm reading what you've written. If so, I don't think that will work. I created a boot USB stick, and it expanded the files and put them in a file structure. 

I'm afraid I don't know what the utility is named, but I got to it from System\Administration\USB Startup Disk Creator. That program asks me for the location of the ISO file, then copies all the files I need from the ISO to the USB stick. It took me a few tries to realize I had to delete the partition on thumb drive, reformat it as FAT32, then point to the location as the install spot, but I eventually worked it out. Boots right up and works great.

---

### Post by magic8ball on 2009-12-19
Hi,

ScottinSoCal's method is an alternative to using Unetbootin as you already tried.  You'll need to be running Ubuntu to use the USB Startup Disk Creator.  If you have access to another computer with a CD drive, you can download/burn the 9.10 desktop .iso to make a bootable CD.  Then if you boot that computer from the CD and choose the option to try Ubuntu without installing, you can follow the instructions in Scott's message.  This is also the place where you would use the "discarded on shutdown, unless you save them elsewhwere" option that I mentioned earlier.

- Chuck

---

### Post by Feline Monstrosity on 2009-12-20
I now have access to a computer running Ubuntu, which is very slow and can't burn CDs. I also have access to a faster computer that can burn CDs but it's a Mac so I wouldn't want to bother to try to boot it from an Ubuntu CD.

I'll carry on trying things...

---

### Post by Feline Monstrosity on 2009-12-21
I borrowed my brother's pen drive and the install worked this time. Thanks for your help! (Is there a way to change this to "solved"?)

---

### Post by vze326ff1 on 2009-12-21
Download the ubuntu iso file then download a installing software from here [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by magic8ball on 2009-12-22
Hi,

I'm glad that you got this working.  Was it just a matter of doing your original Unetbootin install with a new pen drive?  Just curious.

To mark as "solved" - from the thread tools menu at the top, choose "Mark this thread as solved".

- Chuck

---

