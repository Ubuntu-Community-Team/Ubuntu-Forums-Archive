---
title: "No display after Nvidia driver update"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by lidaka on 2009-04-26
Hey guys,

I'm toying around with Ubuntu 9.04, this is my first time after long time using Win, so I'm a total noob.

my q is:
I've tried to upgrade Nvidia driver, and the next time I try to boot my sys up - no display.
what can I do?

---

### Post by Bodsda on 2009-04-26
What do you mean by 'no display'

Do you mean:

[LIST]
[*]No GUI
[*]No Login Prompt
[*]No Splash screen
[*]No screen output whatsoever
[/LIST]

Thanks,

Bodsda

---

### Post by stoogiebuncho on 2009-04-26
This happened to me as well.  I found the information on this page to be very helpful:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

This is the section that fixed my problem:
> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

*

Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
*

Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
*

Find the line that says Section "Screen"
*

Insert a new line that says Option "UseDisplayDevice" "DFP".
*

Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

If you need help following these instructions, let us know.  Good luck!

---

### Post by inobe on 2009-04-26
> **lidaka said:**
> Hey guys,

I'm toying around with Ubuntu 9.04, this is my first time after long time using Win, so I'm a total noob.

my q is:
I've tried to upgrade Nvidia driver, and the next time I try to boot my sys up - no display.
what can I do?

if your video card is version 6xxx series and up' you can follow this thread. 

[http://ubuntuforums.org/showthread.php?t=1129280](http://ubuntuforums.org/showthread.php?t=1129280)

it gets interestingly easy after post #10.

i helped several folks, only one person i couldn't help, the fella had dual video cards in sli.

---

### Post by lidaka on 2009-04-27
thanks for the quick replies, guys!

I've got a Nvidia 5200 GeForce FX. 
I actually tried the repair mode at the start, and pressed the "fix display problems" (or something similar) and it worked!
my next question is - do I need to update drivers for the display card? how do I update drivers at all on ubuntu?
and another silly question - what is the "command line"? where can I find it?

---

