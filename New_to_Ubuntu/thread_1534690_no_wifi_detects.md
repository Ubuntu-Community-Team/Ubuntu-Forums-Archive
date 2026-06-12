---
title: "no wifi detects"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by flavs2001 on 2010-07-19
Hi am new on Ubuntu (wubi) installed on windows 7, runs almost right because no detect wifi and I don`t know how fix it.
I have a Samsung laptop.
I need help

thanks

Flavio

---

### Post by anewguy on 2010-07-19
Obviously we'll need additional information to try to help, so please do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

lsusb <press enter>

lspci <press enter>

lshw -C network <press enter>

Post the output from all of the above back here and we'll go from there.

Dave ;)

---

### Post by Rubi1200 on 2010-07-19
As pointed out above.

Also post the output from

```
ifconfig 
```

and 

```
iwconfig
```

---

### Post by kidknapp on 2010-07-23
If nothing else find out if you need to wrap your Windows 7 driver or if there is a native driver recognizing your wifi. Go to System>Administration>Hardware Drivers....See what options(if any) it gives you...

---

### Post by 3rdalbum on 2010-07-23
> **kidknapp said:**
> If nothing else find out if you need to wrap your Windows 7 driver or if there is a native driver recognizing your wifi. Go to System>Administration>Hardware Drivers....See what options(if any) it gives you...

Connect your computer to your router via an Ethernet cable FIRST. Then go to System > Administration > Software Sources and check that the first four boxes are ticked so Ubuntu knows where to find packages.

Close the window, open System > Administration > Synaptic Package Manager. Click Reload. After that's done, go to Hardware Drivers and see what it says.

If there's still no driver offered to you, then find out the model number of the wifi chipset by typing:

```
lsusb
```

into the terminal. (that's a lowercase L, not a number 1). The terminal is at Applications > Accessories > Terminal.

Then have a look on Google for what you need to do; for instance, if your chipset is "RT3008", then search google for "RT3008 Ubuntu 10.04" or "RT3008 Ubuntu Lucid".

---

### Post by RasmusUb on 2010-07-23
> **3rdalbum said:**
> Connect your computer to your router via an Ethernet cable FIRST. Then go to System > Administration > Software Sources and check that the first four boxes are ticked so Ubuntu knows where to find packages.

Close the window, open System > Administration > Synaptic Package Manager. Click Reload. After that's done, go to Hardware Drivers and see what it says.

If there's still no driver offered to you, then find out the model number of the wifi chipset by typing:

```
lsusb
```into the terminal. (that's a lowercase L, not a number 1). The terminal is at Applications > Accessories > Terminal.

Then have a look on Google for what you need to do; for instance, if your chipset is "RT3008", then search google for "RT3008 Ubuntu 10.04" or "RT3008 Ubuntu Lucid".

I am facing similar issues on my Asus eee pc.
I have updated the sources but can find no "hardware" on the list at all. I can find" network" and it has a bunch of stuff which means preciously nothing to me, and when I type lsusb I get... a list of five busses and seven ports. There i no such thing as a chipset number unless "1d6b" is significant somehow.

---

### Post by korbennn on 2010-08-01
I  think it's pointless to start another thread like this...

On Vaio, with x64 architecture - through Wubi installed Ubuntu x64

should I key in all the settigns from windows? e.g. IPv4? [ my wlan is secured]

edit//

tried my best here and got these results
lsusb
lspci
lshw -C
ifconfig
iwconfig
please find attached to my post.

I aslo tried to insert the IP, Subnet, Default Getaway and...voila! the wifi diode flickers, then goes stable, and I get the message: Connection Establshed but nothing in Firefox :(

since no one wants to d/l the results:

> ra@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b14e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ra@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0c:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0c:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0c:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
ra@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: Marvell Technology Group Ltd.
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 10
serial: 00:24:be:79:5d:27
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
resources: irq:29 memory:d3520000-d3523fff ioport:c000(size=256) memory:d3500000-d351ffff(prefetchable)
*-network
description: Wireless interface
product: Wireless WiFi Link 5100
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: 00:24:d6:10:18:7e
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:31 memory:d2100000-d2101fff
ra@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:24:be:79:5d:27 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:152 errors:0 dropped:0 overruns:0 frame:0
TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:11680 (11.6 KB) TX bytes:11680 (11.6 KB)

wlan0 Link encap:Ethernet HWaddr 00:24:d6:10:18:7e 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

ra@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11abgn ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

ra@ubuntu:~$

and some more info:


> ra@ubuntu:~$ sudo iwlist scan
[sudo] password for ra: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

ra@ubuntu:~$ dmesg | grep iwl
[   10.031070] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.031073] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.031167] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.031202] iwlagn 0000:03:00.0: setting latency timer to 64
[   10.031247] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   10.098687] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.098773] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   10.146887] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.664936] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   12.667686] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   12.816423] Registered led device: iwl-phy0::radio
[   12.816439] Registered led device: iwl-phy0::assoc
[   12.816457] Registered led device: iwl-phy0::RX
[   12.816471] Registered led device: iwl-phy0::TX
ra@ubuntu:~$ 

---

