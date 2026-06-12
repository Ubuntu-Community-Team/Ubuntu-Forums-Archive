---
title: "Ethernet nic names change when PCI Ethernet card is installed"
date: 2021-08-31
forum: Networking &amp; Wireless
---

### Post by sampsonats on 2021-08-31
I'm relying on Ethernet nic names to stay consistent so automation software will work.  I'm using Ubuntu 20.04 with the gui network manager.

I'm finding that when I plug in a PCI Ethernet card, the names of the on-board Ethernet nics change.

Without the PCI card, the on-board nic names are: eno1, enp2s0, and enp3s0.
When the PCI card is plugged in, the nic names are: eno1, enp1s0, enp3s0, and the PCI nic: enp4s0

The names change as follows:
[FONT=courier new]
[/FONT][TABLE="width: 500, align: left"]
[TR]
[TD]**No PCI Card**[/TD]
[TD][/TD]
[TD]**With PCI Card**[/TD]
[/TR]
[TR]
[TD][FONT=&amp]eno1 [/FONT][/TD]
[TD]->[/TD]
[TD][FONT=&amp]eno1[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=&amp]enp2s0 [/FONT][/TD]
[TD]->[/TD]
[TD][FONT=&amp]enp3s0[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=&amp]enp3so [/FONT][/TD]
[TD]->[/TD]
[TD][FONT=&amp]enp1s0[/FONT][/TD]
[/TR]
[TR]
[TD][/TD]
[TD]->[/TD]
[TD][FONT=&amp]enp4s0[/FONT][/TD]
[/TR]
[/TABLE]
[FONT=courier new]
[/FONT]I thought the whole idea was now network nic names are based on the hardware. It seems the added PCI ethernet card shouldn't change the hardware for the on-board nics and hence, the on-board nic names should not change.

Any ideas what could be going on here??? Any ideas how I can get the nic names to be consistent?

Thanks!

---

