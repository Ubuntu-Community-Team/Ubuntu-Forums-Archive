---
title: "Epson rx520 scanner not found by xsane in 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by rue1341 on 2009-11-05
I have just done a clean install of 9.10 64bit (I have tried on a 32bit as well)and cannot get my Epson rx520 all-in-one to scan.
I have been using it in 9.04 and before all I had to do was to make sure that libsane-extras & sane-utils were installed then it just worked.
I have tried System-Admin-User & Groups. Ticked the boxes in "saned" properties.
I have tried System-Admin-Printers. Enabled and shared the rx520
Run ls -l /dev/usb/ to show it is connected
Checked the epson2 backend/drivers are ok for the rx520
Tried using
ALT-F2 to run these commands:

gedit /lib/udev/rules.d/50-udev-default.rules
gksu gedit /etc/udev/rules.d/51-scanner.rules

Copy the line you want to change to the new file. Now, there are two ways to change it. Either 664 -> 666, which gives everyone access (possibly bad, but I'm sure it will work), or add

Code:

GROUP="admin",

I end up with this in /51-scanner.rules

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="admin"

I used "sudo sane-find-scanner" which gave:-

found USB scanner (vendor=0x04b8 [EPSON], product=0x081a [USB2.0 MFP(Hi-Speed)]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
andrew@andrew-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

Can any one help?

---

### Post by Bln on 2009-11-06
I've a perfection V10, but it's the same here: nothing works, the scanner is detected by lsusb, and even if I chmod 777 it (on its usb bus), I get this error too, with xsane AND iscan. Is a change to dbus causing that? Thanks for any clue on this ;)

---

### Post by mconrad on 2010-11-20
Same thing, same messages, same good detect, but try to scan - nothing.

This was with 10.04 Lucid Lynx and Epson Perfection 4490 Photo

---

