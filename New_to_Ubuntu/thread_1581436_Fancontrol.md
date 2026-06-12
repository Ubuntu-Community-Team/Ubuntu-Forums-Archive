---
title: "Fancontrol?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by nathan28 on 2010-09-24
I installed ubuntu 10.04 64-bit on a second-hand Lenovo R60. The fan has been running slow, never rising above the "1"/~2700RPM setting even when temperatures get >70C. It could be a hardware issue, but I want to see if I can manually raise the fan RPM first. most of the tutorials I've found are old and I can't figure out what the deal is with the acpi stuff (e.g., the thinkpad-acpi kernel patch) with newer versions of ubuntu, like ThinkWiki's. Here's what I could do:


I tried to run fancontrol and learned I did not have /etc/fancontrol. I ran sensors-detect.

> To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

I allowed it to add coretemp to /etc/modules.

Also ran pwmconfig.

> Found the following devices:
   hwmon0 is acpitz
   hwmon1/device is thinkpad
   hwmon2/device is coretemp
   hwmon3/device is coretemp

Found the following PWM controls:
   hwmon1/device/pwm1
hwmon1/device/pwm1 is currently setup for automatic speed control.
[yes at prompt]
There are no usable PWM outputs.

So I don't have anything to populate /etc/fancontrol with, at least as far as I know. What am I missing?

---

