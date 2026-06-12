---
title: "install ubuntu on a USB pen drive?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Zundap on 2009-11-30
Hi, could any one please advise me, is it possible to install ubuntu on to a USB pen drive? as in, is it possible to use the USB pen drive like a hard drive?

I hope this is not a silly question. Thanks for any replies.

---

### Post by howefield on 2009-11-30
Yes, which version of Ubuntu are you using, most of the fairly recent ones have an option under, System > Administration > USB Startup Disk Creator.

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

---

### Post by Geoff918 on 2009-11-30
Howefield's right. I use that (I unfortunately had a DVD-RW drive fail on one of my laptops, so this is how I've found is easiest).

Another outstanding source of information is the following:

[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

I've followed a few of those through. Honestly, when it comes to Ubuntu it's easiest with the USB creator.

---

### Post by Zundap on 2009-11-30
> **howefield said:**
> Yes, which version of Ubuntu are you using, most of the fairly recent ones have an option under, System > Administration > USB Startup Disk Creator.

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Thanks for the reply howefield, I am presently running ubuntu 9.04, but i am intending to try 9.10 on a Pen drive, would one be anymore suitable than the other to run on the pen drive? Thanks.

---

### Post by Zundap on 2009-11-30
> **Geoff918 said:**
> Howefield's right. I use that (I unfortunately had a DVD-RW drive fail on one of my laptops, so this is how I've found is easiest).

Another outstanding source of information is the following:

[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

I've followed a few of those through. Honestly, when it comes to Ubuntu it's easiest with the USB creator.


Thanks for the reply Geoff918, and thanks for the link, ile go take a look at that right now, thanks.

---

### Post by howefield on 2009-11-30
> **Zundap said:**
> ...i am intending to try 9.10 on a Pen drive, would one be anymore suitable than the other to run on the pen drive? Thanks.

Not in terms of running from a pen drive. 

As long as 9.10 runs on your hardware, that's the one I'd use, but then, it works a charm for me. It's really your choice.

---

### Post by Zundap on 2009-11-30
> **howefield said:**
> Not in terms of running from a pen drive. 

As long as 9.10 runs on your hardware, that's the one I'd use, but then, it works a charm for me. It's really your choice.


Thanks howefield, But If 9.04 works ok with my hard ware, which it does, then does it not follow that 9.10 will also?

And if i might ask, would i need to disable the original harddrive before using ubuntu on the pen drive?  thanks again.

---

### Post by efflandt on 2009-11-30
9.10 works for many, but has changes that work for most, but some have issues with.  The advantage of installing live/install iso on bootable USB stick is that you can try it, and if it does not work for you, you can try something else.  I have tried a bunch from bootable USB (even from 2 GB microSD on a USB card reader).  An operating system the size of your little fingernail.  Although, I would avoid using a Sandisk Cruzer USB stick with U3 because the U3 in firmware seems to double boot time (and shows up as an additional cdrom).

There is **USB Startup Disk Creator** that you can use from the Administration menu to install any Ubuntu related install iso to bootable USB.  You just need to figure out if you PC can boot to USB and how.  Typically if your PC is capable of that you can either set to boot from the USB device before hard drive in CMOS setup (the splash screen during boot before anything else loads) or you press a key during that time to boot from alternate source (sometimes Esc or F12).

2 GB works well enough for bootable live/install iso with persistent data.  You can do a regular install to USB (preferably 8 GB or larger, 4 GB may not leave you much available free space).  But then you have to remember to use the **Advanced** button near the end to put grub on the USB device (instead of default to your main hard drive).  I shrunk the vfat partition on a WD Passport USB portable hard drive (with gparted-live CD) and installed Ubuntu with grub on that.

---

### Post by lotuscarsltd52 on 2009-11-30
> **Geoff918 said:**
> Howefield's right. I use that (I unfortunately had a DVD-RW drive fail on one of my laptops, so this is how I've found is easiest).

Another outstanding source of information is the following:

[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

I've followed a few of those through. Honestly, when it comes to Ubuntu it's easiest with the USB creator.

I tried this myself but it's not working.

When I try performing step 3 from the website ([**http://tiny.cc/Yr0RV**]("http://tiny.cc/Yr0RV")) and run the START.bat file it tells me to place the ISO into the USB Installer folder (***which I do***) and then to press any key when I am finished...only for it to give me the same prompt again as though I didn't do that in the first place ("place ISO in folder...press any key...").

Here's the catch: step 2 tells me to download a torrent and then download Ubuntu 9.10 ISO using my favorite torrent client...*but wait...*the file I downloaded *is the ISO file*. What's this about downloading some torrent?

Am I doing something wrong here?

---

### Post by howefield on 2009-12-01
> **Zundap said:**
> But If 9.04 works ok with my hard ware, which it does, then does it not follow that 9.10 will also?

One would hope so, but it is not always the case. I'd say you are likely to have no issues with 9.10 but there is no guarantee. If it doesn't work, then simply use 9.04 on the pen drive, all you've lost is a little time

> would i need to disable the original harddrive before using ubuntu on the pen drive?

No, just set your computer to boot from the pendrive. Some computers will need to be set in bios to do this, others have a key (eg, F12) that you can use during the boot process to select the boot device.

---

### Post by Zundap on 2009-12-01
Thanks very much indeed howefield, some of what you have said has gone over my head, but most of what you have said i can comprehend, and the little bit i dont understand, i will pick up as i go along. I cant wait to get started. Where we would we all be with out people like your self?  I just hope that i can get as good as you and then help some else in the future.  Thanks again for everything.

---

### Post by bodhi.zazen on 2009-12-01
> **Zundap said:**
> Thanks very much indeed howefield, some of what you have said has gone over my head, but most of what you have said i can comprehend, and the little bit i dont understand, i will pick up as i go along. I cant wait to get started. Where we would we all be with out people like your self?  I just hope that i can get as good as you and then help some else in the future.  Thanks again for everything.

We were all beginners once and most of us are still learning, the rabbit hole is indeed deep.

---

### Post by jrrader on 2009-12-01
Most posts seem to be suggesting the usb startup disk method, which essentially turns your usb into the live CD.  I prefer to just install directly to the USB from the live CD.  This way I can change what programs are installed, add drivers, save changes - all the things one normally does with their operating system.  

Doing this is very simple:
1. Boot from Live CD.
2. Click Install Ubuntu
3. Choose your partition manually - select your usb drive
4. On screen 8 of the install program click advanced and direct the boot loader to your usb stick.  By default it will go to your first hard drive.  You do not want it there.

I have done this with 9.04, crunchbang (9.04), and Mint 8. All of them 32 bit. My brother-in-law upgraded his usb from 9.04 to 9.10 and he says it still works fine.

---

### Post by Zundap on 2009-12-13
Thanks for the reply jrrader, ile give that a go also.  :D

---

