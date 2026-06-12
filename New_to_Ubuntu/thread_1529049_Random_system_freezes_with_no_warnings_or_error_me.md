---
title: "Random system freezes with no warnings or error messages"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by atannus on 2010-07-11
Hi guys...

I've had 9.10 SERVER installed for a long time on a P4; I've recently upgraded the hardware (motherboard, processor and memory). I've kept the two ide hds, the case and the power supply.

The system just hangs, no warning.

I've checked some of the logs I could figure out in /var/log, but I don't really know what to look for, and there are no "obvious" messages. There are a bunch of warnings, but I remember seeing those there even before the hw upgrade;

I've tried testing memory, but could not get memtest86+ to run; it says it is installed, but it's not there, and GRUB won't give me a menu; 

The hw is brancd new, fans are setup and running, nothing is dirty or dusty; ventilation is ublocked, the box sits about 5-10 inches from the wall, et cetera.

I'm lost, I don't know where to look and "random system freeze" isn't a very friendly way to look for solutions online!

I'm hoping someone can tell me where to check! Hope so!

---

### Post by Gone fishing on 2010-07-11
I'd say it would be hardware - isn't the memory test supposed to be an option on boot up? If not I'd suggest running memory test from a live CD. 

Next I'd look for over heating of the processor is the heatsink seated properly etc (you can monitor the temp of the processor using software or see it in BIOS). Then is the power supply big enough working properly can you swap it out with another unit?

---

### Post by atannus on 2010-07-11
> **Gone fishing said:**
> I'd say it would be hardware - isn't the memory test supposed to be an option on boot up? If not I'd suggest running memory test from a live CD. 


Yes, I'd expect that, but like I said, GRUB doesn't give me a menu. It does give me the memtest option on my other machines, but I have dualboot on all of them - except the one freezing.

> **Gone fishing said:**
> 
Next I'd look for over heating of the processor is the heatsink seated properly etc (you can monitor the temp of the processor using software or see it in BIOS). Then is the power supply big enough working properly can you swap it out with another unit?

Overheating is out of the question; I've monitored the BIOS, and I've tried to load the processor to get it to fail, but it fails when it wants to... even when there is no load, completely random.

I am also suspecting the power source; I'll try  that next, BUT:

Shouldn't there be some kind of warning in the logs somewhere? Or is power so critical that there's not even time to log?

so far, Thank you...

---

### Post by diablo75 on 2010-07-12
> **atannus said:**
> Yes, I'd expect that, but like I said, GRUB doesn't give me a menu. It does give me the memtest option on my other machines, but I have dualboot on all of them - except the one freezing.

To get the grub2 menu to show up, hold down SHIFT at boot (changed from the old version of grub, which used to use the ESC key).
> 
Overheating is out of the question; I've monitored the BIOS, and I've tried to load the processor to get it to fail, but it fails when it wants to... even when there is no load, completely random.

I am also suspecting the power source; I'll try  that next, BUT:

Shouldn't there be some kind of warning in the logs somewhere? Or is power so critical that there's not even time to log?

so far, Thank you...

I had a problem very similar to this that had to do with a specific wireless adapter that I still use; I think it's a Netgear WG311 (not at home right now; can't confirm).  For the longest time it worked great but a new kernel update came down that would cause it to lock the whole system up.  In the log file I saw this warning before the eventual crash:

```
Jun 24 01:47:33 ubuntu kernel: [11801.154225] ath5k phy0: unsupported jumbo
Jun 24 02:04:21 ubuntu kernel: [12808.825501] ath5k phy0: unsupported jumbo
Jun 24 02:06:19 ubuntu kernel: [12927.198284] ath5k phy0: unsupported jumbo

```
These were the very last entries in the log file before the system was powered down hard, and back up again.

The best advice I can give you right now is to look at those logs like a hawk and take note of the exact times your system is crashing to see what's happening just before it crashes.  I had to disable my screensaver to do this because I'd return to my crashed PC stuck at a black screen with no way for me to see the clock that froze on the upper task bar and know exactly when it crashed.  

You may have a hardware bug on your hands.  One experiment you might try if you have a lot of time on your hands is pull extra hardware out of the PC (expansion cards, USB devices that are not essential) and let it sit and run over night to see if it still crashes.  If it doesn't crash, add one piece of hardware back to the mix, repeat the test until it starts to lock up again.  This will take you a few days to do right but will help with narrowing down your problem.

Granted, my problems occured way back with 9.04 but they never did get solved until after 10.04 was released... so I had one long buggy year of computer use.  Perhaps you should start over with 10.04...

---

### Post by atannus on 2010-07-12
Diablo,

Thank you for your attention.

There is no hw I can pull out! It's just MB Processor and RAM; two HDs and the power source.

I'm going home in about an hour, and I'll drop by a store and pick up an alternative power source. I'm quite convinced it's to blame... 

About the logs, I've checked the syslog, and there are no particular warnings or errors before the freeze.... more as it develops...

thanks everyone...

---

### Post by atannus on 2010-07-17
Solved... or so it seems!

Well, I got a new power supply, and that did nothing. The system continued to freeze, no warnings, no log messages, no nothing.

I went back to the store and got the MB replaced, kept the same processor and ram chip. System's been up for about 10 hours now.

I get a recurring "* Reloading /etc/samba/smb.conf smbd only" message, but no freeze up.

I'll wait another couple days with and see it I get any freezes. Any ideas on these "reload" messages? I check the forum, and it seems quite common... It's nagging though...

cheers!

---

### Post by gandaran on 2010-07-18
I sometimes get freezes too and I know they are due to the video card, I used to dual boot on this old computer and the freezes only happen if I used windows XP for a long time, sometimes windows XP would crash completely and I would have to reinstall it (this computer cannot run XP service pack 2 with this graphic card) but Ubuntu would randomly freeze after so I got rid of XP and only have Ubuntu now and no problems with freezes so far.
so do you still have the same video card or are using the new motherboard on-board graphics card.

---

