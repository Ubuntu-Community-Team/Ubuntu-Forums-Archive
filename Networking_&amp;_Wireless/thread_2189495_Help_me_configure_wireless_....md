---
title: "Help me configure wireless ..."
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by caro8pare on 2013-11-22
Can you help me step by step how to configure Wireless , using WPA2?

Here is my info, what do I have to do Next? It make about 3 hours that I'm searching what to do Next....  ;o(
I think my driver is well installed but I don't see any device ath0, ....

karo@KARO:/$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       **logical name: eth0**
       version: 03
       serial: 00:24:e8:d1:ff:dd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 driverversion=2.3LK-NAPI** duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=216.113.111.69 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
      ** product: BCM4322 802.11a/b/g/n Wireless LAN Controller**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0
       resources: irq:18 memory:fa000000-fa003fff

karo@KARO:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

karo@KARO:/$ lsmod
**Module **                 Size  Used by
**b43  **                 347284  0 
mac80211              461161  1 b43
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
ssb                    50087  1 b43
...

karo@KARO:/$ sudo lspci -nn | grep 0280
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

karo@KARO:/$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
...

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

---

### Post by praseodym on 2013-11-22
Install the package **linux-firmware-nonfree** via cable connection:
```

sudo apt-get install linux-firmware-nonfree
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by caro8pare on 2013-11-22
karo@KARO:~$ sudo apt-get install linux-firmware-nonfree

---

### Post by caro8pare on 2013-11-22
Ok, I have installed the package linux-firmware-nonfree and the command you post, then reboot.
And it doesn't works. Someone have an idea??? Regards,

---

### Post by praseodym on 2013-11-23
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
ifconfig -a
rfkill list
cat /etc/resolv.conf
dmesg | grep b43
```

---

