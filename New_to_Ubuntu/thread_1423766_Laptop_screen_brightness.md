---
title: "Laptop screen brightness"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by tsiliman on 2010-03-07
Hello everybody.
When I switch on my laptop using AC power, the screen's brightness is 100%, so it is OK for me. But when I switch on using the battery, the brightness drops down almost to 50%. If I plug/unplug the AC power during the operation, nothing happens.
All I want is the brightness to be at 100% all the time.
Thanks 

Ubuntu 9.10
Fujitsu Siemens PA1538

---

### Post by spiky001 on 2010-03-07
hi have you looked in system preferences power management there is an option under battery by default to reduce screen brightness when on battery

---

### Post by Arkitekt on 2010-03-07
Do the function keys work for raising and lowering brightness when on battery power?

if your system is compatible with xbacklight then perhaps you can install it and use it to set your levels to 100% all the time, only problem I see is gnome-power-manager overriding and settings set by xbacklight.

I believe there may be a script out there somewhere that would fix this but It might take some searching to find it

---

### Post by tsiliman on 2010-03-07
> **spiky001 said:**
> hi have you looked in system preferences power management there is an option under battery by default to reduce screen brightness when on battery

Yes, I have. It doesn't work, unfortunately.

---

### Post by tsiliman on 2010-03-07
> **Arkitekt said:**
> Do the function keys work for raising and lowering brightness when on battery power?

if your system is compatible with xbacklight then perhaps you can install it and use it to set your levels to 100% all the time, only problem I see is gnome-power-manager overriding and settings set by xbacklight.

I believe there may be a script out there somewhere that would fix this but It might take some searching to find it

The function keys, which are F8 and F9, worked only after installing the latest BIOS from Fujitsu Siemens. When pressing them, what I get is a small graphic bar at the top right corner of the screen. They have no effect, though. I'll try installing xbacklight.

---

### Post by tsiliman on 2010-03-07
I installed xbacklight, but when trying to run it, I get "No outputs have backlight property". That means that my laptop is not compatible with xbacklight?

---

### Post by tsiliman on 2010-03-07
I also installed the latest 190.53 nvidia drivers, but nothing changed. :sad:

---

### Post by sandyd on 2010-03-07
this is because of the acpi (kernel) problem. it has been fixed in lucid.

---

### Post by realTHK on 2010-06-18
I have the same problem on 64 bit Lucid running on an HP 6830s: the keyboard shortcut (Fn + F7, Fn + F8 ) pops up a brightness setting slider, but it does not change in any direction. 

The command
```
echo -n VALUE > /proc/acpi/video/DGFX/LCD/brightness
```works OK (though it accepts "VALUE" only in steps of 10),  and under Power Management, the "Display Brightness" slider also works fine (and it seems to work in 1% steps!)

Is it perhaps the Power Management itself that blocks brightness from change?

I suspect it, because the slider that pops up when Fn+F7 is pressed, shows the correct value that is set in Power Management - but it always stays on that value...

---

