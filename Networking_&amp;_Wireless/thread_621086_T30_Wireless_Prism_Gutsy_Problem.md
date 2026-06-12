---
title: "T30 Wireless Prism Gutsy Problem"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by cat5e on 2007-11-23
I've got a Thinkpad T30 with a Prism 2.5 wireless card. I've really enjoyed using ubuntu and was looking forward to this laptop, but so far the wireless card has thwarted me. Gutsy seems to find the card, but won't do anything with with it. After booting if I open network manager the wireless card is there, but if I close network manager, or change any settings it disappears. The same thing seems to happen if I use iwconfig - the first time I use iwconfig after booting it puts the wireless card at wifi0, but once I'm done with the command it disappears, iow if I use iwconfig again it finds no wireless extensions. I'd desperately love to get this going, any help would be appreciated!

***sudo lshw -C network output***:

 *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical
       configuration: broadcast=yes driver=hostap_pci latency=64 module=hostap_pci multicast=yes

***copy of the /etc/network/interfaces file***

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface wifi0 inet dhcp
wireless-essid CCFB
auto wifi0

***lspci -v***

02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Intel Corporation Wireless 802.11b MiniPCI Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

---

