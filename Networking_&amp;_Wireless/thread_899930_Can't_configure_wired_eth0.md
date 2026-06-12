---
title: "Can't configure wired eth0"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by bpudlo on 2008-08-24
So got a new computer that I thought I would set up as a home server.  Installed 8.04, got the software raid working, ftp server, remote desktop, and shared the folder to my vista machine.

I try to get ushare to work and I get an error message that eth0 is down.

So I go into the Devices - Network Tools from the admin window and I unlock and try to configure eth0.  As you can see from the attached file eth0 does not exist.

sudo lshw -class network
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:5d:7d:fe
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.0.155 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s
```

sudo lspci
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7911
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```


I searched and found alot of errors with the new kernal and the rtl8111 chip set.  So I go and purchase a 'world link fast 10/100 card', different chipset but still when I try to configure it I get the 'interface does not exist'.

I can see it, I can use it, I can ping out, I can remote in, I can FTP to it, etc.

I can't run ushare or connect to it because it says it is down.


This is probably something silly I'm doing wrong.  Can anyone help?

---

### Post by bsh on 2008-08-25
just don't use network manager, because it is crap. i have always had problems with it.
use manual configuration throught the config files.
- first, make sure the kernel module is loaded, but it obviously is, otherwise you wouldn't be able to use the network card et all. do a 'lsmod' and check if you see a 'r8168' or 'r8111' or similar module in the list.

- assign 'eth0' to the card's MAC address in 'iftab'. in */etc/iftab*, add this line if it's not already existing:
*eth0 mac 00:1f:d0:5d:7d:fe arp 1*

- configure the 'eth0' interface in */etc/network/interfaces*:
should look something like this:

[I]auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.0.155
netmask 255.255.255.0
gateway 192.168.0.1
mtu 1500
txqueuelen 1000[/I]

(note: gateway address might be different for you. use your router's ip address here.)
this configures 'eth0' for a fixed ip address of 192.168.0.155.

- when done, restart networking by typing:
*sudo /etc/init.d/networking restart*, or just reboot. (reboot is recommended, to check if the kernel module gets loaded automatically and the interface is brought up automatically)

- finally, check if it's working:
type *ifconfig*
it should display your existing and configured interfaces, like 'lo', 'eth0', 'wlan' etc etc. if eth0 is there with an ip address etc, then it's working.

---

