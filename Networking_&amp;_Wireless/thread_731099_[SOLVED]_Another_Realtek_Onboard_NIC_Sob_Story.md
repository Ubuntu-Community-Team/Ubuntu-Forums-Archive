---
title: "[SOLVED] Another Realtek Onboard NIC Sob Story"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Chris Weaver on 2008-03-21
I'm writing with the hope that some can shed some light on this problem (or even the missing piece of the puzzle!)

I've been try to get Ubuntu 7.10 to connect to my router with about 8 hours now and after reading dozens of posts. I'm nowhere closer but I have some clues. The background is this:

The machine is a HP Pavilion a740uk model with an onboard Realtek 8139 NIC. The machine came preinstalled with XP Home SP2 and therein lies the first clue. I believe I'm suffering from the "Wake on LAN" problem. Unfortunately I've been through the solutions associated with this problem (unplugging the CAT5, reset the BIOS, reset the router) and nothing has worked. I've also tried various boot parameters noapic, pci=routirq, pci=noacpi, and acpi=off.

I've yet to try ndiswrapper or simply buy a new card as I'm sure their must be a solution (and beside trouble shooting is a great way to learn!)

kind regards to those read this.

---

### Post by ugm6hr on 2008-03-21
Maybe this will help: [http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

Does require reinstalling XP tho.

---

### Post by drdos2006 on 2008-03-22
I found I had to reinstall Windows and deselect the Wake-On_Lan before shutting Windows down and re-installing Ubuntu.
regards

---

### Post by Chris Weaver on 2008-03-25
Thanks for the suggestions. I reinstalled XP and disabled the power management option for the onboard NIC, then reinstalled Ubuntu and everything was well!

---

### Post by ugm6hr on 2008-03-25
> **Chris Weaver said:**
> Thanks for the suggestions. I reinstalled XP and disabled the power management option for the onboard NIC, then reinstalled Ubuntu and everything was well!

Glad you got it sorted.

Shame it is suck a nuisance!

PS: I have marked this as solved for you.

In future - you should mark it using "Thread Tools"

---

