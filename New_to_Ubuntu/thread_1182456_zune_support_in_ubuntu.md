---
title: "zune support in ubuntu?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by thepiratefish on 2009-06-09
Does Ubuntu support the zune? I didn't take my zune into consideration when i decided to make the switch to ubuntu...

---

### Post by mtheultimate on 2009-06-09
Same here. I dont know how I spaced on something so big.
Sadly, there is no support. 

I found this post:
> 
The solution for real MTP Unix compatibility is the libmtp open source library. We at Zune-online.com support the effort for a Linux and Mac compatible Zune. (I have no idea what Microsoft thinks about this).

[http://www.zune-online.com/news/zune/zune-on-mac-os-x-and-linux.html](http://www.zune-online.com/news/zune/zune-on-mac-os-x-and-linux.html)

Some linux apps support MTP but I dont think they work for Zunes because
the Zune uses "MTPZ".

Look before you leap.

---

### Post by thepiratefish on 2009-06-09
What is MTP? I wouldn't quite say I'm tech-retarded...but I'm not terribly familiar with anything to do with programming. The farthest I got in high school was TrueBASIC...

---

### Post by mtheultimate on 2009-06-09
[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

Its just the way they transfer data to the device. Unfortunately the Zune
uses a modified protocol called MTPZ so I dont think mtp-friendly linux apps like amarok will work.

We are just SOL.

---

### Post by thepiratefish on 2009-06-09
Is that part of the reason why you can't just drag and drop files to the zune? and why you can't view the zune as a drive?


perhaps another solution would be to force a different firmware on the zune?

---

### Post by mtheultimate on 2009-06-09
> 
perhaps another solution would be to force a different firmware on the zune?


Funny you say that, MS in their infinite evil encrypted the firmware just so we couldnt do that.
God knows why such a thing was even necessary.

[http://ubuntuforums.org/showthread.php?t=661358](http://ubuntuforums.org/showthread.php?t=661358)

> 
There have been attempts to put Linux on it, but the firmware is encrypted. Without knowing the hash to follow the firmware boot, it's difficult to intercept the firmware boot and substitute your own. A google search will show what has been done to date, but to my knowledge, the encryption is a real show stopper. The hardware is good and shouldn't be too difficult a challenge once a method is discovered to substitute firmware.


---

### Post by tacantara on 2009-06-09
I'm not as tech-savvy as many of the folks on here, so I went with a fairly simple solution.  I installed VirtualBox (from the website - the repos version is very limited) and set up a virtual XP machine.  The only reason I have the virtual machine is to run things like Zune, for which there isn't a Linux alternative.

I did check out Wine, but I found it to be of no use for Zune :(

---

### Post by izaneartist on 2009-08-15
Is it possible to install the zune software into Wine?

---

### Post by GoldenSun on 2009-08-15
> **izaneartist said:**
> Is it possible to install the zune software into Wine?

> **tacantara said:**
> 
I did check out Wine, but I found it to be of no use for Zune :(

The zune is a dead end for linux support.  VBox is the only reasonable solution.

---

