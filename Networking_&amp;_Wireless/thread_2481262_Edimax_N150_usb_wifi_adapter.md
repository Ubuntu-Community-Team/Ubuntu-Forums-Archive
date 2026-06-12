---
title: "Edimax N150 usb wifi adapter"
date: 2022-11-23
forum: Networking &amp; Wireless
---

### Post by scubascooby on 2022-11-23
I have this box set-up with a working Edimax wifi adapter and a bought a newer Edimax N150 for another box, the same wifi adapter is no longer available.

The new adapter can see the available networks but cannot connect to my (secured) network, it will connect to a local unsecured BT.

I tried blacklisting rtl8xxxu, rtl8192cu and rtl8192c_common drivers one at a time with no luck.


```
$ lsmod | grep rtl
rtl8xxxu              151552  0
rtl8192cu             106496  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        81920  1 rtl8192cu
rtlwifi               114688  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211             1249280  4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu
cfg80211              974848  3 rtlwifi,mac80211,rtl8xxxu
btrtl                  24576  1 btusb
bluetooth             704512  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
```

```

$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: 6d:3b:e5:37:e1:c7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.15.0-53-generic firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:f7800000-f781ffff memory:f7839000-f7839fff ioport:f080(size=32)
  *-network:0
       description: Wireless interface
       physical id: 8
       bus info: usb@1:1.2
       logical name: wlx08beac32f68f
       serial: 08:ba:ac:32:f6:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu driverversion=5.15.0-53-generic multicast=yes wireless=unassociated
  *-network:1
       description: Wireless interface
       physical id: 9
       bus info: usb@1:1.1
       logical name: wlx801f029ab6d6
       serial: 80:1f:02:9f:b6:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=5.15.0-53-generic firmware=N/A ip=192.168.0.11 link=yes multicast=yes wireless=IEEE 802.11
```


driver=r8188eu belongs to the not fully working device.

All suggestions gratefully received.

---

### Post by morrownr on 2022-11-25
Hi,

To see what chipset is in the adapter, you can run the following:

$ lsusb

Here is a site that has a lot of information about usb wifi adapters:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

The list in Main Menu item 2 shows adapters that are plug and play. The list is long and contains a lot of extra information and links to specific adapters.

---

### Post by scubascooby on 2022-11-26
I fixed it but not entirely sure what I did differently.

I plugged in the new Edimax and deleted the connection (again).  It immediately found it again and connected prompting for the password.

It then logged in and worked.

I must have done this 3-4 times on both machines that I tried the adapter in.

---

