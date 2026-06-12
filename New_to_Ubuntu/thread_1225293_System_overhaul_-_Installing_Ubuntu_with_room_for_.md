---
title: "System overhaul - Installing Ubuntu with room for Win7 later"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by sackbj on 2009-07-28
I am going to do a fresh install on my machine when I get a new video card this week.  I am planning on using Ubuntu 9.04 64bit as my main operating system.  This computer was built to play games, so I want to leave some room for Windows in order to play some games that don't go well with Linux.  

However, I absolutely hate Vista - it is the cause of this entire computer reworking.  I will wait for Windows 7 and possibly install that if it is received well a couple months after release.  Until then I can occupy myself with WoW which seems to work fine with Linux.

My specs are:
Core 2 Duo 3.0Ghz (E8400 I think)
Abit IP35 Motherboard
8GB DDR2 Ram
EVGA Nvidia GTX 260
Raptor 150 GB 10k rpm drive (for OS)
WD 640 GB (for storage)

The 640 GB drive will hold most of my media like music, videos etc. It has already been formatted in NTFS and is already home to a bunch of stuff.  However, the games I will generally want to run from my faster drive, and probably from a Windows environment.

Right now I am considering this:

40 GB for Ubuntu. I am not sure how I will partition this, any help would be appreciated.  Particularly whether or not I should have a swap partition, and how to set up primary/logical partitions.  I am somewhat inexperienced with this, so I would default to 2GB swap, 10GB for /, and then the rest for /home.   That leaves me plenty of room for applications and whatever else I need to install.  Is that a safe setup?  Should I be using ext4 for all of this?

The rest I would leave for Windows because it needs more space for games.  My concern with this is should I be leaving this space at the beginning of the drive and putting the Ubuntu installation after leaving 100GB of free space.  I have read before that Windows likes to be the first OS on a drive; I don't know if this just means first installed or literally first.

Thank you in advance for any help.

---

### Post by nhasian on 2009-07-28
as long as windows is on a primary partition (you can have up to four per drive) you will be alright.  if you want windows on the first partition you can just leave it blank for now and have ubuntu installed on the 2nd one.  with all that ram, you probably dont even need a swap file unless you plan on hibernating/suspending to disk power saving features.  if thats the case you'll want at least an 8 gig swap file.

PS give Karmic Alpha3 a whirl.  it uses EXT4 by default and its been running great on my laptop.

---

### Post by sackbj on 2009-07-28
8 gigs is a lot to lose out on when your drive is only 150.  I'll probably forego using Swap and just manually startup and shut down my machine.

If Karmic is pretty stable, then I wouldn't mind giving that a shot.  This machine isn't for production by any means, basically just games and stumbling around.

If I did decide to use swap, would my machine have to write 8GB to the hard drive every time it suspends?  This seems pretty taxing on the hard drive and time consuming.

---

### Post by nhasian on 2009-07-28
the swap partition doesnt need to be on your super fast raptor drive, it can be on your secondary hard disk.  when you suspend your computer all the data in ram gets copied to the hard disk.  if you only use 1 gig out of 8, then only the 1 gig of data will be written to the hard disk.  I've been using karmic since alpha2 first came out (alpha3 is out now) and although there were a few glitches, they were easily corrected after fixes were released.  no major show stoppers.  Plus it boots really fast and the fsck is also really quick thanks to EXT4.

> **sackbj said:**
> 8 gigs is a lot to lose out on when your drive is only 150.  I'll probably forego using Swap and just manually startup and shut down my machine.

If Karmic is pretty stable, then I wouldn't mind giving that a shot.  This machine isn't for production by any means, basically just games and stumbling around.

If I did decide to use swap, would my machine have to write 8GB to the hard drive every time it suspends?  This seems pretty taxing on the hard drive and time consuming.

---

### Post by sackbj on 2009-07-31
Ok, here is my new plan:

Install Windows 7 RC 1 x64 beta.  Format 150GB drive NTFS and install windows.  After installation, install Ubuntu 9.04 by carving out 50GB from the end of the drive for ext4.  10GB for / and the rest for /home.  Carve out 8 GB at the end of my storage drive and use that for swap.

I previously had an ATI HD 3870 X2 video card. This never worked with Linux.  Now I have a Nvidia GTX 260.  I tested it out last night with my current Kubuntu install.  I have never had an easier time getting my graphics drivers working.  Using the restricted drivers interface was simple.  One reboot and I was at 1920x1200 with everything running smoothly.

I tried using KDE but didn't really like the interface as much as GNOME.

Thanks for the advice, nhasian.

---

### Post by llamabr on 2009-07-31
> **nhasian said:**
> if thats the case you'll want at least an 8 gig swap file.


That's an old rule that doesn't really apply anymore.  It was a rule of thumb when we all has 64 meg of ram, but with several gigs available, i us just no longer really the case.

Even a gig of swap will do you just fine, and you can get by with much less.  Mine is 500 meg

---

