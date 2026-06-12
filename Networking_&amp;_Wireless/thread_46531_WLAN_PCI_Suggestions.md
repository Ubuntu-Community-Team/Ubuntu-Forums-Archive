---
title: "WLAN PCI Suggestions?"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by oracle2025 on 2005-07-05
Hi,

I'm planning to get a WLAN PCI-Board, and I wonder what Model is supported by a recent standard-Kernel without additional patches and drivers?

Any Suggestions?

---

### Post by scoon on 2005-07-05
Hey there, 

I use linksys WMP54Gv4 and I compile ndiswrapper.  It works like a charm. 

regards, 

scoon

---

### Post by oracle2025 on 2005-07-05
Thanks for your advice, but ndiswrapper is not what I refer to as "standard-kernel" ;)

Therfore it's not really an Option.

However I found out that ralink chips are well supported, and that the MSI MS-6834 PC54G2 uses such a chip, I think I'll get one of these.

---

### Post by darrell on 2005-07-05
RT2500 driver is not in the standard kernel, but it is simple enough to get going - there is a howto in the wiki. Additional benefit of this chipset is that WPA is supported in the driver - no need for wpa-supplicant or suchlike. And I managed find a card with this chipset for £15 (in the UK) - Tornado 122

---

### Post by scoon on 2005-07-07
Hey there, 

The linksys uses the ralink chip and it was nothing but problems for me. Ndiswrapper works much better.

regards, 

scoon




[QUOTE=oracle2025]Thanks for your advice, but ndiswrapper is not what I refer to as "standard-kernel" ;)

Therfore it's not really an Option.

However I found out that ralink chips are well supported, and that the MSI MS-6834 PC54G2 uses such a chip, I think I'll get one of these.[/QUOTE]

---

### Post by txgeek on 2005-07-07
I have a Dlink DWL-G520 PCI in my desktop and a Dlink DWL-G650 PC-CARD in my laptop.  Both work "out of the box" on a Hoary install. The only thing I had to do to get either connected to my network was to enter the WEP key.

---

