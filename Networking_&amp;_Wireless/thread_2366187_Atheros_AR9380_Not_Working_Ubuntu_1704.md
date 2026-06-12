---
title: "Atheros AR9380 Not Working Ubuntu 17:04"
date: 2017-07-14
forum: Networking &amp; Wireless
---

### Post by xsario on 2017-07-14
My Atheros Wireless card  is not working on Ubuntu 17.04. Appears as Device ID 168C: ABCD. The  outputs I get from my device are as follows.

Lspci output:
sudo lspci -nnk | grep -iA2 net
1e:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] I211 Gigabit Network Connection [1462:7a32]
    Kernel driver in use: igb
    Kernel modules: igb
1f:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)
23:00.0 USB controller [0c03]: ASMedia Technology Inc. Device [1b21:2142]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a32]

You might be able to help solve the problem.

System features:
Ryzen 1700X
Msi X370 Pro Carbon 
2X8 Gb 3200 Mhz DDR4
And Atheros Ar9380 PCIx1 Wifi card
Link: [https://www.aliexpress.com/item/Atheros-AR9380-AR5BXB12-802-11AC-900Mbps-PCI-E-WiFi-Adapter-With-3-x-6DBi-SMA-Antenna/32660629687.html?](https://www.aliexpress.com/item/Atheros-AR9380-AR5BXB12-802-11AC-900Mbps-PCI-E-WiFi-Adapter-With-3-x-6DBi-SMA-Antenna/32660629687.html?) sPM = a2g0s.9042311.0.0.cq2vv4

---

### Post by wildmanne39 on 2017-07-15
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by BenginM on 2017-07-15
we see two entries for Ethernet devices but no mention of an actual wireless device...!

## have you noticed 

 1f:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)

## it should read:

 1f:00.0 Network controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)

You might need to rescan/rest the PCI device!

```


remove and rescan will allow the kernel to cycler-power the PCI device for example:

echo "1" > /sys/bus/pci/devices/DDDD\:BB\:DD.F//remove
sleep 1
echo "1" > /sys/bus/pci/rescan

where DDDD.BB.DD.F =[Domain:Bus:Device.Function]("https://www.kernel.org/doc/Documentation/ABI/testing/sysfs-bus-pci")



```

Welcome to the forums & Good luck,

---

### Post by wildmanne39 on 2017-07-15
This:
>  1f:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)
is the wifi device, some atheros devices show up as ethernet devices but it is okay, that is not the issue.

---

