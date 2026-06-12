---
title: "Intel 2100 wireless card doesn't work (Tecra M2)"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by daehenoc on 2008-07-06
Hi all,

I have a Toshiba Tecra M2 laptop (PTM20A-00RTD, Australian model, could be -OORTD) which I've just installed Ubuntu 8.04 on and I have the dreaded 'Error initializing Symbol' problem with the ipw2100 module is loaded.

Here's the output from lspci:
```
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

Here's the output from dmesg:
```
[   48.873959] ipw2100: eth1: Error initializing Symbol
[   48.873970] ipw2100: eth1: Error loading microcode: -5
[   48.874014] ipw2100: eth1: Failed to power on the adapter.
[   48.874020] ipw2100: eth1: Failed to start the firmware.
[   48.874081] ipw2100Error calling register_netdev.
[   48.874644] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[   48.874663] ipw2100: probe of 0000:02:05.0 failed with error -5
```

I've done some searching on these forums and Googled around and have found other people with the same problem, but haven't found a solution yet.

This laptop does have a physical switch for the wireless card, which is in the 'On' position, and there is a keyboard switch (Fn-F8 ) which I have tried pressing before the module is loaded or after I manually remove ipw2100 and manually reload it, to no avail.

One telling indicator is that I can't get the wireless card to work in Windows, either.  None of the Wireless drivers for XP on the Toshiba Australia web site will make the wireless card work, and I've tried the 2100, 2200 and Atheros drivers off that site.  They either install and the 'Network interface' doesn't get a driver, or they flat out tell me that they don't support the current hardware.

I'm going to try booting other operating systems (I've got a copy of Sabayon linux here somewhere) to see if they operate the wireless card.

Meanwhile, does anyone have any other hints or tips?

Thanks,
Greg

p.s. Ethernet LAN on the laptop is working just fine, that's where I'm making this post from!

---

### Post by daehenoc on 2008-07-07
Hah, I pulled the laptop apart and found out that the card is an Intel 2100**A** WLAN card, which the Intel 2100 driver doesn't appear to support in Windows.  Since the Intel site doesn't have a driver for the 2100A, does anyone know why the driver isn't available on the Intel web site, or where I can get it from?

---

### Post by daehenoc on 2008-07-12
For completeness, I decided that the card was cactus, pulled it out and am using a Netgear WG511 instead :)

---

