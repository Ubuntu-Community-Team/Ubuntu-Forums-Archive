---
title: "wireless package needed or not?"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by wdbreen on 2007-08-28
Gday,
I have a question regarding the IPW2100 driver.  I have just installed an INTEL/PRO WIRELESS 2100 3B MINI-PCI card into my IBM Thinkpad R40 laptop.
Things seem to be working well (even though i'm nowhere near a hotspot!) by seeing the iwconfig output as a ETH1 with power on 16dbm.  The thinkpad wireless light is coming on and showing that it is in roaming mode.

My question is, do i need to download the ipw2100-source package from the repositories or does this type of driver now get rolled into the latest kernel as an installed module automatically?

Cheers

Breeny

---

### Post by Steve1961 on 2007-08-28
> **wdbreen said:**
> Gday,
I have a question regarding the IPW2100 driver.  I have just installed an INTEL/PRO WIRELESS 2100 3B MINI-PCI card into my IBM Thinkpad R40 laptop.
Things seem to be working well (even though i'm nowhere near a hotspot!) by seeing the iwconfig output as a ETH1 with power on 16dbm.  The thinkpad wireless light is coming on and showing that it is in roaming mode.

My question is, do i need to download the ipw2100-source package from the repositories or does this type of driver now get rolled into the latest kernel as an installed module automatically?

Cheers

Breeny

The driver is built into Ubuntu, along with the necessary firmware.  You shouldn't need to do anything else other than connecting to a network with network manager.

---

