---
title: "Cross referencing lsusb results with ip or ethtool"
date: 2022-08-03
forum: Networking &amp; Wireless
---

### Post by slippery-slope on 2022-08-03
I have 3 USB Ethernet devices plugged in to my PC. I manually have mapped these to VMs, but given that QEMU uses xml files and looks for a Ethernet device based on it's USB Bus & ID (found via a **lsusb**), is there a away to know or merge the output of **lsusb + ip a** to know what's the MAC address of what USB device at some BUS + ID value?

I can't find some common thread of output between **lsusb **and something like **ip a** to match up to find the information that I'm after.

---

### Post by TheFu on 2022-08-04
If it were, I'd setup a udev rule based on the device ID so it gets the exact same device name each time it is plugged in.
But that's just me.  You do you.

---

