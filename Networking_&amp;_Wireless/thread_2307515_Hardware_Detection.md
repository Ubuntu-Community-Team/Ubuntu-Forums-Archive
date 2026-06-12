---
title: "Hardware Detection"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by Terone on 2015-12-25
So the deal is that I got a Mobile Broadband Dongle. Curiously enough, whenever I boot the computer with the Dongle connected, it would show a connectable network from my list of network connections. But if, say for example, I connect my Dongle after everything is booted, no connections would be displayed and it's as if my dongle is not connected at all.

Now I'm not looking for a fix per se, I'm looking for some help understanding what's up. Is this to with the Dongle being detected as a modem? How would I go about probing it? Would love any help on this.

---

### Post by ian-weisser on 2015-12-25
Start with dmesg (hardware recognition) and udev (rules for specific hardware)

---

### Post by Bucky Ball on 2015-12-25
*Thread moved to **Networking & Wireless**.*

As you can boot with the dongle in and it works, no issue with hardware. You'll have better luck here. :)

---

### Post by Terone on 2015-12-27
Alrighty, dmesg for when the Dongle is detected as a USB

```
[   96.721381] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[   96.851360] usb 1-1: New USB device found, idVendor=12d1, idProduct=1446
[   96.851365] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[   96.851368] usb 1-1: Product: HUAWEI Mobile
[   96.851370] usb 1-1: Manufacturer: HUAWEI Technology
[   96.936333] usb-storage 1-1:1.0: USB Mass Storage device detected
[   96.938521] scsi host2: usb-storage 1-1:1.0
[   96.938727] usb-storage 1-1:1.1: USB Mass Storage device detected
[   96.939053] scsi host3: usb-storage 1-1:1.1
[   96.939158] usbcore: registered new interface driver usb-storage
[   97.032437] usbcore: registered new interface driver uas



```

And when it is properly connected. (Allows me to connect to the internet)

```
[  171.700560] usb 1-1: new high-speed USB device number 9 using xhci_hcd
[  171.891594] usb 1-1: New USB device found, idVendor=12d1, idProduct=1436
[  171.891598] usb 1-1: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[  171.891600] usb 1-1: Product: HUAWEI Mobile
[  171.891601] usb 1-1: Manufacturer: HUAWEI Technology
[  171.895523] usb-storage 1-1:1.0: USB Mass Storage device detected
[  171.895701] usb-storage 1-1:1.1: USB Mass Storage device detected
[  171.895844] usb-storage 1-1:1.2: USB Mass Storage device detected
[  171.895955] usb-storage 1-1:1.3: USB Mass Storage device detected
[  171.896057] usb-storage 1-1:1.4: USB Mass Storage device detected
[  171.896156] usb-storage 1-1:1.5: USB Mass Storage device detected
[  171.896384] scsi host13: usb-storage 1-1:1.5
[  171.896499] usb-storage 1-1:1.6: USB Mass Storage device detected
[  171.896726] scsi host14: usb-storage 1-1:1.6
[  171.936622] usbcore: registered new interface driver usbserial
[  171.936683] usbcore: registered new interface driver usbserial_generic
[  171.937093] usbserial: USB Serial support registered for generic
[  171.968904] cdc_ether 1-1:1.1 wwan0: register 'cdc_ether' at usb-0000:00:14.0-1, Mobile Broadband Network Device, 02:50:f3:00:00:00
[  171.968962] usbcore: registered new interface driver cdc_ether
[  172.021750] usbcore: registered new interface driver option
[  172.021817] usbserial: USB Serial support registered for GSM modem (1-port)
[  172.022275] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  172.023019] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  172.023182] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2


```

And I've only been using Ubuntu for two weeks now, so I'm not familiar with udev commands. Could someone explain that to me? Or at least point me towards some resources to read up on?

---

### Post by Bucky Ball on 2015-12-27
With dongle plugged in:

```
sudo lshw -C network
```

Post the output back here.

---

### Post by Terone on 2015-12-27
Also I would really appreciate if someone would explain the process a bit more in-depth. I'd like to learn more about this.

---

### Post by Terone on 2015-12-27
sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: eth0
       version: 12
       serial: f0:76:1c:be:97:59
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff
  *-network DISABLED
       description: Wireless interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 30
       serial: d8:5d:e2:4c:58:8f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=3.19.0-42-generic firmware=WLAN.TF.1.0-00267-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:c4200000-c43fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 02:50:f3:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes


```

---

### Post by Vladlenin5000 on 2015-12-27
```
*-network DISABLED        [COLOR=#008000]description: Ethernet interface[/COLOR]
       physical id: 1
       logical name: wwan0
       serial: 02:50:f3:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 [COLOR=#006400]firmware=Mobile Broadband Network Device[/COLOR] link=no multicast=yes
```

This suggests your modem is one of the new ones that emulate Ethernet over USB, like the Huawei E3131 (???).
Not that it helps but hopefully will give someone some idea...

---

### Post by Terone on 2015-12-27
Here's the thing. Whenever I'm hot plugging on a fresh boot, it will always detect it as a USB. This may be the case after removing and plugging back again. But once it properly detects it as a "modem" or an actual dongle, it will always detect it as a dongle. Regardless of how many times I'm plugging and unplugging.

```
 lsusb
Bus 001 Device 011: ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode) 
```

A fresh boot would clear this up and the process happens all over again.

Another titbit is if it is plugged in while the computer initially boots, it detects it as a dongle.

---

### Post by Terone on 2016-01-15
I feel that I have narrowed it down to these two areas.

```
[   31.095745] usb 1-2: New USB device found, idVendor=12d1, idProduct=1446
[   31.095748] usb 1-2: New USB device strings: Mfr=3, Product=2, SerialNumber=0
```

When detected as a USB and 

```
[  184.101041] usb 1-2: New USB device found, idVendor=12d1, idProduct=1436
[  184.101045] usb 1-2: New USB device strings: Mfr=4, Product=3, SerialNumber=0

```

When it's detected as a dongle.
Is it physically possible for me to change the idProduct or the USB device strings of a USB device? 
Just wanna test it out if there is.

---

### Post by Terone on 2016-01-16
After strolling around the internet, I wanna know if I'm going down the right path. Would the command in this situation be usb_modswitch? And if so, how do I use this command? Bear in mind that I've only just started using linux for around three weeks.

---

### Post by Terone on 2016-01-23
Bump.
Assigning device strings, anyone?

Edit: For refreshers, I want to know how to use "usb_modeswitch" properly. With this I can change the USB device strings of the idProduct.

---

### Post by Terone on 2016-02-20
Well, I fixed the problem myself.

Since it was one of them huawei dongles I used the command

```
sudo usb_modeswitch -v 12d1 -p 1446 -J
```

-v 12d1 is the vendor of said device and -p 1446 is the product id

The option -J is a special producer applied specifically to newer models of huawei devices.
FYI for those with the same problem.

---

### Post by Bucky Ball on 2016-02-20
Thanks for sharing, marking as solved and well done finally fixing. I'm having some similar issues with a wifi dongle and I've tried everything so might try this now. :)

---

