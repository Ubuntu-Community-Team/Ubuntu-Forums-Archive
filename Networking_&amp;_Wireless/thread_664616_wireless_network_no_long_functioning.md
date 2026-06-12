---
title: "wireless network no long functioning"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Rever75 on 2008-01-11
OK,
  Not sure what is happening here but my wireless network had been working fine for sometime. Now for the past 2 wks I cannot get it working. I am using ndiswrapper and I also have tried wireless USB devices. The card is seen and loaded but dmesg always gives this.... 
> [11912.904000] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[11912.904000] usbcore: deregistering interface driver ndiswrapper
[11916.524000] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[11916.592000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[11916.592000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[11916.592000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[11916.600000] ndiswrapper: using IRQ 17
[11916.804000] wlan0: ethernet device 00:19:7e:cc:96:77 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[11916.804000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[11916.808000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[11916.816000] usbcore: registered new interface driver ndiswrapper
[11916.836000] ADDRCONF(NETDEV_UP): eth1: link is not ready

I can not find any wireless networks in either KDE or Gnome network manager nor can I create manual connection. I also cannot use wlassistant to find any networks. 
> $iwlist scan ...
o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan result


Any help would be great.
[11916.836000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

