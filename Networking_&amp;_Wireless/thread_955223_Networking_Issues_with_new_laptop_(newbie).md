---
title: "Networking Issues with new laptop (newbie)"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by Safire10 on 2008-10-22
I just purchased a new laptop, hp dv71130us. I install ubuntu and it is not allowing me to connect wireless or wired. When I type lspci it is telling me I have the RTL8101E ethernet adapter and the atheros wireless adapter. I need help getting connected

---

### Post by melojo on 2008-10-22
Can you post the output of 
lspci and sudo lshw -C network

---

### Post by Iowan on 2008-10-22
There are a few other threads about those devices:
[http://ubuntuforums.org/showthread.php?t=901064]("http://ubuntuforums.org/showthread.php?t=901064")
[http://ubuntuforums.org/showthread.php?t=792092]("http://ubuntuforums.org/showthread.php?t=792092")
[http://ubuntuforums.org/showthread.php?t=921589]("http://ubuntuforums.org/showthread.php?t=921589")

I missed more than a few...

---

### Post by prematurebaby on 2008-10-22
Was there a driver installed for said device. If not find one.

---

### Post by Safire10 on 2008-10-23
This is what comes up when I enter lspci
maggie@maggie-laptop:~$ lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge

00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]

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

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382

08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381

08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383

08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

09:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

