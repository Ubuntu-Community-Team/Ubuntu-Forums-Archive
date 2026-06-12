---
title: "Laptop (Ubuntu) to Windows connection with USB link cable"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by guano on 2005-11-12
Hello all.

I have this GeneSys USB link cable and I wanna use it to get some files from a windows machine, but I don't know how to do it. When I plug the cable, dmesg shows:

```
[4301752.887000] usb 2-2: new full speed USB device using uhci_hcd and address 4
```

but none network connection is assigned. According to linux-usb.net, I should see something like this:

```
usb0: register usbnet usb-00:02.0-1.3, Belkin, eTEK, or compatible, c2:91:27:cb:d7:29
```

but I don't...

if I run lsusb, I get:

```
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 05e3:0501 Genesys Logic, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 06a2:0033 Topro Technology, Inc.
Bus 001 Device 001: ID 0000:0000
```

so the cable is recognized.

(just to note, usbnet is loaded)
My questions:

How to set up this connection? what should I do to get it working?

thanks all.

---

### Post by Remmelas on 2005-11-13
You'll need to find a usbnet driver for your windows machine as well.  I'd link one, but i don't know of any free(as in beer or otherwise) ones.

---

