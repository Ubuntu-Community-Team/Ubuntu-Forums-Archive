---
title: "Intrepid Ibex wireless problem: Dell Latitude D600"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by gargouille on 2008-11-25
HARDWARE:
Dell Latitude D600
Broadcom BCM4309 (bcm43xx)


PROBLEM:
Wireless connection disconnects.  When shutting down, or rebooting, the following error appears and keeps repeating:  b43-phy0 ERROR: PHY transmission error

kern.log entry:
Nov 25 18:25:57 coruscant kernel: [   92.216246] wlan0: no IPv6 routers present
Nov 25 18:26:02 coruscant kernel: [   96.820027] __ratelimit: 386 callbacks suppressed
Nov 25 18:26:02 coruscant kernel: [   96.820027] b43-phy0 ERROR: PHY transmission error


FIX:
found in Ubuntu help:

3.3.6.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

---

