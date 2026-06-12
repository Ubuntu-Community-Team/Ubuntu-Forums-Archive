---
title: "wlan0 is missing"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by snail8 on 2016-06-04
[COLOR=#111111][FONT=Ubuntu]I've tried all the solutions I've found on the internet but none of them have worked.

[/FONT][/COLOR]asus f556ua
ubuntu 16.04 LTS

**iwconfig**
[HTML]enp2s0    no wireless extensions.
lo        no wireless extensions.[/HTML]

[COLOR=#111111][FONT=Ubuntu]**lshw -c network**
[/FONT][/COLOR]  [HTML]*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: d0:17:c2:14:a2:b6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.0.110 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:127 ioport:d000(size=256) memory:dfc04000-dfc04fff memory:dfc00000-dfc03fff
  *-network
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:130 memory:df000000-df1fffff[/HTML]

**lspci -nn**
[HTML]02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)[/HTML]

any help?

---

### Post by jeremy31 on 2016-06-04
Please results for ```
dmesg | grep ath10k
```

---

### Post by snail8 on 2016-06-04
**dmesg | grep ath10k**

[    2.108493] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.354577] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    2.354588] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[    2.354590] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[    2.354595] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[    2.354597] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[    2.354601] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[    2.354602] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[    2.354607] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[    2.354609] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[    2.354617] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[    2.354619] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    2.354620] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    2.354622] ath10k_pci 0000:03:00.0: could not probe fw (-2)

---

### Post by jeremy31 on 2016-06-04
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

Reboot and it should function

---

### Post by snail8 on 2016-06-04
> **jeremy31 said:**
> ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

Reboot and it should function

resolved,thanks!

---

