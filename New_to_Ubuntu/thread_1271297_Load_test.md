---
title: "Load test?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by japhyr on 2009-09-20
I have a laptop which I believe may be faulty.  It has crashed several times, and usually when it is working somewhat hard.  For example, when playing around with compiz it has crashed a number of times.  Even if disabling compiz addresses the immediate problem, I would still run into the problem when doing intensive work at some other point.

Before sending it back to the factory, I would like to run some kind of performance test that is easily reproducible.  I hate the thought of people at the factory not being able to reproduce the problem.

Is there a simple way to load-test the computer?  Something that every machine should be able to do, that if this machine can't do it there is definitely something wrong with it?

---

### Post by dearingj on 2009-09-20
You can try running a RAM test using memtest86. It can be accessed from the grub menu when your computer boots up.
You can also try testing your Ubuntu hard drive partition for errors, though from what you've said I don't think that's the problem. You'll need to boot from a live CD or USB for this since you can't test a partition that is in use.

As for testing your CPU, try installing cpuburn. I've never used it myself but it might help you.

I'll post again if I think of any other tests you can try.

---

### Post by tgalati4 on 2009-09-20
I agree, first run the RAM test for 30 complete cycles--this will take overnight.  You should have 0 errors for 30 complete cycles.  Even 1 error is too many for reliability.

Next, I would work the processor.  Try superpi (search superpi in the forums).  There are several options in cpuburn.  Run it and watch the temperature of the processor.  Install a temperature monitor in the panel to watch.  Your temperatures should not exceed 70C--especially in Alaska.

Then work the graphics card.  I assume the machine came with Windows initially.  Try playing a 3D shooter game--perhaps a demo that you can download.  That will stress the processor.  If it locks up during the game, then you need to do more testing of the GPU to determine if it is faulty.  There are a few 3D games in linux that you can use as well.

If it crashes in both windows and linux during 3D game play, then you can be reasonably sure that the GPU is the culprit.

---

### Post by XCan on 2009-09-21
I recommend Orthos if you plan to do CPU stress test. Unfortunately you'll have to run it through Wine, but other than that I find it very convenient as it will notify you if a checksum doesn't add up, i.e., unstable PC.

---

### Post by 3rdalbum on 2009-09-21
Three words: Phoronix Test Suite.

It has a bunch of benchmarks for various things, including ones for "burning" the CPU and testing the speed of RAM and disks.

There's always the possibility of the problem being caused by bad RAM, so try some runs of Memtest.

---

### Post by japhyr on 2009-09-24
> **tgalati4 said:**
> I agree, first run the RAM test for 30 complete cycles--this will take overnight.  You should have 0 errors for 30 complete cycles.  Even 1 error is too many for reliability.


The computer came with 9.04 installed, and I tried memtest the other night.  On the first attempt the test started normally, but when I looked at the computer less than 10 minutes later it was off.  I decided to try again, and this time the computer ran overnight.  After 9+ hours, it had completed 4 passes with no errors.

[LIST]
[*]People are suggesting 30 cycles, overnight for a good test.  At this computer's rate, 30 cycles would take ~60 hours.  Is 4 passes in 9 hours cause for concern?
[*]What do I make of the computer crashing once during memtest?
[/LIST]

---

### Post by japhyr on 2009-09-26
bump?

---

### Post by dave WB3DWE on 2009-09-26
[FONT=Lucida Sans Unicode][SIZE=3]Several replies up it was suggested to install a temperature monitor in the panel.  I have seen someone else's system with a cpu temperature monitor.  How does one do this ?[/SIZE][/FONT]

---

### Post by Miljet on 2009-09-26
Yes, I would be concerned both about the computer crashing during mem test and about the mem test taking so long. You might try re-seating the ram module and trying it again. 

Shortly after Jaunty was released, a lot of people were having problems with laptops overheating and shutting down. That was some months ago and I assumed that it has been fixed. But I would install some way to monitor the cpu temps. Do a search for lm-sensors.

---

