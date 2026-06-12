---
title: "Cannot connect to Internet after upgrade"
date: 2019-04-27
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2019-04-27
Lubuntu 14.04.6 LTS.

I ran an upgrade (sudo apt-get dist-upgrade), after which I cannot connect to the Internet either by ethernet or wifi. If I click the network icon in my panel (bottom right), it says (but greyed out) "Ethernet Network disconnected". The cable is attached and works if plugged into another computer. If I right click, "Enable Networking" is ticked, "Connection Information" is greyed out. I open "Edit Connections" and see that my network connections are listed and configured correctly. It is not a hardware problem, as if I boot into Windows on the same machine, both Ethernet and wifi work.

I would appreciate help with troubleshooting this issue.

Many thanks.

---

### Post by rdh61 on 2019-04-27
Correction. I CAN connect via Ethernet after a reboot, but WIFI is not working.

---

### Post by rdh61 on 2019-04-29
Bump. I have now upgraded to Lubuntu 16.04 LTS. Still no Wifi. Please help!

---

### Post by rdh61 on 2019-04-29
Additional information: The system apparently can find my wireless card, but still there is no wifi connection...

```
robert@robert-Lenovo-B590:~$ sudo lspci
[sudo] password for robert: 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
robert@robert-Lenovo-B590:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0500000-f0507fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 07
       serial: 3c:97:0e:d1:73:64
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.55 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
```

---

### Post by jeremy31 on 2019-04-29
I would check ```
mokutil --sb-state
```
If that says Secure Boot is enabled reboot and go into BIOS settings and disable Secure Boot, then
```
sudo apt update && sudo apt install broadcom-sta-dkms
```
Reboot

It does appear that Lubuntu LTS are only supported for 3 years, so Lubuntu 16.04 is likely going to be EOL soon

---

### Post by rdh61 on 2019-04-29
Secure boot was already disabled. Installing [COLOR=#000000][FONT=&quot]broadcom-sta-dkms and rebooting solved the problem. Thank you.[/FONT][/COLOR]

---

