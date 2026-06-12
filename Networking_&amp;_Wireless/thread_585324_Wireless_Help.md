---
title: "Wireless Help"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by chris00 on 2007-10-21
Hi there,
My Intel wireless network card/chip has always worked perfectly well. However, recently (in a failed attempt to get xgl and OpenGL apps working, I un-installed all linux-restricted-modules and fglrx and then re-installed them. I rebooted and everything came back up ok apart from the wireless network was not working. When clicking on the wireless network icon I get the message:

SIOCGIFFLAGS error: No such device

If I do a lshw -C network, I get:

```

~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:11:d8:c9:05:e4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.11 firmware=N/A ip=192.168.1.67 latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=24 mingnt=3

```

Notably the wireless device is "UNCLAIMED".

Does anyone know how I can fix this problem? I'm sure I've just uninstalled something I shouldn't have, and not reinstalled it - but the question is - what is it?!!

Help very much appreciated - thanks in advance,
Chris

---

