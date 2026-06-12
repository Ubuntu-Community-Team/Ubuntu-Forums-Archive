---
title: "Keyboard/Mouse issue"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by mnix on 2010-11-20
Hey all,  it's me again.

I'm having an odd issue where Ubuntu 10.10 (i386) is randomly not recognizing the keyboard/mouse on startup.

Here's what happens:
I turn on the computer.  It loads to the login screen, however, the choices at the bottom for keyboard layout, ect. is gone.  I try to click my mouse, nothing happens.  I try to hit enter on the keyboard, nothing happens.  I try to re-establish connection (this does not appear to be the issue, since the issue persists)  I try unplugging/replugging/plugging into a different USB port...same thing.

Here is the mouse/keyboard set I'm using : [http://www.logitech.com/en-us/keyboards/keyboard-mice-combos/devices/7306](http://www.logitech.com/en-us/keyboards/keyboard-mice-combos/devices/7306)

I then reboot, rinse, repeat.  I dunno if it's ever come up correctly again after a reboot, but I do know that if I power it down and leave it off for a bit, it comes back up, and I can login no issue.

---

### Post by lisati on 2010-11-20
A shot in the dark here: you might want to check your BIOS settings to see if you can enable USB Legacy mode.

---

### Post by 311005901 on 2010-11-20
The link you posted looks like the keyboard and mouse set is bluetooth. Someone with more infos on that might be able to help you.

---

### Post by honeybear on 2010-11-21
> **mnix said:**
> Hey all,  it's me again.

I'm having an odd issue where Ubuntu 10.10 (i386) is randomly not recognizing the keyboard/mouse on startup.

Here's what happens:
I turn on the computer.  It loads to the login screen, however, the choices at the bottom for keyboard layout, ect. is gone.  I try to click my mouse, nothing happens.  I try to hit enter on the keyboard, nothing happens.  I try to re-establish connection (this does not appear to be the issue, since the issue persists)  I try unplugging/replugging/plugging into a different USB port...same thing.

Here is the mouse/keyboard set I'm using : [http://www.logitech.com/en-us/keyboards/keyboard-mice-combos/devices/7306](http://www.logitech.com/en-us/keyboards/keyboard-mice-combos/devices/7306)

I then reboot, rinse, repeat.  I dunno if it's ever come up correctly again after a reboot, but I do know that if I power it down and leave it off for a bit, it comes back up, and I can login no issue.

please give more info: 

dmesg
while plugin in

is it usb cable or bluetooh to the pc ?

---

### Post by mnix on 2010-12-27
> **lisati said:**
> A shot in the dark here: you might want to check your BIOS settings to see if you can enable USB Legacy mode.

I can check, would I have this problem in windows then also?  I'm dual-booting with winXP, and I even had this problem with GRUB for a bit....I tried changing batteries and everything.  After and update, GRUB seemed to work fine again, but Ubuntu still has the problem.

It's annoying enough that I've switched back to mostly using XP.

---

### Post by mnix on 2010-12-27
> **honeybear said:**
> please give more info: 

dmesg
while plugin in

is it usb cable or bluetooh to the pc ?

I'll try to boot it again when I get back home, but it's neither...sort of.

It's RF with a USB receiver.

---

### Post by mnix on 2011-01-25
Ok, so I think I finally figured this out a few days ago.  I have a Nostromo n52 that was sitting on my desk and apparently something was sitting on one of the keys.  My desk is pretty cluttered so it's hard to tell what.  I eventually had the issue in windows too. 

Sorry for taking up time with this, but thanks for your help!

---

