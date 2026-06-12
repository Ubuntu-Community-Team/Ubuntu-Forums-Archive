---
title: "DWL-630G works in Live, but not Install"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by billnvd on 2006-08-20
Ok, here is a problem that is kicking my butt.  I have a Dlink 630.  This card will come up and run fine if I boot from the live breezy cd.  I will not come up if I boot from the installed version of breezy.

I have tried just about everything.  The ath modules load in both live and install.  I ahve manaully loaded the drivers before and after card insertion.  I have booted with the card inserted and removed.

When booting into install, the link and act lights blink alternating, but the card never sees an access point, no signal ever received.

When booting into Live, the lights first come on steady(both) and the card instantly sees the access point as per iwconfig.

I am baffled.  What can the difference be between live and install that casues this?  Basically, it seems that the card is never told to listen, but I cannot figure out why.

Thanks in advance.

---

### Post by billnvd on 2006-08-20
Ok, figured it out.

I was getting a irq 10:nobody cares message during boot from the install that did not occur during the live session.  IRQ 10 was trying to be used by the g630.  By boot time the kernel was reporting 100000 interrupts and I guess freezing the interrupt.

I now boot the install kernel with the following options:
pci=assign-busses
pci=routeirq
acpi=noirq

this does away with the irq 10 issue and allows the 630 to get a working interrupt line.

I guess the live cd boots with similar options or something else in its scripts that bypasses this problem.

bill

---

### Post by Ajith Warrier on 2006-09-10
I have the same problem, but could not figure out how to amend the  install boot options in Xubuntu successfully.

Could you help?

Thanks

---

