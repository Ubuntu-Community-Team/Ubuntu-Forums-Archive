---
title: "Keyboard not recognized in startup"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by edurning on 2009-01-25
A very weird problem. :(

I installed Ubuntu as a partition in WindowsXP.  However when th OS loader starts the keyboard is locked on me and I can't select an OS, so it times out back to Windows.

Any suggestions.

---

### Post by arochester on 2009-01-25
Is it a USB keyboard? I think, if it is, you need to look at your BIOS to see if you can load a USB keyboard from there...

---

### Post by edurning on 2009-01-25
It is a USB keyoard by Logitech.  What's also weird is that I can get to the bios screen and change the bios, but when it gets to the OS loader no response.

---

### Post by Spherical on 2009-01-25
D'oh! Or... in English...
Probably something in your BIOS, although, I've had the same problem, usually, a few hard-resets (BEFORE GrUB starts booting any OS), try until the Num Lock LED lights up in GrUB, then it should work.

Also check if USB_HID_COMPLIANT (Or anything like that, depends on what version and BIOS type) is set to Enabled or On.

Otherwise, just a standard PS/2 k/b works ;)

---

### Post by edurning on 2009-01-28
Situation fixed.

There was a USB Keyboard section in the bios.  The two options were "OS" and "BIOS".  Since it was set to "OS", I switched it over to "BIOS".  Works like a charm now.

Linux Rocks.

---

