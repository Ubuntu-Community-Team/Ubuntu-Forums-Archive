---
title: "Glitchy artifacts on screen; Dell Dimension 2400; Intel 82865G"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-01
A little background:

The system is a Dell Dimension 2400 which comes with an Intel 82865G Integrated Graphics Controller.  Not spectacular, I know, but I use this mostly as a server of sorts.

When I attempted to upgrade it from 10.10 to 11.04 recently, the system went to a black screen mid-way through the upgrade process  and remained frozen in this black screen until I forced it off and powered it back up.

The system booted, albeit very slowly, but no error messages showed up along the way.  I went to the update manager which still said "11.04 is available" so I clicked the upgrade button, but this time is said I had to do a "partial upgrade", so I told it to proceed.  It went forward and applied the rest of the packages and replaced a few configuration files, and asked me to reboot the system.

The first time I booted I got an error message that told me the hardware was not capable of displaying Unity and asked me to select "Classic Ubuntu" or something at the login screen (which never appeared), and it proceeded to boot into GNOME after clicking OK.  The desktop, icons and upper/lower panels loaded but looked a little glitchy and then the system completely locked up abotu 15 seconds after booting.  Attempts to boot again didn't show the error message about Unity, but the system still locked up.

I used another computer to burn a fresh Live CD and proceeded to "Upgrade from Ubuntu 11.04 to 11.04" (yes, this is what it said), and this thankfully repaired the system at least to the point where all I had to do after this upgrade was reinstall a couple things like ssh.

The problem I'm having now is the exact same glitchy display problems seem to be persisting.  I've attached a screen shot to show what this looks like.  Any ideas on why this is happening and how to fix it?

---

### Post by danielgm on 2011-05-02
I'm having exactly the same problems.


```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

---

### Post by TZer0 on 2011-05-02
Same card, same kind of issues, both KDE and Gnome (but not crashes while updating) - Xorg hangs occasionally at 99% CPU usage, any fixes?

[Screenshot]("http://dl.dropbox.com/u/1184173/Screenshotgpu.png") (note: black boxes were made by me)

(tested with different RAM and live, both 11.04 and pre 11.04 - all conclusively pointing towards 11.04 as the cause)

Mod: move this to general help

---

### Post by nigeltufnel on 2011-05-02
I can completely echo the sentiments.  I too have an older machine with the same Intel Corporation 82865G Integrated Graphics Controller.  I also had the same pop-up about not displaying Unity and to choose Classic Ubuntu.  I can't say my problems are completely resolved, but I at least have an operational system now.

My current issue is that I see "visual noise" in various windows or on my desktop.  The two attachments show noise in Firefox and distortion in my toolbar.

I suspect this has to do with the i915 driver being loaded, instead of i810.  I had several display issues on 10.10 (and perhaps 10.04) due to the system incorrectly determining my video card.  On 10.10, I had set up GRUB defaults in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i810.modeset=0"
```

However, the system clearly shows the i915 driver is back:
```
$ lsmod | sort | grep i915
drm                   180037  3 i915,drm_kms_helper
drm_kms_helper         40745  1 i915
i2c_algo_bit           13184  1 i915
i915                  450944  2 
video                  18951  1 i915
```

To the original poster's comments about glitchy screens and lock up, I mainly have dealt with flicker problems where I could could click on the Ubuntu menu and it would appear to display.  I could position my pointer where the menu should display and for a moment, I could see a flash of the menu appear.  I learned that switching between a virtual console and the GUI would allow me access to the main menu.  I eventually logged, out, then tried other sessions.  I can't remember the exact name of the one I am using now, but it basically has no visual effects.  I step away from my computer briefly and upon my return, found the GUI completely locked up.  I could log in remotely through XRDP, so I am pretty convinced that issue can be attributed to the video card troubles.

I think the solution lies in getting the i810 module loaded, but how does one configure this in 11.04?  Since my /etc/default/grub shows i810, why is i915 loaded?

---

### Post by diablo75 on 2011-05-02
> **nigeltufnel said:**
> I can completely echo the sentiments.  I too have an older machine with the same Intel Corporation 82865G Integrated Graphics Controller.  I also had the same pop-up about not displaying Unity and to choose Classic Ubuntu.  I can't say my problems are completely resolved, but I at least have an operational system now.

My current issue is that I see "visual noise" in various windows or on my desktop.  The two attachments show noise in Firefox and distortion in my toolbar.

I suspect this has to do with the i915 driver being loaded, instead of i810.  I had several display issues on 10.10 (and perhaps 10.04) due to the system incorrectly determining my video card.  On 10.10, I had set up GRUB defaults in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i810.modeset=0"
```

However, the system clearly shows the i915 driver is back:
```
$ lsmod | sort | grep i915
drm                   180037  3 i915,drm_kms_helper
drm_kms_helper         40745  1 i915
i2c_algo_bit           13184  1 i915
i915                  450944  2 
video                  18951  1 i915
```

To the original poster's comments about glitchy screens and lock up, I mainly have dealt with flicker problems where I could could click on the Ubuntu menu and it would appear to display.  I could position my pointer where the menu should display and for a moment, I could see a flash of the menu appear.  I learned that switching between a virtual console and the GUI would allow me access to the main menu.  I eventually logged, out, then tried other sessions.  I can't remember the exact name of the one I am using now, but it basically has no visual effects.  I step away from my computer briefly and upon my return, found the GUI completely locked up.  I could log in remotely through XRDP, so I am pretty convinced that issue can be attributed to the video card troubles.

I think the solution lies in getting the i810 module loaded, but how does one configure this in 11.04?  Since my /etc/default/grub shows i810, why is i915 loaded?

It looks like you're on to something.  I just checked the Dell and it's running the i915 modules just like yours was.  So yeah, how do we fix that?

---

### Post by Arifcatalyst on 2011-05-02
Same HEre-[http://ubuntuforums.org/showthread.php?t=1746854](http://ubuntuforums.org/showthread.php?t=1746854)

---

### Post by berapp on 2011-05-03
I'm having the same problem on a custom machine.  I was able to see the screen enough to change to Classic Ubuntu (no effects). 

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation Desktop Board D865GLC
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 1
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

---

### Post by TZer0 on 2011-05-03
No help with this?

---

### Post by diablo75 on 2011-05-04
From the looks of this thread:  [http://ubuntuforums.org/showthread.php?p=10761694](http://ubuntuforums.org/showthread.php?p=10761694)

An update is in the works already and will be downstreamed soon.  So... Problem solved (soon, via updates).

---

