---
title: "GBU Grub issue"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by El-Linux on 2010-01-18
Hi guys,

After a recent system crash, I've had to wipe the computer clean and this time around have installed Ubuntu for the first time ever.

It has said it installed however upon loading up I'm met with:

"GBU Grub version 1.97 beta4

Ubuntu, Linux 2.6.31-14 Generic
Ubuntu, Linux 2.6.31-14 Generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+ serial console 115200)"


I've tried the first two options, however when the computer processes both, I get the following error:

"error: biosdisk read error
Press any key to enter"


Pressing any key only takes me back to the original Grub screen. I haven't tried either of the memory test options yet as I have no clue at all what I'm doing there.

How do I proceed from here?

Thanks in advance!

---

### Post by synapsys on 2010-01-18
Sounds like the "crash" may have had something to do with a failing hard drive? 

Have you tried scanning the hard drive with a diagnostic tool like seatools?

---

### Post by El-Linux on 2010-01-19
That's correct, yes.

I haven't tried anything like that due to a lack of any (working) OS. How would I go about doing it without an OS, and where do I go from there? (after it's run)

Thanks

---

### Post by inobe on 2010-01-19
if you know the brand hard drive, seagate for example has a tool called seatools, you can make a bootable cd that will perform maintenance on the disk.

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

---

### Post by ranch hand on 2010-01-19
And you should be able t odo these things from the Live CD.

You can install things while running the Live Session.  They install on your ram so they are gone on shut down or reboot but they work fine.

---

### Post by synapsys on 2010-01-19
You can also grab a copy of the ultimate boot cd, which has a lot of diagnostic programs including hard drive tests from a few different manufacturers.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by El-Linux on 2010-01-20
OK, just finished doing all three (as and when I can) in order:


**HDD Tools** - I found one for my hard drive, Hitachi Travelstar (Drive Fitness Test). I've run that, found corruption and tried to fix it. At the end of the repair bit it said it couldn't do it and "Defective Device - [something else I cannot remember off hand]." Sounds to me like a problem with the drive physical side of the drive..

Upon re-trying, it couldn't even find the drive at all, so I couldn't get the exact error to come here complaining about.


**Live CD** - Next, I tried loading up the Live CD (Ubuntu disc) and using the option there, it completed and said there was absolutely nothing wrong with the hard drive.. oddly.


**Ultimate Boot CD** - So I moved on to the UBCD option, loaded it up and tried the Drive Fitness Test option on there too, which did work, however at the end of it, it came back saying "Defective Device" (but no second bit to the explanation as I got with the first Drive Fitness Test I ran).



So unfortunately for me, I'm still no further ahead.

Is there anything else that might do the trick on the Ultimate Boot CD? I've only tried that Drive Fitness Test option so far, don't want to start playing with things I have no clue about needlessly.

I'm starting to seriously believe this might be a "throw some money at a new hard drive" job.

Thanks for your input so far guys - much appreciated.

---

### Post by ranch hand on 2010-01-20
I would boot to the Live CD and install testdisk (yes you can do this) and run it.

When you have 2 completely different test procedures telling you that your drive is bad there is a possibility that your problems may be caused by a bad drive.

I don't think that Throwing money at a new drive is the way to look at it.  You can still read the drive.  This makes data recovery and saving nice and easy.

---

