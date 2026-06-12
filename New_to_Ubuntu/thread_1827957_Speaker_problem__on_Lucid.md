---
title: "Speaker problem  on Lucid"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-18
I'm having a sound problem with my machine. Here is the output of "lspci":
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

For the time being, I am able to listen to by using an earphone, but still problematic when using internal speaker..

Any idea?

---

### Post by Daveth on 2011-08-18
what do you mean by "problematic? Do you get any sound at all through the internal speakers? Or does it come and go? Is this recent? What make is your laptop/pc, as it may be a hardware issue with Linux. Might be worth also looking to see if the BIOS has options for sound.

---

### Post by alfa_80 on 2011-08-18
> **Daveth said:**
> what do you mean by "problematic? Do you get any sound at all through the internal speakers? Or does it come and go? Is this recent? What make is your laptop/pc, as it may be a hardware issue with Linux. Might be worth also looking to see if the BIOS has options for sound.

"Problematic" in my case means it works with earphone/headphone but it doesn't work with internal speaker. This happens after I reinstalled my ubuntu. Before ubuntu reinstallation, both ways (internal speaker+earphone) work out of the box..

Thanks anyway..Any idea?

---

### Post by alfa_80 on 2011-08-19
Thanks a lot for the concern, everything[(internal+external) (mic+speaker)] is now working out of the box after upgrading to the latest linux kernel today :-)

---

