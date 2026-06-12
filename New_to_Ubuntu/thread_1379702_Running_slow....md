---
title: "Running slow..."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-12
I got Ubuntu 9.10 installed on my laptop and it was working fine, except compared to Windows it seemed to struggle quite a bit.  Even things like opening folders and Firefox could've ended up being a 5 second ordeal (which doesn't seem like much, but adds up when you're constantly doing that sort of thing).  Tried turning off the visual effects and everything, no real help.

Is there any possible reasons why Ubuntu was running so much worse than Windows (any)?  Is it normal that its a bit slower?  My laptop isn't even good, by any means, but if it can handle Vista at a respectable speed, I would think a nice O/S like Linux/Ubuntu could be handled.

Specs:
Intel Core2Duo T5800 2.0Ghz
2gb RAM
250gb Hard Drive
Intel GMA X4500HD

I wasn't running it on Windows or anything, it was in it's own 15gb partition with a swap partition and everything.

Thanks for any help. :)

---

### Post by ssulaco on 2010-01-12
open a terminal:Applications>Accessories>Terminal and run ```
top
```
see if there is anything hogging the processor

---

### Post by Dreakon on 2010-01-12
I can't really get onto it at the moment, but it was literally installed for like an hour and from the very start I noticed this as a bit of a problem.  What could possibly be eating the processor up so badly lol?

Could it be a driver problem?  I never installed any since the defaults seemed to look and work okay enough, outside of the performance issue.

---

### Post by ssulaco on 2010-01-12
> **Dreakon said:**
> I can't really get onto it at the moment
I have no clue as to why it is so slow,you have plenty of horsepower according to your specs.

---

### Post by Dreakon on 2010-01-13
Anyone else maybe have any other ideas as to things I could do to help performance with Ubuntu?  Perhaps places where I can get Linux specific drivers for my graphics chipset (the Intel card), unless the default should be functional enough?

Anything at all? ;)

---

### Post by muteXe on 2010-01-13
So did you actually do what ssulaco suggested and type "top" at the command line??

---

### Post by Dreakon on 2010-01-13
The object "root" is taking up 2% or less of the CPU.  That's the largest object in the "top" thing.

Any other ideas? :)

---

### Post by Forbees on 2010-01-13
could be how you partitioned the drive.

if your linux partiton is fragmented on the harddrive in anyway it'll slow it down. clean instal usually runs better than a dual boot

---

### Post by DestructionsRightHand on 2010-01-13
do you have apparmor profiles enabled for firefox?

---

### Post by Dreakon on 2010-01-13
> **Forbees said:**
> could be how you partitioned the drive.

if your linux partiton is fragmented on the harddrive in anyway it'll slow it down. clean instal usually runs better than a dual boot
Will it make it this noticably slow?  Can anyone confirm this because I would prefer to keep the operating system on a reasonably sized partition (Ubuntu is currently sitting on 15gb of hard drive space).  I thought the point of creating a seperate partition was so things could run full speed?  Space shouldn't be an issue yet... If I wanted to slow things down, I would've just kept the flash drive Ubuntu thing I had...

Also, I intend to delete Windows off of the other partition, so technically it won't be dual booting soon lol.

> **DestructionsRightHand said:**
> do you have apparmor profiles enabled for firefox?
I'm not sure what that is, and would it effect system performance even when Firefox isn't running?

---

### Post by DestructionsRightHand on 2010-01-13
[URL="http://en.wikipedia.org/wiki/AppArmor"]http://en.wikipedia.org/wiki/AppArmor
[/URL]
or man apparmor

---

### Post by mörgæs on 2010-01-14
> **Dreakon said:**
> Will it make it this noticably slow?  Can anyone confirm this because I would prefer to keep the operating system on a reasonably sized partition (Ubuntu is currently sitting on 15gb of hard drive space).  I thought the point of creating a seperate partition was so things could run full speed?  Space shouldn't be an issue yet... If I wanted to slow things down, I would've just kept the flash drive Ubuntu thing I had...

Also, I intend to delete Windows off of the other partition, so technically it won't be dual booting soon lol.



I have not experienced that a fragmented drive slowed Ubuntu down. It makes a diffenence in Windoze, but not much here. A simple test is just watching the HDD-LED :-)

If Ubuntu is slow, in my experience a good first shot is to focus on the graphics driver.

---

### Post by Dreakon on 2010-01-15
> **mörgæs said:**
> If Ubuntu is slow, in my experience a good first shot is to focus on the graphics driver.
From what I hear, there aren't any really good drivers for Intel integrated cards yet... :(

---

### Post by Michalxo on 2010-01-16
My ubuntu is running very slow especially when flash comes in.
Here's small vid what can happen on this machine watching youtube.

32bit ubuntu dualcore, nvidia latests, flash latest.
30MB video -> [here]("http://www.mediafire.com/?lze0ohm2mjo") or [here]("http://xpa.cz/data/michalxo1.ogv")

Anyone willing to help, please? :-/

---

### Post by DestructionsRightHand on 2010-01-17
you not the only one having this problem with flash.  Just keep making noise about it, if your rely nice and want a fix post it to the devs and they might fix it.

---

### Post by EugeneK on 2010-01-21
> **Michalxo said:**
> My ubuntu is running very slow especially when flash comes in.
Try this (from [this thread]("http://ubuntuforums.org/showthread.php?t=1375504&page=2&highlight=flash+system+slow")):

[INDENT]*The video is sluggish/has a slow response. What can I do?*

You may have set "ximagesink" ("X Window System (No Xv)") as video-output. This means that your cpu is doing all the work. Change it to "xvimagesink" ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.

To change the settings, run "gstreamer-properties", click the Video tab, and change the appropriate settings.[/INDENT]

---

### Post by Marvin666 on 2010-01-21
Have you tried xfce? I've never tried gnome, but my laptop runs at a crawl with kde. With xfce it's fast.

---

### Post by Kai69 on 2010-01-21
Hi all I installed ubuntu 9.10 64bit this week full os no dual boot and it was really slow for about 48 hours and then sorted itself out i was running 32bit and had no problems with it i just used my lappy as normal rebooted as normal i still dont know what caused the slowdown but its ok now 
[http://ubuntuforums.org/showthread.php?t=1385569&highlight=64bit+running+slow](http://ubuntuforums.org/showthread.php?t=1385569&highlight=64bit+running+slow)

---

### Post by ZeroSpawn on 2010-01-21
Check your start up programs, take out anything you don't use. See if that speeds the computer up. Worked for me.

---

### Post by Michalxo on 2010-01-23
> **EugeneK said:**
> Try this (from [this thread]("http://ubuntuforums.org/showthread.php?t=1375504&page=2&highlight=flash+system+slow")):

[INDENT]*The video is sluggish/has a slow response. What can I do?*

You may have set "ximagesink" ("X Window System (No Xv)") as video-output. This means that your cpu is doing all the work. Change it to "xvimagesink" ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.

To change the settings, run "gstreamer-properties", click the Video tab, and change the appropriate settings.[/INDENT]

Wow! Thank you very much. Same site, same video on FF3.6 uses about 20-50% less of CPU  :-) and I see no eye-catching screen torning ;-)
Why is that not set as default?

---

