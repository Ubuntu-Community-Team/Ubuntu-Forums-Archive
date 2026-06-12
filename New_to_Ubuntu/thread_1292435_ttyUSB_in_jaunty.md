---
title: "ttyUSB* in jaunty"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Spritegeezer on 2009-10-15
I guess I'm just a bit thick but I've been trying to get "ScanTools" an OBD II analysis program running in Wine.  I've found a couple of threads that should be helpful but... One of them refers to a file /dev/ttyUSB* the * is a number.  I've looked in the /dev/ directory and there is no such file as ttyUSB*.  There are tty device files (over eighty) and USB 1.1 and USB 2.0 files but no ttyUSB.  How do I read a USB device as a serial device in jaunty?

---

### Post by lkraemer on 2009-10-16
From your posting it appears you are using a USB to RS-232C (Serial)
device to communicate with the ODB Scanner Hardware.

If you plug in the USB Device, and use the following command in a Terminal
window:
```

lsusb

```
You should get some information on it.

Also, if you have wvdial installed you can use it to scan for the serial
(USB to Serial) device, so you can configure the ODB II software properly.

```

sudo wvdialconf /etc/wvdial.conf

```
will configure wvdial in a Terminal window, after it is installed
with Synaptics Package manager.

Then, when the correct port is determined the ODB II Software can be configured properly, with the port information.

What ODB II software a you using?

I am using Proscan v5.1, but from Win2K, not WINE?  Proscan has a few
BUGS.

You could also try these two options:
VirtualBox, running your Windows version (XP, Vista...) running ODB II Software.
Crossover by Codeweavers.

lk

---

### Post by Spritegeezer on 2009-10-16
What ODB II software a you using?

I want to use ScanXL.  That's what I was using when I was running Windoz on my laptop.  I'm now going completely to Ubuntu, but it isn't easy!  I tried VirtualBox but hooking up to the host USB was just as difficult. - Thanks

---

### Post by lkraemer on 2009-10-16
I am using Proscan v5.1, but from Win2K on an old Compaq 1672 AMD K6
350 MHZ with 192 Meg of RAM.  And ProScan v 5.1 has a few BUGS.

If you install VirtualBox PUEL version (NOT the OSE Version) your USB
will work fine.  You just need to create a filter so it finds the device.
I've had good luck with the USB usage from within VirtualBox.

lk

---

