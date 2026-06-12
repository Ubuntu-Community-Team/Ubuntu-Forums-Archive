---
title: "fresh install 14.04, ethernet for first few days, now none"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by kithrup on 2014-10-06
Fresh install of 14.04 LTS in a dualboot with W7. first few days, wrestling with Unity (will save that for a separate post) 

NOW no ethernet, wireless, nothing. W&, no problem.

What gives? What am I missing, and why did 14.04 change its mind about the internet connection?

Thanks for looking

---

### Post by varunendra on 2014-10-06
For starters, please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
sudo lshw -C network
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by oldos2er on 2014-10-06
Moved to Networking & Wireless.

---

### Post by grahammechanical on 2014-10-06
Perhaps you disabled Networking? Or wrestling with Unity, as you put it, you removed something? Perhaps Network Manager? Another command to run is

```
nm-tool
```

Cannot give more advice without more information.

Regards.

---

### Post by kithrup on 2014-10-08
```
 *-network                       description: Ethernet interface        product: RTL8111/8168B PCI Express Gigabit Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:02:00.0        logical name: eth0        version: 03        serial: 48:5b:39:52:d9:d7        size: 10MB/s        capacity: 1GB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=10MB/s        resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable) 
```

---

### Post by varunendra on 2014-10-08
Capacity=1GB/s and speed=10MB/s?

Have you tried replacing the cable with another working one? Is it a Cat-5e or better cable?

While it can be a problem at the driver or the router's firmware side, this kind of downgraded speed is quite often caused due to loose contacts or bad cable, so please double-check them.

Assuming it is not the cable or a bad contact problem, you can try the following on the software front -
```
sudo mii-tool -F 100baseTx-FD eth0
```
Or, if the above gives any errors,
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Then check the speed again -
```
sudo lshw -C network | grep configuration
```
Is the speed '100MB/s' now? If yes, does it solve the problem? If not, please post the full outputs of -
```
sudo lshw -C network
lsmod
nm-tool
```

You can copy-paste the outputs from the terminal to a text file using your mouse cursor (which I think you already did above). Just remember to keep the "Line Ending" compatible to "Windows" while saving the file (the option is given in the "Save" dialogue) if you are opening the file in Windows to post the contents here. This will help preserving the Line Breaks correctly. Otherwise all the contents will pile up in a single long line of text like you post above, making it too hard to interpret. :)

---

