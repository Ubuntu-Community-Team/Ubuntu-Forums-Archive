---
title: "Oh this can't be good..."
date: 2010-09-03
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-03
I just installed Ubuntu yesterday on a brand new hard drive and was getting into it.  So, a few hours ago I started to notice something strange.  I would periodically get little blips in the system.  Nothing major, or so I thought.  Just a periodic black screen that lasted for a second or two.  It was usually fixed by a simply tap of the space bar.  However... I turned off my machine and came back to it about an hour ago.  I turned it on and I get the initial boot screen where you select what you want to boot, and then... nothing.  Zip.  Nada.  I have manually gone in and ensured that the proper drive was selected.  It starts the boot and the just goes black.  Odd, yes.  Ok, so that's not good, right?  So I threw in my Ubuntu Installation CD figuring I could try booting from that just to see if the HD was somehow defective.  Guess what?  The CD doesn't boot either.  Same thing a the hard drive.  I get about 9 seconds of the original Ubuntu purple screen and then just black.  So I cannot boot from the Ubuntu hard drive or the Ubuntu cd.  But... I slipped my old Vista HD back into the machine, and it booted up fine.  So it's not the machine.  It has to be something in the Linux, but I can't fathom how it would affect the CD, which has not been in the machine since I did the install.  Any thoughts?  Anyone?  Bueller?

---

### Post by davidmohammed on 2010-09-03
have you connected anything apart from the hard-drive recently for example new usb device?  Added a new PCI card?  New monitor?  Anything?

---

### Post by uRock on 2010-09-03
Throw the LiveCD back in and when the first purple screen comes up, hit the space bar. Once the menu comes up select to test the cd.

---

### Post by ubunwhat on 2010-09-03
Nothing new has been added.  In fact, the only change that I can think of was that maybe my iphone was plugged in earlier and now it isn't.  Aside from that, nothing.  The last thing I did was to install Wine, but I installed it from the App Store thing and it installed without a hitch so I doubt that is causing the problem.  Will now reboot again with the CD and try the spacebar deal.

---

### Post by warfacegod on 2010-09-03
It may not be the machine but it could be the HDD you used to install Ubuntu.

---

### Post by ubunwhat on 2010-09-03
Ok, so did the space bar deal on the CD.  Selected Check Disk and.... the screen went black and stayed black.  

Warface:  It seems very odd that both the CD and the new HDD would die simultaneously for no apparent reason.  Factor in that I can see the HDD in Vista when I attach it via USB, and that makes it even more unlikely.

---

### Post by uRock on 2010-09-03
If the test didn't work, then it sounds like the disk is bad and some how you got lucky with the first install.

---

### Post by ubunwhat on 2010-09-03
The disk being bad wouldn't explain the HDD issue.  I just don't see both A) being bad and B) going bad at exactly the same time C) the HDD showing as healthy when viewed from Vista.  I found a thread on this that talks about video drivers and doing some type of driver load from a command line, but I'm not getting a command line so I am a bit lost here.

---

### Post by jcolyn on 2010-09-03
From a good working computer go to [http://www.ptdd.com/manual2.htm](http://www.ptdd.com/manual2.htm) and download the CD version and burn it to a CD. Now place it in the tray of the suspect computer and see if it boots into super fdisk. If so you can check the disk from there.

You will get errors up front but answer no because it is reading the Linux partitions which do not line up with Windows partitions.

---

### Post by corrytonapple on 2010-09-03
> **ubunwhat said:**
> The disk being bad wouldn't explain the HDD issue.  I just don't see both A) being bad and B) going bad at exactly the same time C) the HDD showing as healthy when viewed from Vista.  I found a thread on this that talks about video drivers and doing some type of driver load from a command line, but I'm not getting a command line so I am a bit lost here.
There may not be an issue with the HDD. See, if the disc were bad, then while it was still young it was able to install the already corrupted Ubuntu system to the HDD. Then since the CD was bad, it passed the bad disc install to the HDD. Things like this happen often. Try reburning a CD.

---

### Post by Jerry N on 2010-09-03
I would suggest downloading a new Ubuntu ISO and burning it to a new CD.  Some people suggest burning a a very low speed although I have never had to resort to that unless (a)my CD burner is going bad [these things do fail quite often] or (b) I am using a very marginal CD.  Then boot this new CD on your computer and select "check the CD" from the menu.

Jerry

---

### Post by ubunwhat on 2010-09-03
Ok, so fdisk says the HDD is peachy keen.  It even congratulated me on having such a spiffy disk.  I really did not want to start completely over with Ubuntu, but that may be my only option at this.  Well, that or install Windows 7 on the drive and be done with it.  I mean, come on... I thought Linux was supposed to be more stable.

---

### Post by corrytonapple on 2010-09-03
It is not Linux's or Ubuntu's fault. It was just the fact that you had a bad CD. Nothing to worry or get mad at anyone or anything about. Just get another CD and reburn the Ubuntu iso.

---

### Post by ubunwhat on 2010-09-03
I know that.  I regretted that last comment as soon as I hit submit.  I'm just frustrated and that was a fairly childish way of expressing my frustration.

---

### Post by beren.olvar on 2010-09-03
Edit: if turns out the CD wasn't the problem, then try out my suggestion. :P

what's your graphic card? does this also happen if you enter in text mode? that is without starting the X server. 
If you manage to go into text mode, do the following, after logging in
```

$ dmesg > log.1
$ lspci > log.2
$ lsmod > log.3

```
save them in a pendrive, or someplace in the disk you can access from other OS, or in whatever other way you can think of to be able to post them here. (this site could also be useful: [http://ix.io/](http://ix.io/))

Note that if you need to save the log files in a pendrive you may need to mount it manually, since there will be no gnome to help you. Try something like 
```

$ sudo mount /dev/sdb1 -t auto /media/disk

```
where sdb1 should be your pendrive partition. (If you don't know what this is ask here for further guidance)
After having it mounted you have to 
```

$ cp log.* /media/disk/
$ sudo umount /media/disk/

```

---

### Post by ubunwhat on 2010-09-03
I have not been granted any opportunity to do anything in text mode and wouldn't even begin to guess how I might achieve that...

---

### Post by soresger on 2010-09-03
Download Ubuntu again from this web page: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

This time burn it to a DVD disc instead of a CD and follow Jerry N's instructions too. 

Try it out.

---

### Post by ubunwhat on 2010-09-04
Ok, so downloaded from the link above and followed the install instructions.  I have a new build that boots... in fact it boots a little too often.  Like, at random intervals.  For no apparent reason.  I'm still getting the periodic black screens, but now half of the time rather than recovering with a tap of a space bar the system just reboots.  I'm not sure where to go from here...

---

### Post by uRock on 2010-09-04
What GPU does your system use? This sounds like a hardware/driver issue.

---

### Post by ubunwhat on 2010-09-04
I am running a Toshiba Satellite P205 that is stock except for the new HDD.  It runs an Intel GMA 950.  I've never had a problem with it in Windows.

---

