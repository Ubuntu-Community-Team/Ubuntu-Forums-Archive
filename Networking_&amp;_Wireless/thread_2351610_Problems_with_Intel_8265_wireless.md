---
title: "Problems with Intel 8265 wireless"
date: 2017-02-05
forum: Networking &amp; Wireless
---

### Post by opprobrium on 2017-02-05
I've got a new laptop with an Intel wireless device. I can't get it to recognise the wireless.

I've read lots of discussions on forums, but been unable to resolve the issue. Probably I'm missing omething.

The wireless card should be Intel wireless AC-8265.

I've tried updating Ubutnu (over Ethernet) to see if this resolves it. It didn't and apparently there are no further updates. (I managed to screw this up the first time, borking the computer - apparently the update section of the new Software Centre is a bit dangerous - requiring a reinstall. The problem persisted after this.)

I've looked up the driver on [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi).

I've then downloaded this, extracted it and put it in /lib/firmware. I can see iwlwifi-8265-22.ucode in the folder so despite having not done this before I think this bit at least has worked.

This hasn't fixed the problem. Do I need to do anything further?

Output of lspci:

```


00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.1 PCI bridge: Intel Corporation Device 9d11 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Intel Corporation Device 24fd (rev 78)


```

Output for sudo lshw -c network

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: enp1s0f1
       version: 12
       serial: 80:fa:5b:39:4e:a5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.85 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:125 ioport:e000(size=256) memory:df114000-df114fff memory:df110000-df113fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:df000000-df001fff


```

---

### Post by jeremy31 on 2017-02-05
Moved to Networking

You need a newer kernel for that wireless card
```
sudo apt-get install linux-generic-hwe-16.04-edge
```
Reboot

---

### Post by opprobrium on 2017-02-05
Brilliant. Worked first time.

Thanks.

---

### Post by aasheeshjoshi on 2017-06-30
This worked for me as well! :D I've been struggling with this for the last 3-4 hours now.

I have a Dell Latitude 5480, Ubuntu 16.04 + Intel 8265 Wireless card. I even upgraded to kernel 4.8 but that didn't help. Upgrading as suggested below and rebooting fixed the issue immediately.

Thank you jeremy31.=d>

> **jeremy31 said:**
> Moved to Networking

You need a newer kernel for that wireless card
```
sudo apt-get install linux-generic-hwe-16.04-edge
```
Reboot

---

### Post by jfleroux on 2017-10-26
[COLOR=#000000]This worked for me
[/COLOR] [COLOR=#000000]
[/COLOR][COLOR=#000000]Dell Latitude 7480, Ubuntu 16.04 + Intel 8265 Wireless card.[/COLOR][COLOR=#000000]
[/COLOR]
Thanks

> **jeremy31 said:**
> Moved to Networking

You need a newer kernel for that wireless card
```
sudo apt-get install linux-generic-hwe-16.04-edge
```
Reboot

---

