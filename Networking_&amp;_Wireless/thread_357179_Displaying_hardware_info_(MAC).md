---
title: "Displaying hardware info (MAC)"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-09
What is the command to display hardware information for the wireless cards?
Lets say i want to see the MAC of the current wifi card into the slot. Besides looking what's printed on the back of the card though ....

And why do i have this nonexistent broadcom BCM4306 wireless card with its own mac address and everything listed in the device manager? how can i remove it?

Thanks

---

### Post by spd106 on 2007-02-09
You can use this command to find information about network interfaces
```
sudo lshw -C network
```
The MAC address is also shown by ```
ifconfig
```

Device Manager will only display information that it has found from the hardware in your system, it is unlikely to display wrong data. Far more likely is that you have a wireless card that has a Broadcom chipset. Look under the pci.subsys_vendor key for the manufacturer of the card. Incidentally the MAC address can also be seen under the info.udi key of the interface. Look where it says /org/freedesktop/Hal/devices/net_xx_xx_xx_xx_xx_xx

---

