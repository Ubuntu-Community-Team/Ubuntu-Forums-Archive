---
title: "Wireless not showing after installing Additional Drivers deb"
date: 2021-09-14
forum: Networking &amp; Wireless
---

### Post by errorous on 2021-09-14
Not sure if installing Additional Drivers deb is actually the issue, but this is the only thing I could think of that I have changed since the last restart. This said, now, I do don't even see network in notification area, but can open it via settings. This is what I get in console:

```
milos@lenovo:~$ sudo lshw -C network  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 98:fa:9b:34:15:d7
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-34-generic firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:3000(size=256) memory:b4204000-b4204fff memory:b4200000-b4203fff
  *-network
       description: Network controller
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:135 memory:b4000000-b41fffff
  *-network:0
       description: Ethernet interface
       physical id: 3
       logical name: veth5a51ebf
       serial: e6:cb:96:b9:5e:9e
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 4
       bus info: usb@1:3
       logical name: usb0
       serial: 86:89:4b:ea:5e:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=5.11.0-34-generic firmware=RNDIS device ip=192.168.42.201 link=yes multicast=yes



```

So, the only problem that I have right now is that WiFi is not working.


UPDATE: However, a slightly different output without sudo:

```
milos@lenovo:~$ sudo lshw -class network  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 98:fa:9b:34:15:d7
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-34-generic firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:3000(size=256) memory:b4204000-b4204fff memory:b4200000-b4203fff
  *-network
       description: Network controller
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:135 memory:b4000000-b41fffff
  *-network:0
       description: Ethernet interface
       physical id: 3
       logical name: veth5a51ebf
       serial: e6:cb:96:b9:5e:9e
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 4
       bus info: usb@1:3
       logical name: usb0
       serial: 86:89:4b:ea:5e:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=5.11.0-34-generic firmware=RNDIS device ip=192.168.42.201 link=yes multicast=yes



```

---

### Post by chili555 on 2021-09-14
Please run and post:

```
sudo dmesg | grep -i ath
```

---

### Post by errorous on 2021-09-14
Empty, no output.

---

### Post by chili555 on 2021-09-14
Let's try another approach:

```
sudo modprobe ath10k_pci
sudo dmeg | grep ath
```

---

### Post by errorous on 2021-09-14
```

milos@lenovo:~$ sudo modprobe ath10k_pci
milos@lenovo:~$ sudo dmesg | grep ath
milos@lenovo:~$

```

---

### Post by chili555 on 2021-09-15
Let's see what is going on, or wrong, on the PCI bus:

```
sudo dmesg | grep 03:00
```

---

