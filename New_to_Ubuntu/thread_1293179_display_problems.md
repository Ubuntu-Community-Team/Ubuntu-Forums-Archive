---
title: "display problems"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by dneril on 2009-10-16
I'm trying to get my Ubuntu up-and-running again. Recently reinstalled 9.04, but I cannot get it to properly load.

Here's what happens. I reach the grub menu, ubuntu starts loading, finishes loading, then... blue screen of death. I can hear the startup music playing, but no visuals. Makes me think that the problem is with my monitor (I'm using a Polaroid flatscreen TV) - but I've had it working before.

I found this:
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

I thought that grub wasn't passing the right resolution to the screen, so I manually set it to load at vga=791, vga=788, vga=787 etc, etc. Each time, same result. The resolution of the load screen changed, but once it finished loading, BSOD. Also tried vga=ask and scan... they didn't help.

Any ideas as to what's going wrong?

---

### Post by OlsenCNC on 2009-10-16
Is this machine Dual Booted w/ Windows?

---

### Post by dneril on 2009-10-17
It is dual-booted w/ windows.

Update: I can't even boot from the installation disk - same thing happens. I tried cycling through the diff't consoles with ctrl+alt+f(x) - no help =(

I'm going to try hooking it up to my roommate's monitor to see if the problem is my monitor.

---

### Post by mosaic2s on 2009-10-18
I had display issue with 9.04 while 8.04 is working fine on the same system. Finally, gave up 9.04. Unless you need 9.04 for a specific reason, stick to 8.04 LTS. It works.

---

