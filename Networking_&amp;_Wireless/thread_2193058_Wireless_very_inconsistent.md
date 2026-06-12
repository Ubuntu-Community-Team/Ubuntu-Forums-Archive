---
title: "Wireless very inconsistent"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by fourhendrik on 2013-12-11
Every 10 minutes or my network stalls and I can't even ping anymore. The problem goes away just by waiting 1-2 minutes. The issue recurs every 5-10 minutes.

Any help appreciated.

Are there any known problems with the driver for card below?

  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 80:56:f2:80:68:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.11.0-14-generic firmware=N/A ip=192.168.1.140 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:5000(size=256) memory:d3600000-d3603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0f:00.0
       logical name: eth0
       version: 0c
       serial: a0:d3:c1:72:f7:30
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:d3500000-d3500fff memory:d3400000-d3403fff



Best Regards,
Hendrik Greving

---

### Post by varunendra on 2013-12-12
Welcome to the forums fourhendrik !

Where have you installed this driver from?

Please try a parameter temporarily -
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee swenc=1 fwlps=0
```
..then try to connect and see if it is more stable now. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Martyd16 on 2014-04-24
[QUOTE=varunendra;12871890]

Please try a parameter temporarily -
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee swenc=1 fwlps=0
```


I was having inconsistencies as well, I ran these codes and now my onboard wifi doesn't connect!

---

### Post by varunendra on 2014-04-25
The first command removes the driver, so the wireless will naturally be disabled with it. The second one reloads the driver with the given parameters, which is supposed to make the connectivity better. If it fails to do so, it shouldn't hurt either.

In any case, reverting is just a matter of a reboot. So if your wifi doesn't connect even after a reboot, this is 100% coincidental and 200% unrelated to the commands above.

If you need help, please start a new thread and post back the wireless_script report there as asked in the post that you quoted.

---

### Post by Martyd16 on 2014-04-25
Yes it came back on after reboot, I will post soon the output of the scripts. Thanks!

---

