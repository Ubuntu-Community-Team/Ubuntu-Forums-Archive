---
title: "Wifi problems"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by alexast23 on 2016-08-11
I don't have WiFi for Ubuntu 16.04 Compaq 

```

alexey@alexey-Compaq-615:~$ lspci -knn | grep Net -A2
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:1508]
    Kernel driver in use: b43-pci-bridge
alexey@alexey-Compaq-615:~$ 
```



```
alexey@alexey-Compaq-615:~$ lspci -vnn -d 14e4:
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:1508]
    Physical Slot: 1-1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 92000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```
Can somebody five me support.
Thanks in advance
Best regards Alexey

---

### Post by jeremy31 on 2016-08-11
If you have an ethernet connection or otherwise can access the internet from the machine ```
sudo apt-get install firmware-b43-installer
```

Reboot

---

