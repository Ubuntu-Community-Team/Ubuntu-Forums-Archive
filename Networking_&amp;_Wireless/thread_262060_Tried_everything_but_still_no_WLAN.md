---
title: "Tried everything but still no WLAN"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by BlackTiger on 2006-09-21
Please help, I tried everything I could find but stil no WLAN...
This is my card, found it in google, because on the card is nothing more then a FCC ID

E-Tech Wireless 11Mbps LAN PC Card
Model: Am1772 / WLPC05
FCC ID:PQP-WP288P

first installed network-manager,
then ndiswrapper, driver etc...
it says driver present, hardware present...
but nothing works.

look to the next...

```
root@laptop:/etc/ndiswrapper/netam772# modprobe ndiswrapper
root@laptop:/etc/ndiswrapper/netam772# dmesg | grep ndiswrapper
[17182356.648000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17182356.704000] ndiswrapper: driver netam772 (Advanced Micro Devices,01/26/2004,2.2.0.0) loaded
[17182356.704000] ndiswrapper (KeCancelTimer:711): invalid wrap_timer
[17182356.704000] ndiswrapper (miniport_init:240): couldn't initialize device: C0000001
[17182356.704000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[17182356.704000] ndiswrapper (miniport_halt:271): device eb195260 is not initialized - not halting
[17182356.704000] ndiswrapper: device eth%d removed
[17182356.704000] ndiswrapper: probe of 0000:02:00.0 failed with error -22

```

pcmia is working

```
root@laptop:/etc/ndiswrapper/netam772# cardctl ident
Socket 0:
  product info: "", "", "", ""
  manfid: 0x0001, 0x0000
  function: 6 (network)
```

```
root@laptop:/etc/ndiswrapper/netam772# lsmod | grep pcmc
pcmcia                 40508  0
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
```

and the conf file in /etc/ndiswrapper/netam772

```
Environment|1
BusType|5
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Advanced Micro Devices,01/26/2004,2.2.0.0

ProductName|Am1772(tm) Wireless LAN Chipset
ProductVersion|RDK-2-2-0-0
VendorName|Advanced Micro Devices
```

Please help

---

### Post by BlackTiger on 2006-09-21
new update...

when I remove, and insert the card again i get with dmesg

```
[17197358.876000] pccard: card ejected from slot 0
[17197385.588000] pccard: CardBus card inserted into slot 0
[17197385.588000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17197385.588000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 169
[17197385.588000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17197385.588000] ndiswrapper (KeCancelTimer:711): invalid wrap_timer
[17197385.588000] ndiswrapper (miniport_init:240): couldn't initialize device: C0000001
[17197385.588000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[17197385.588000] ndiswrapper (miniport_halt:271): device e2fde260 is not initialized - not halting
[17197385.588000] ndiswrapper: device eth%d removed
[17197385.588000] unregister_netdevice: device eth%d/e2fde000 never was registered
[17197385.588000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17197385.588000] ndiswrapper: probe of 0000:02:00.0 failed with error -22
```

---

