---
title: "Unstable system - how do I check if the correct kernel is loaded"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Brad wilkinson on 2010-05-16
Hello,

I've just put together a new PC and loaded 10.04 as my os.

I actually loaded 9.10 then upgraded the distro to 10.04.

The PC is a Gigabyte GA-880GM-UD2H motherboard (V4 bios), a Phenom II x6 1055, 8gig of ram in 2x4gig sticks, 2tb hdd, DVD drive, 750W power supply.

The Video is the on-board version for now. (in system monitor it sees 6 processors and 8 gig of ram, and Kernel Linux 2.6.32-22-generic-pae. There, answered part of my own question!).

The problem I am having is that the system is really slow to do things like open firefox, system monitor, and just about everything. It even crashed to a blank screen with a non-blinking cursor in the top left a little while ago while I tried to copy ~8 gig from USB to Hdd.

How do I find out what the correct kernel is for my CPU (I'm guessing it is not the i386 one) and how do I load this kernel after I find it?

How do I ensure I have a 64 bit kernel loaded?

I know the CPU is only recently released, but it doesn't have any extra instructions (afaik) than the Phenom x4 does, so should I use a kernel for that and see how I go?

Cheers,

Brad

---

### Post by slibuntu on 2010-05-16
If you want to use a 64bit kernel, you'll need to install the 64bit version of Ubuntu, just download and install the 64 bit version from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (click alternate options to select 64 bit)

That said, it's stange that you are having stability issues. The only thing I can think of is the PAE patch making the kernel unstable, but that shouldn't happen either.

My advice would be to reinstall using the 64 bit version and see how that goes.

---

### Post by Brad wilkinson on 2010-05-16
OK, I could download a whole new cd worth of stuff, but shouldn't I be able to just go to synaptic and find the extra bits I need, and download them only? (I've looked a bit, but my search-fu is weak).

And as I recall from years ago when I last played with linux, wouldn't I then be able to (set it up to) choose which kernel I booted into when I turn the PC on?

Cheers,

Brad

---

### Post by marshmallow1304 on 2010-05-16
No, you can't just switch to a 64-bit kernel; all the software is still 32-bit and you'd run into all sorts of problems.  The only way to switch to 64-bit is to install it fresh.

Something strange is going on - some of the slowness may be due to onboard graphics, but X shouldn't crash when you copy data over USB.  Be sure to check the iso integrity with an MD5 sum or use a torrent and verify the disc after burning.

---

### Post by Brad wilkinson on 2010-05-16
ok, so the 32-bit and 64-bit versions don't work together.

thanks. I'll let you know how it goes.

---

### Post by galileon on 2010-06-10
Hey Brad, what's the latest?

---

### Post by Brad wilkinson on 2010-06-12
Well I got the 64-bit kernel running in a new partition and it seems to be running fine. 

However.

I was just using the on-board graphics chip (ati/amd) and it wouldn't do 2560*1600, so I went and got an ati 5850 add in board, as it is the same as the chip set manufacturer, so hopefully less problems.

Now I get 2560*1600, but I don't get flash video (abc iview tv shows) and my ctrl+ scaling in firefox ends up with blocky pictures. This makes me think that I've not got the correct drivers loaded.

I downloaded (and installed) the binary drivers (fglrx) supplied by ati/amd using synaptic, but I also have the X.Org X server -- AMD/ATI Radeon display driver loaded.

Should I un-install the X org stuff, and just rely on the fglrx stuff?

The reason I think the setup I have now is not working properly is that in winXP on an athlon 2400 with a ati 1600 video card, on the same screen firefox would ctrl+ scale pictures and not make blocky bits out of them.

---

### Post by Buffalo Soldier on 2011-04-28
Hi Brad,

Sorry to hijack your thread. I'm planning of buying the Gigabyte GA-880GM-UD2H for my next computer. How is it so far? Any other problems beside the resolution issue?

---

### Post by nebileix on 2011-04-28
Try the drivers from ati website

---

