---
title: "Is this meaning linux driver doesn't support access point mode?"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Blaxter on 2008-05-25
I've just bought motherboard ASUS p5k-e Wifi-ap, which has wifi support. I want to set the wifi interface as an access point, but if i run:
```
# iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```
i don't really know how can i go on, because all the docs i've found always start setting the interface as master mode :(. 

btw when i run *# lshw -C network* the driver doesn't appear, but i think it's **rtl8187** (or at least it's the module loaded).

any help would be appreciate, thanks!

---

### Post by chili555 on 2008-05-25
First of all, the card will not probably change its mode for any ordinary user, but it will for super user, so please precede that command with **sudo.** Second, not every card supports every mode, so it may not work, even with sudo.> lshw -C network the driver doesn't appear, but i think it's rtl8187 (or at least it's the module loaded)May we please see your:```
sudo lshw -C network
```Thanks.

---

### Post by Blaxter on 2008-05-25
i've done the *iwconfig* command as root. The output of *lshw* is:
```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:8c:b5:d4:78
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=83.138.248.176 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:63:e6:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.1 multicast=yes wireless=IEEE 802.11g

```

Though i've been searching and now i'm sure that the chipset of the "ASUS wifi Solo" (as asus called the integrated wifi in theirs pk5-* motherboards) it's rtl8187.

---

### Post by chili555 on 2008-05-25
Since it's up and has an IP address, some driver is loaded, although *lshw* is mum about it. You could do:```
lsmod | grep 818
```See if any candidates appear. If rtl8187 shows up, that's surely what you have.

By the way, there are two threads here, one of which I participated in, concerning rtl8187, one involving the jadams version and the other, the aircrack-ng version. I have examined both READMEs and they both state they support ad-hoc and managed mode; no mention of master.

---

### Post by Blaxter on 2008-05-26
yeah, with lsmod i can see rtl8187 module.

I guess that my only way for getting master mode, could be trying with ndiswrapper, isn't it? i hate asus! :(

---

