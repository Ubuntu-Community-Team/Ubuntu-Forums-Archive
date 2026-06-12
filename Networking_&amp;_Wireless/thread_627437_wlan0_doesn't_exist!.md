---
title: "wlan0 doesn't exist!"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by isecore on 2007-11-30
I'm trying to setup an old laptop with Xubuntu Gutsy. Everything installed like a charm - except that the PC Card wlan doesn't exist as far as the system is concerned.

It's an SMC something-or-other with the  ADMtek ADM8211 chipset.

The output of lspci is as follows:
```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

00:04.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)

00:04.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)

00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)

00:09.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)

00:09.1 Serial controller: Agere Systems LT WinModem

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

02:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 20)

```

Now, this card worked excellent under regular Ubuntu Feisty, but I decided to reformat the machine with Xubuntu since it's slightly less taxing (the machine is a laptop, 450Mhz P3) but after installation I find that wlan0 doesn't exist! The only network devices present is eth0 (the wired connection) and lo. All the kernel-modules seem to be loaded, but I'm not sure which module is required for this card to function.

Any help or input would be appreciated!

---

### Post by rustybronco on 2007-11-30
looks like ndis and drivers.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)  (number 22 on that page )

---

### Post by isecore on 2007-11-30
I don't really see why I would need ndiswrapper since it worked fine out of the box with both Edgy and Feisty, complete with native drivers. Yet a fresh install of Xubuntu won't show wlan0, or even that the card is active - only that it's recognized and all the kernel-modules seem to be loaded.

---

### Post by rustybronco on 2007-11-30
The module doesn't appear to be included in the 7.10 kernel, you could try to find it and compile it your self ( I couldn't find it, and I looked )

---

### Post by isecore on 2007-11-30
Well, that would explain it all.

How stupid isn't that? Not including a simple little kernel module? I'm getting a bit irritated by how each new release of Ubuntu somehow breaks something that worked fine on older versions.

---

### Post by rustybronco on 2007-11-30
> **isecore said:**
> Well, that would explain it all.

How stupid isn't that? Not including a simple little kernel module? I'm getting a bit irritated by how each new release of Ubuntu somehow breaks something that worked fine on older versions.I think ubuntu is very good for only about 3 years old, 7.10 is a lot more stable on my desktop than 7.04 was, but on my laptop (1999 vintage ) I had acpi issues with 7.10 so for now its 7.04 on it.
I'll see if I can find the module.

---

### Post by isecore on 2007-11-30
> **rustybronco said:**
> I think ubuntu is very good for only about 3 years old, 7.10 is a lot more stable on my desktop than 7.04 was, but on my laptop (1999 vintage ) I had acpi issues with 7.10 so for now its 7.04 on it.
I'll see if I can find the module.

I agree that Ubuntu has come a long way, and overall that it's really showing what a good distro should be like on the desktop, but sometimes I wonder about some decisions, such as not including a kernel module/driver that was included previously. This breaks the usage for a lot of people, including me - and not including a nice, neat way of acquiring those "obsolete" modules makes it even worse.

---

### Post by isecore on 2007-11-30
Well, I've downloaded the source from linuxwireless.org and I'll try compiling the kernel module from there...

edit: that solved it, now the module is properly loaded.

---

