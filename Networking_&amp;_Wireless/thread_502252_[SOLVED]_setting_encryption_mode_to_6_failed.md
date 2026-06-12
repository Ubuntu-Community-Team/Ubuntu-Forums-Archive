---
title: "[SOLVED] setting encryption mode to 6 failed"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-16
I see that an error is reported  (last line in bold)

setting encryption mode to 6 failed   -- is this important? The web is working very well, thank you.

james@Maplewood:~$ tail /var/log/messages
Jul 17 19:08:28 Maplewood kernel: [  123.116000] lo: Disabled Privacy Extensions
Jul 17 19:08:28 Maplewood kernel: [  123.116000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 17 19:08:34 Maplewood gconfd (james-5030): Resolved address "xml:readwrite:/home/james/.gconf" to a writable configuration source at position 0
Jul 17 19:10:42 Maplewood kernel: [  257.540000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Jul 17 19:10:43 Maplewood kernel: [  257.832000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
Jul 17 19:10:43 Maplewood kernel: [  258.128000] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
Jul 17 19:10:44 Maplewood kernel: [  259.220000] wlan0: ethernet device 00:0f:66:ef:61:b4 using NDIS driver: wusb11v4, version: 0x36e, NDIS version: 0x501, vendor: 'M4301 NDIS Miniport Driver', 13B1:000B.F.conf

**Jul 17 19:10:44 Maplewood kernel: [  259.220000] ndiswrapper (set_encr_mode:694): setting encryption mode to 6 failed (C00000BB)**

---

### Post by Mark_in_Hollywood on 2007-07-25
THREAD CLOSED.

This has been resolved by reinstalling Feisty.

---

