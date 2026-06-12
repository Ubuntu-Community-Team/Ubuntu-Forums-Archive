---
title: "USB Mouse(Optical) Freezes at random times."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-08-16
Hi there!

I'm having some major problems with my USB optical mouse. At random times (although it seems to happen quicker when I use the mouse wheel) my mouse will just freeze with the optical red light still on. Unplugging the mouse and replugging it doesn't fix it, in fact, after the replug the laser doesn't even turn on.

I only have the problem with USB Mice, using a PS/2 mouse I have absolutely ZERO problems.

I think these could be the problem:

    * My motherboard is messed up.
    * My USB Mouse is messed up (but why would it disable on Linux and work perfectly on Windows XP/Vista)


Any help would be greatly appreciated. I like this distro but this is the only thing holding me back.

---

### Post by northern lights on 2009-08-16
If your mouse works under Windows, you can rule out a hardware failure.

Hence, it must be an OS-specific problem. I have no idea what could be causing the freezes. More info would be useful.

How do you fix it? I.e. re-login / reboot

Please post make and model.

Also post the output of ```
lsusb
``` with the device connected.

---

### Post by papuccino1 on 2009-08-16
Only way to fix it is to do a hard forced reboot.

Output of **lsusb**:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Also, when I turn on my PC, while the giberish is loading on the black screen it gets stuck for a while on some ACPI error, something about bla bla bla not being connected. Could this be what's causing the problem?

---

### Post by Pappy1911 on 2009-08-18
My mouse has a access cover to install the batteries.

The cover is underneath, and I don't have it in place. Invariably, I sometimes bump the mouse and the batteries become displaced, thus no mouse power..

But, on mine, Logitech, I need to synchronize the mouse and receiver when batteries are replaced...

Any help?????

---

