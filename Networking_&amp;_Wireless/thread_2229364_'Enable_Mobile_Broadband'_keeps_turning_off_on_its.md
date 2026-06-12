---
title: "'Enable Mobile Broadband' keeps turning off on its own on 12.04LTS."
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by gubbinator on 2014-06-12
'Enable Mobile Broadband' keeps turning off on its own on 12.04LTS.

When I connect, 'Enable Mobile Broadband' comes on, I obtain a connection, but then 'Enable Mobile Broadband' flips off again a few seconds later, causing the connection to be dropped. If I 'Enable Mobile Broadband' without actually attempting to connect, it also flips off on its own a few seconds later.

This has only started happening today, and it doesn't happen using an old 12.04LTS Live CD I have.

Anyone got any ideas please?

---

### Post by gubbinator on 2014-06-12
A bit more information.

The USB modem still works fine on one USB port, but not the other.

On the bad USB port it just endlessly cycles between being visible and invisible within Network Manager.

When I run lsusb, or usb-devices the device is always visible on the USB port.

How do I fix it so it works on both USB ports again?

---

### Post by gubbinator on 2014-06-12
Have reinstalled Network Manager and the problem has gone away!

   sudo apt-get install --reinstall network-manager

---

