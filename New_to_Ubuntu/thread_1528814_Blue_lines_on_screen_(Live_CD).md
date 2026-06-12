---
title: "Blue lines on screen (Live CD)"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Holy Penguin on 2010-07-11
I have installed Ubuntu on my brothers desktop a few days ago. I also want to switch to Ubuntu from Vista on my Toshiba A305-S6861 laptop which has a 64-bit architecture and uses an                   ATI Mobility Radeon HD 3470 graphics card. Before I install Ubuntu, I wanted to test several things like hardware and wireless compatibility. When I choose the live cd option from the boot menu, horizontal blue lines appeared on my screen. The lines are short and not steady, there are hundreds of them traveling around my screen.

Before posting, I thought about installing the drivers and test again but I can not restart the OS(with drivers installed) with the live cd, am I wrong?

I want to test the drivers without formatting the hard drive because I do not want to format 320 GB several times.

:arrow: I also have a live usb. Can I install the drivers in it and reboot?

---

### Post by audiomick on 2010-07-11
Hallo.
I think you are right in suspecting that the blue lines are a driver problem.

If you are running from the live CD, I think this will work (although I haven't tried it).

Boot into the live CD. "Install" the driver there. Do not shut down, but log off and back on. This will re-start the desktop environment, and should start the video driver you have just installed.


Another option, _maybe_: Partition off about 10 GB of your drive and do a test install there. I am really not sure, but I think if the partition involved is small, the format /install process isn't that long.

---

### Post by Holy Penguin on 2010-07-11
> **audiomick said:**
> 
Boot into the live CD. "Install" the driver there. Do not shut down, but log off and back on. This will re-start the desktop environment, and should start the video driver you have just installed.

Thank you for your help, your first suggestion worked like a charm.

---

