---
title: "Karmic Freezes"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by lukashjanssen on 2010-03-17
Hi, I've been running Ubuntu for just a little and not long after moving to 9.10 Karmic (not sure if it's related, probably), the system started to have problems in Ubuntu and would freeze up. If anyone could help, I'd be really glad. I dual-boot with XP, and the Windows partition runs just fine. 
what happens is I start up Ubuntu (which seems like its taking longer than usual), and I can run everything perfectly for a few minutes. however, what happens is if I try to use the scroll bar in metacity, firefox, anything, the GNOME desktop environment won't display anything new and I have to minimize/maximize to see anything new on the page. (actually, at the very bottom of the window, the picture WILL scroll, but it's just a tiny line). then, a few minutes usually after booting up, Ubuntu will completely freeze up.
I can move the cursor around as much as I want, but no keystrokes will work, and I can't do anything with the mouse on the screen, apart from move the cursor around.

can anyone help? I've tried doing a little research on the symptoms, but I'm pretty much still a noob, and I need some outside help to diagnose this. It would be greatly appreciated. thanks so much.

I was told at one time to look at my Xorg log files:

ok, first thing i happened when I opened log viewer is it said it could not open these (I'm gonna give all the info I can, hopefully some will help):

/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory

then I looked at Xorg.0.log, Xorg.20.log, and 21 and 22. 21, 22, and 23 were identical as far as I could see. I looked at the WW (warning) tags and found these: 

(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found

then a bunch of resource ranges before and after probing.

(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor

(the Could not find/read video BIOS also appeare3d in the Xorg.0.log)

then nothing that I thought seemed bad for a while and at the very bottom: 

(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) ImPS/2 Generic Wheel Mouse: Close
(II) UnloadModule: "evdev"
(II) SIS(0): Restoring by setting old mode 0x03
(WW) SIS(0): xf86UnMapVidMem: cannot find region for [0xb769e000,0x10000]
(WW) SIS(0): xf86UnMapVidMem: cannot find region for [0xaf69e000,0x8000000]
 ddxSigGiveUp: Closing log

I really don't know what any of this means, so I'm hoping the community could help me out. thanks.

---

