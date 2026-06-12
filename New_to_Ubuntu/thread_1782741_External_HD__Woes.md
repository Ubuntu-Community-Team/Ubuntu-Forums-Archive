---
title: "External HD  Woes"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by scirwine on 2011-06-15
I'm running Natty on a slightly older Dell Dimension B110 desktop I inherited... I increased increased its RAM, DBAN'ed the hard drive, and installed ubuntu. Had some trouble at first, toying with xubuntu and kubuntu, and couldn't overwrite on top of the other (even though the installers seemed to suggest this as possible)...so I could find my only solution in giving the HD a hard wipe-down in the process. 

Somehow, along the way, I screwed up big time and also DBAN'd my Simpletech 320gb External, and about 200gb of music. Very sad, but I'm over it. since then, the Simpletech has been spotty at best, and usually just horrible. At first it wouldn't mount automatically, but rather sporadically in the first 30 minutes after power-up or not at all. I took it to a laptop running Windows XP and was able to successfully mount the hard drive, and reformat it with FAT. STILL, I was having problems after, though I was getting sporadic recognition again with Natty Narwhal. So, one of the times it mounted, I formatted it AGAIN. This time, I thought, it should work. It did!

The next step in my process of rebuilding my music collection was to copy some from the Windows Laptop. This time the laptop wouldn't recognize it, but I was able to reclaim music off my old ipod with idump. idump didn't strike me as being very linux-friendly, so I used it on the laptop with xp insteadm and since it couldn't recognize my newly formatted (still FAT) external hard drive, I used my GF's Westrern Digital external (which through all this, as a benchmark of consistency has been mounting fine wherever it was needed) as what I expected to be a weirdly necessary step. Transfer files via iDump to WD on XP laptop, then transfer files from WD to Simple tech using my Dell Dimension, running Ubuntu. 

Now Ubuntu (AGAIN) can't recognize, mount, or otherwise interact at all with my simpletech. the last time I formatted it, WITH UBUNTU, it worked fine for severall days, receiving and transferring files, etc, just as it should have. The computer was shut down and restarted many times. The only catch - I hadn't unplugged it from the USB port at all yet. as soon as I did, it has not worked with any computer thus far.

I pretty new to this. I've probably done some stupid stuff already, but I've also sifted through a fair number of forums, and have not found any solutions (or even similar problems) yet.

I've tried   "lsusb"
and "sudo lsusb -v"

and a few other basic "recommended" solutions on finding out if the computer is interacting at all with the simpletech. it certainly seems not to be.  The Drive itself has 2 lights that normally come on - a red one that stays solid when it's receiving power, and a blue one that blinks as it manages data. Blue doesn't flash at all any more, though it did as little as 2 days ago.

I'm about ready to toss it, but I can't bring myself to do it if there may be a solution out there. I think there should be. I've owned it for just over 2 years now, never any problems until this mess.

Any help would be great, I'm at my wits' end.

---

### Post by decoherence on 2011-06-15
Howdy! So, let me just collate the facts to see if I understand this right.

1. Your GF's external drive always works properly in Windows or Ubuntu
2. lsusb does not list your simpletech drive (or at least, not consistently)
3. the simpletech drive has a FAT filesystem that you have (occasionally) been able to access and work with using Ubuntu since the last time you reformatted it
4. The red power light always comes on when you plug it in.

I'm going to assume that all other things are equal... that is, you're using the same USB cable with your GF's drive as with yours, you are using the same USB port, etc. Do whatever you can to eliminate 'low tech' failures like bad ports or cables.

When you plug a USB drive in, UDEV is what takes care of it. You can see what UDEV is doing by running

```
sudo udevadm monitor
```

you should run this BEFORE you plug in the drive. Once it is running, plug in a drive and you should get some output. Try it with your GF's first so you can see what things are supposed to look like when they work.

Unplug her drive and plug in yours (taking care to click the eject button if it mounted, of course. you don't want to kill the thing and have a pissed off GF) and see if you get any output. If you do, and the thing STILL doesn't work, please post the output here.

Another thing you can try is to plug in your drive and run the Disk Utility program. If it recognizes your drive, click on it and check the SMART status in the upper right area of the window. This is the drive's internal diagnostic information -- usually if there is a problem with SMART Ubuntu will automatically let you know when you plug the drive in but hey, it's worth a shot.

Good luck! The good news is that hard drives are cheap these days! Remember, the only good hard drive is a backed up hard drive! ;)

---

### Post by scirwine on 2011-06-16
Here's my update, and thanks for what I assume was helpful info.  within twelve hours of posting this, through no particular action of my own (just normal turning on and off of the computer and ignoring the drives) my simpletech has become a recognized, fully-functioning feature again. I have successfully removed it, reconnected it, and still with ease of use and mounting.

But I've had enough trouble already, that I don't trust this magical fix to be permanent. I will try the monitor next, just to see what it tells me, but - I guess in this case, perhaps you can't fix it if it's not broken. Thanks again.

---

