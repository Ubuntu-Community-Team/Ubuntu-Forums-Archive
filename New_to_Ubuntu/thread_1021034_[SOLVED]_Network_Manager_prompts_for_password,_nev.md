---
title: "[SOLVED] Network Manager prompts for password, never connects"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by robvvrob on 2008-12-24
Help!  I am running Ubuntu 8.10 on a Dell Inspiron 1520.  After fully updating Ubuntu and enabling the proprietary Broadcom STA wireless driver, my laptop appears to be capable of detecting local networks. When I configure the network connection, Network Manager keeps changing my specified password to a long string of numbers and letters.  When trying to connect to my wireless access point (D-link g router - wpa personal - tkip encryption - not broadcasting), the Network Manager attempts to connect, but then asks for the password. The Network Manager repeats this indefinitely, and never successfully connects. Its probably something really stupid, but anyways thanks ahead of time for your help :)

OUTPUT FOR: lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

OUTPUT FOR: lsusb

Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04f3:0212 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 007: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

OUTPUT FOR: sudo lshw -class network
[sudo] password for rob: 
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:1d:d9:6b:27:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a9:9b:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.103 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:6b:3c:1c:00:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by sportscrazed2 on 2008-12-24
i don't know how to help you but if network manager isn't working you might want to try wicd it works much better for me and connects much quicker after waking from suspend

---

### Post by robvvrob on 2008-12-24
ok thanks for the advice.  I just switched to wicd.  now it's hanging at authentication validation, andthenn fails to connect. hm   Merry Christmas, ps :D

---

### Post by abn91c on 2008-12-24
if you network manager has a "allow roaming" option uncheck the box then try to connect

---

### Post by robvvrob on 2008-12-24
Hi thanks for the reply! Ok I will try that.  Is there an option like this that causes trouble in wicd, or just Network Manager? I read somewhere that this could help, but couldn't find where to disable roaming... where can I find the "allow roaming" option?

---

### Post by abn91c on 2008-12-25
> **robvvrob said:**
> Hi thanks for the reply! Ok I will try that.  Is there an option like this that causes trouble in wicd, or just Network Manager? I read somewhere that this could help, but couldn't find where to disable roaming... where can I find the "allow roaming" option?
i do not use wicd, im on kubuntu right now and cant remember if ubuntu's network tools has that

---

### Post by Dedoimedo on 2008-12-25
To see whether the problem is with router or your pc, try:

- using the router with no encryption, see if you can connect.
- using the router with wep
- using the router with wpa / aes ...

Try to isolate the problem.

Cheers,
Dedoimedo

---

### Post by robvvrob on 2008-12-26
Ok so I've confirmed that the router does work, it's definitely my computer that is causing the problem.  If anyone owns a dell inspiron 152x connecting to a wireless network, it'd be much appreciated if you could link to some kind guide that you can confirm works.

thanks

---

### Post by Dedoimedo on 2008-12-26
So which of the three options mentioned worked, if any?
Dedoimedo

---

### Post by nhasian on 2008-12-26
its the propriety Broadcom driver in ubuntu.  it doesnt work with WPA/WPA2 networks.  he can still connect to an unsecured network or a WEP network.  WPA/WPA2 support should arrive in a future driver update.

---

### Post by robvvrob on 2008-12-26
Ok thank you very much for the information.  Do you have any idea when such an update might come around?

---

