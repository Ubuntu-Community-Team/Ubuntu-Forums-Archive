---
title: "Slow USB 2 speeds"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by Fidelio on 2009-09-24
Hi all, I just bought a Storagebird 200gb external USB2 drive. Formatted it to Ext3, did the chown thing and set about trying to use it.
I'm getting write speeds of about 1.3 MB/s.
I'm running 8.10, and my usb ports are definitely USB 2. Any idea why so slow?
Thanks

---

### Post by ibuclaw on 2009-09-24
Try using Ext2 - or Ext4.

Ext3 isn't very equipped for External Hard Disk Drives from my experience.

Regards
Iain

---

### Post by khelben1979 on 2009-09-24
The question is whether your Linux system can handle your usb port as USB 2. Have you tried to connect other usb units as well?

In some cases you can solve this by getting another Linux kernel or by activating kernel modules from your present kernel.

---

### Post by LowSky on 2009-09-24
> **khelben1979 said:**
> The question is whether your Linux system can handle your usb port as USB 2. Have you tried to connect other usb units as well?

In some cases you can solve this by getting another Linux kernel or by activating kernel modules from your present kernel.

Linux sucks for USB2, Supposedly USB3 is going to work without a hitch but I'm holding my breath. It doesn't matter the distro  USB2 Speeds are impossible to achieve. Try transferring a 1GB or larger  file to a FAT32, NTFS, EXT2, or EXT3 formatted USB flash drive or External USB hard drive and they all take much longer than any Windows XP or Windows 7 machine I have ever used, or even fail to complete in many cases. I have no idea how a person is supposed to put a movie onto a media player or a storage device since write speeds seem to never work.

And don't say it the hardware, its not. The same results over multiple machines with Intel, AMD, and Nvidia chipsets all spanning a few different years, and usb drives from corsair, kingston, even generic fail. My External hard drives where WD and Maxtor, both were incredibly slow.



This topic comes up every few months and no one has a good fix, sorry if I seem angry but mass storage over USB is required, its the default of the portable hard drive market.

---

### Post by khelben1979 on 2009-09-24
> **LowSky said:**
> Linux sucks for USB2, Supposedly USB3 is going to work without a hitch but I'm holding my breath. It doesn't matter the distro  USB2 Speeds are impossible to achieve.

I strongly disagree about that USB 2 speed is impossible, but... I suspect that you might have correct regarding usb harddrives, I have no experience myself on this so I really can't tell. 

When it comes to speed with USB pen drives the speed has been faster on my Linux system than Windows, actually. So your argument for USB 2 speed isn't valid for these kinds of things.

I really hope that you're wrong regarding usb harddrives as well, that it's just about how the kernel is compiled or something like that, or maybe some "evil combination" ?

---

### Post by QIII on 2009-09-24
I have heard (* heard, *mind you) that Windows 7 has similar issues.

I have also heard (again *heard, *mind you) that the initial current load to spin up the platters while using one USB cable may cause the device to incorrectly report the transfer speed back to the OS, so you get stuck with that.

(I have gotten great transfer speed with thumb drives...)

A possible solution -- which I cannot confirm -- would be to use two USB cables then unmount and remount the drive.

I don't have the hardware to test this.

It might be something to check out and let us know.

---

### Post by Fidelio on 2009-10-11
Well I hope the definitive answer is not just that 'linux sucks for USB 2.0'
I'll have a go at trying EXT4.

---

### Post by mikechant on 2009-10-12
> Linux sucks for USB2

I bought the cheapest 500Gb USB2 drive I could find for backups and I have never had a single failure (including when doing an initial full backup of about 300Gb of data). Also, I timed one of these large backups and ended up with a speed of about 400Mbit/Sec - the theorectical maximum for USB 2 is 480, and I understand that under any OS it's not generally possible to get much more than 400. So Linux doesn't always suck for USB 2.

I'm sure your problems are very frustrating, but there must be something about your (multiple) PCs, drives etc. that's different to mine and other satified Linux/external USB drive users.

As far as comparing transfer speeds between Linux and Windows, I hope you are taking into account that depending how you are doing the copy operation, Windows may report that it has finished the transfer long before it actually finishes writng the data and so give a transfer time/rate which bears no relation to reality!

---

### Post by mikechant on 2009-10-12
Back to the original post:

> I'm getting write speeds of about 1.3 MB/s.

I.e. about 10 Mbits/Sec.

This is very suspicious. The theoretical maximum for USB v1 is 12Mbit/Sec so it looks as if your device is running as USB 1 rather than 2.
I have read that some machines that claim to be USB 2 actually have some USB 2 ports (typically at the back) and then some more at the front which are attached via a USB 1 hub. However, if the exact same port is giving USB 2 speed in Windows and USB 1 in Ubuntu, then that's not the problem. So I suppose it could be QIII's issue above or another drive detection issue.
If it was a power-over-USB spinup issue then that could work differently in Windows if Windows (say) waited longer for spinup to complete. Does the drive run off USB power or has it got its own power supply?

---

### Post by Arup on 2009-10-12
Two things work out quite well here, one is turning off legacy usb mode in BIOS and other is getting a powered USB hub, seems its a voltage issue which makes hdds spin at 1.1 rate. I had the same issue on some PCs till I added a powered hub, now the file transfer flies be it mp3 player, camera or usb hdd.

---

### Post by CharlesA on 2009-10-12
> **LowSky said:**
> Linux sucks for USB2,

It does? Funny, I'm backing stuff up to an external USB drive and it transfers at around 30MB/sec (which is 240ish mbps). That's the usual transfer rate for the device that I use, be it on Windows or Linux.

For reference, the drive I used isn't powered by USB, it's got it's own power pack.

> **Fidelio said:**
> Well I hope the definitive answer is not just that 'linux sucks for USB 2.0'
I'll have a go at trying EXT4.

The transfer rate seems close to the old USB 1.1 standard, rathe then USB 2.0. Could try a different port (one that you know is USB 2.0) or check the bios to ensure you have USB 2.0 enabled.

---

### Post by Hated On Mostly on 2009-10-12
There is definitely a bug when it comes to USB 2 transfers and Linux on some hardware. The bug appears to have been around for years across every distribution.

[http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688)

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/88746?comments=all](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/88746?comments=all)

The word is that kernel 2.6.31, which can be found in 9.10 Karmic Koala, cures this problem for some. So far in my tests it seems to have fixed the slow USB problem for me. I would wait until the final release of 9.10 Karmic Koala if your USB is slow and see if things are better.

---

### Post by Cuco3 on 2009-12-13
I'm also experiencing less than acceptable USB2 speeds. I'm gonna try disabling Legacy USB (which is enabled) but I hope I don't have to format as EXT2 or EXT4 (using EXT3 atm). That would suck since the transfers would take about 6 hours to put on another disk, another 20-30 minutes to format the 1TB USB HDD to EXT4, then another 3 hours to transfer the databack (assuming the speeds at least double).

I'm also skepticle about using EXT4. How safe and reliable is it? I plant to use the drive to back up my data and my clients Windows drives. Can't have anything going wrong.

---

### Post by mikechant on 2009-12-14
> I'm also experiencing less than acceptable USB2 speeds. I'm gonna try disabling Legacy USB (which is enabled) but I hope I don't have to format as EXT2 or EXT4 (using EXT3 atm).

The question is, what speed are you getting and is it less than or equal to USB 1.1 speed, or greater than USB1.1 speed?

> I'm also skepticle about using EXT4. How safe and reliable is it? I plant to use the drive to back up my data and my clients Windows drives. Can't have anything going wrong.

If you're really getting unacceptably low speeds with ext3, ext4 won't help. It's faster, but not that much faster (25%-50% depending on access pattern in my experience).
Also, if you're using it for business purposes, personally I'd stick to ext3 for maybe another year. There are still a few reports of corruption although I get the impression they may well be special/minority cases. 

Personally, for home use I'm just about getting to the point where I'll trust it for all my data (currently using it for root filesystems), but I'll take a final full ext3 backup on an external drive before I switch over (and then keep that for a couple of years).

---

### Post by nhasian on 2010-01-12
its a bug in the kernel.  see my post here:

[http://ubuntuforums.org/showpost.php?p=8653721&postcount=29](http://ubuntuforums.org/showpost.php?p=8653721&postcount=29)

---

### Post by Bartender on 2010-01-13
So, nhasian, are you saying that it's likely to be fixed in the next kernel upgrade?  

I was reaching for the 9.04 install CD when I read your post...;)

---

### Post by nhasian on 2010-01-15
I don't know if it will change from whats in the PPA mainline now when Lucid Lynx 10.04 comes out, but so far using he newer kernels in there work for me.  I thought there was something wrong with my pendrive for a long time but it turns out changing the kernel speeds up my usb file transfers quite a bit.

> **Bartender said:**
> So, nhasian, are you saying that it's likely to be fixed in the next kernel upgrade?  

I was reaching for the 9.04 install CD when I read your post...;)

---

