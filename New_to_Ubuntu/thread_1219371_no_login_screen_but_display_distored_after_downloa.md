---
title: "no login screen but display distored after downloading radeon drivers"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by svenoliverspiess on 2009-07-21
Hello.

I'm not sure this is the appropriate place to post, but since I am a absolute beginner I thought I'd start out here. If there is better place to post this let me know and I'll move it accordingly.


Okay here is **my problem**:
   I recently installed Ubuntu 9.0.4 on my PC in parallel to Windows Vista. The installation went smoothly and I was up running in no time.
After getting a feel for the OS, I went on to customize it. The last time I was able to use it I installed LaTex (Kile) and some graphics drivers. I have a radeon mobility HD2300 graphics card on board and found two packages in the Synaptic window: radeonHD driver and Catalyst Control Center, which I both downloaded and installed.
   Immediately after restarting I wasn't able to log in any more. When starting my computer I first see the Ubuntu screen with the progress bar under the logo and then the screen flickers 3 times, showing white and black squares on the lower 5/6 of the screen and colorful shapes in the upper sixth. After this pattern appeares for the third time it stays and nothing else happens. There is no sound to indicate that I can log in and also trying to blindly enter log in information and confirm does not work. The power switch, however, is recognized and after pushing that the system shuts down (with the screen changing once more) and the machine subsequently turns off.


After searching online I suspect that my problem is related to the xserver and the fact that the Catalyst Center does not support older versions of ATI Radeon graphic cards which I think applies to my model as well as possibly some incompatibility between radeonHD and the Catalyst Center.


I made the following **attempts to resolve the issue** with information I could find online, which all failed:
- start the system with the xforcevesa boot option
- removing Catalyst Center with "dkms remove" in the command line/shell (which worked but didn't solve the problem)
- use the xfix option in the recovery mode window to auto repair display settings


At this point I have no ideas what else to do whatsoever and appreciate any suggestions. Or maybe somebody read about a similar problem and can provide a useful pointer.

I suppose I could just start over with a clean install, but that seems somewhat disproportionate. I'm hopeful that it's actually a pretty simple problem for a more seasoned user.

Best,
Sven-Oliver Spiess

---

### Post by arochester on 2009-07-21
Don't boot into your normal kernel (top of boot list). Boot into Recovery Mode (second on boot list). It has an option (which changes its name from time to time)(you may need to scroll up and down to find it) called something like "Try to recovery xserver". Have a go at that first.

---

### Post by svenoliverspiess on 2009-07-21
> **arochester said:**
> Don't boot into your normal kernel (top of boot list). Boot into Recovery Mode (second on boot list). It has an option (which changes its name from time to time)(you may need to scroll up and down to find it) called something like "Try to recovery xserver". Have a go at that first.
Tried that (third item on list), didn't help. :(
Thanks, though!

Oh, and I also tried Ctrl+Alt+Bksp/F1, which was futile as well.

---

### Post by svenoliverspiess on 2009-07-22
Following the advice in another thread I was able to solve the problem.

In recovery mode I opened a shell and typed:
```
sudo apt-get remove -purge xorg-driver-fglrx
```Everything works like a charm again. :)

---

