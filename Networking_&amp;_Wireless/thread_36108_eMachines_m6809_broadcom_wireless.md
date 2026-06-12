---
title: "eMachines m6809 broadcom wireless"
date: 2005-05-21
forum: Networking &amp; Wireless
---

### Post by droric on 2005-05-21
No matter what i try to do short of noapic pci=noacpi nopcmcia will allow my network card to boot in ubuntu hoary 5.04 amd64.  Im pretty sure ive installed everything correctly.  The wierd part is if i do a fresh install of hoary, install kernel compilier, g++, ndiswrapper then the drivers it works fine.  As soon as i reboot the computer it hangs at loading network interface and the status light on my laptop for the wireless network just blinks rapidly.  I have not been able to get this to work at all.  I have the bcm4306 chipset in here.
    I get some other errors like ACPI: PCI Interrupt Link [ALKC] disabled and referenced. ACPI: Bios reported IRQ 0, using IRQ 23. as well as "irq 18: nobody cared (try booting with the "irqpoll" option. Help, ive gotten nowhere in the last three days ive been trying to get this to work.

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=droric]No matter what i try to do short of noapic pci=noacpi nopcmcia will allow my network card to boot in ubuntu hoary 5.04 amd64.  Im pretty sure ive installed everything correctly.  The wierd part is if i do a fresh install of hoary, install kernel compilier, g++, ndiswrapper then the drivers it works fine.  As soon as i reboot the computer it hangs at loading network interface and the status light on my laptop for the wireless network just blinks rapidly.  I have not been able to get this to work at all.  I have the bcm4306 chipset in here.
[/QUOTE]

Are you using the 64 bit version of Ubuntu? That might be the problem.

---

### Post by droric on 2005-05-21
yeah im using the 64 bit version of ubuntu

---

