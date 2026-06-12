---
title: "Sony webcam_Sype_Ubuntu_10.04"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by GLIA on 2010-11-14
Hi,

A few days ago I downloaded SKYPE BETA v.2; everything went smoothly. However, when I tried to configure my built-in camera under "options" ->"video devices" and test it, skype crashed every time. Same thing happened when I tried calling my contacts; immediately after they (or I) took the call, it crashed.

Here are a few things I've tried so far to remedy the situation using whatever help I could find on similar problems documented in the forum. I've had minimal success, and would appreciate if anyone could help me solve this problem. 
[B]
1. Launching skype from the terminal using[/B]

[COLOR=Red]LD_PRELOAD=/user/lib/libv4l/v4l1compat.so skype[/COLOR]

If ran from the terminal, skype does not crash when the webcam is tested. However, the display window does not change and when clicked twice in quick succession the computer screen turns white; when ESC is pressed, the computer returns to the "options" window in skype, but this time webcam window is completely white.

I then found out that I could launch skype from the terminal by simply typing "[COLOR=Red]skype[/COLOR]" at the shell prompt. This is what I use now. When I tried running skype from "Applications", it crashed every time I tested the camera and continues to do so even now

**2. Checking the webcam**

Running [COLOR=Red]lsurb[/COLOR] in the terminal I got this:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 002: ID 04a9:262f Canon, Inc. MultiPASS MP730
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**[COLOR=Blue]Bus 001 Device 002: ID 05ca:18b5 Ricoh Co., Ltd [/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Also, I downloaded "Cheese" and the webcam works.

I also ran "gstreamer-properties" and tested the camera in "Multimedia Systems Selector" and it works.

**3. Installing r5u87x driver**

In several forums, it was suggested downloading this driver and apparently for a lot of the built-in cams on sonies this does the trick. There were two suggestions on how to code the installation and I tried them both. Both seemed to have worked, but at the end always the same message:

r5u87x firmware loader v0.2
Searching for device...
Error: Failed to find any supported webcams

I then visited this site [COLOR=Blue]http://www.arakhne.org/ricoh/[/COLOR] and did not find my webcam in the list provided, so I assume that this driver is not for it (or perhaps there is some sort of a workaround that I don't know of???)

**4. Launching Google Talk**

I also tried google talk to see if the problem is specific to skype. No! Neither I nor my contacts had any video transmission at all and I kept getting "technical difficulties" error message every time.

When using skype in video mode (and only when it's launched from the terminal) my contacts can see me and I receive their video. But I have a white window where 
my video is supposed to be. Another, interesting thing is that if I launch skype first and then try to launch "cheese", it crashes (i.e. cheese) after the countdown. But if I lauch "cheese" first, my contacts receive no video from me on skype; and after exiting from "cheese" I have to activate my webcam for my contact to see me, but it does not automatically come on. There is obviously some sort of a sharing problem and in the terminal I get the following:

libv4l2: error setting pixformat: Device or resource busy
segmentation fault

I'm out of solutions right now. If some of you could suggest what to do next, I'd appreciate it. Thank a lot!

---

