---
title: "Help viewing and connecting to wireless networks"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by SlaughterDog on 2008-11-24
I just got a little netbook by Acer, an Aspire one. It includes a wireless network card. However, I can't connect. Part of it may be because I don't how. The network icon in the system tray lists only wired connections. The hardware drivers shows that I've got the drive for the card in use. When I first fired up the computer, it had a bloated Windows installed but it did actually show wireless networks. So, how might I get this to work here in Ubuntu? There's a button on the computer to turn it on and off, though I cannot tell if it's on or off. 

Here's what lspci says about it:
```

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Foxconn International, Inc. Device e008
	Flags: fast devsel, IRQ 18
	Memory at 55200000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

```

---

### Post by SlaughterDog on 2008-11-25
More info:
sudo lshw -C network shows that it's unclaimed
```

*-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

But then how come it says there's drivers being used for it in the drivers control panel?

edit: I installed the windows driver but of course it does not work.

---

### Post by SlaughterDog on 2008-11-25
More info: the hardware drivers control panel says there is a driver provided by the Ubuntu community activated, but not in use. What does this mean? How do I get it in use?

I also noticed the button that should enable/disable wi-fi can be mapped in the keyboard shortcuts control panel, but there's no setting in that panel to turn on/of a wifi card. How else would I turn it on then?

---

### Post by SlaughterDog on 2008-11-26
Problem solved by installing ath5k drivers.

---

