---
title: "Flash Drive Help!!"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-03-31
My friend's 8 GB PNY Flash drive can't be seen when he plugs it into his windows machine, and he gave it to me to try to fix. My Ubuntu 10.10 and my Mac OS X 10.6 won't see it either. HELP!!!!!](*,)

---

### Post by TeoBigusGeekus on 2011-03-31
Can you post us the output of
```
lsusb
```
before and after you've plugged it in?

---

### Post by CharlesA on 2011-03-31
Try that ^

I have a feeling the drive is toasted.

---

### Post by doppel.ganger on 2011-03-31
After:


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Before:


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by PCNetSpec on 2011-03-31
Install **gnome-disk-utility** and/or **gparted**, and see if either of those can see it.

if so, just format as FAT32

If not, unplug the USB stick, replug it, then see if:

```
dmesg | tail
```

gives you any clues.

---

### Post by doppel.ganger on 2011-03-31
I can't format it. It doesn't pop up anywhere!

---

### Post by TeoBigusGeekus on 2011-03-31
> **doppel.ganger said:**
> After:


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Before:


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Not recognised at all...
Your friend can have my condolences, sorry...

---

### Post by doppel.ganger on 2011-03-31
Any way at all?
Could you tell me what that output meant? I'm in my early teens but have been with ubuntu a while...

---

### Post by TeoBigusGeekus on 2011-03-31
> **doppel.ganger said:**
> Any way at all?

I'm afraid not...
The device isn't even recognised as a usb device (as you've seen by the lsusb command).
I hope there wasn't anything (too) important in it.

---

### Post by TeoBigusGeekus on 2011-03-31
> **doppel.ganger said:**
> Could you tell me what that output meant? I'm in my early teens but have been with ubuntu a while...

lsusb: list usb devices attached to your system

For more info
```
man lsusb
```

---

### Post by doppel.ganger on 2011-03-31
Thanks for all the help. If there was any way to friend you on ubuntu forums, I would. Thanks!

---

