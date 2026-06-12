---
title: "DGE-528T recognized, but not running in Hardy (but in Feisty)"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by vimico on 2008-06-16
The card is a few years old and has the following lspci value:  1186:4300

I'm running a triple-boot system:
- Ubuntu Feisty
- a fresh install of Ubuntu Hardy
- and an o/s that shall not be named....

The card is running perfectly under Feisty (and worked out off the box in Dapper, if I recall correctly).

Reviewing the log files showed, that the relevant kernel module r8169 is loaded. From the syslog (full file attached):

> 
Jun 17 00:40:42 ubuntu kernel: [   46.603442] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 17 00:40:42 ubuntu kernel: [   46.603544] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 16
Jun 17 00:40:42 ubuntu kernel: [   46.603947] eth0: RTL8110s at 0xf883af00, 00:13:46:2f:15:ec, XID 04000000 IRQ 16
...
Jun 17 00:40:52 ubuntu kernel: [  126.028940] r8169: eth0: link down
Jun 17 00:40:52 ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Jun 17 00:40:52 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 17 00:40:52 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 17 00:40:52 ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun 17 00:40:52 ubuntu NetworkManager: <info>  Deactivating device eth0. 
...
Jun 17 00:40:52 ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link.


*ifconfig* shows **eth0**. With all counter stay at zero.
The (local) network is not reachable.
A static IP configuration did not help either.
I tried the Hardy Live-CD. Same result.
After rebooting the machine with Feisty, it runs like a charm.

After a few hours of googleing, I did not find someone with a similar problem (at least for the current release).  Some entries in this forum even suggest that people have the card running under 8.04, although very slowly.

Any hints, please?

---

### Post by vimico on 2008-07-05
The problem solved itself.

Don't ask me how...

It is strange enough if things suddenly stop working, but even more strange if they come back to life again for no apparent reason.

---

