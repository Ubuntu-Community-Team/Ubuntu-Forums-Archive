---
title: "cannot connect to the internet"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by rre12 on 2010-09-26
I just installed Kubuntu 64-bits latest version and am having trouble connecting to the internet via ethernet cable.

I read the sticky and it said to present these information when asked for troubleshooting

lspci output

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:01.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:05.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:07.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
07:09.0 PCI bridge: PLX Technology, Inc. Device 8608 (rev ba)
08:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
09:00.0 SATA controller: Device 1b4b:9123 (rev 10)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```lsusb output

```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 004: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 002 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ifconfig output

```
eth0      Link encap:Ethernet  HWaddr 48:5b:39:36:1b:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23648 (23.6 KB)  TX bytes:23648 (23.6 KB)


```I tried the other programs, but their output never made it onto the text file.

My computer specs are:
i7 875k
ATI Radeon 5850
ASUS P7P55D-E PRO

I have read the documentation at [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

and followed the PPPoE modem section, but after running 
```
sudo pppoeconf
```it tried to detect access point concentration, but failed. It did detect my ethernet card though. 

My ISP is ATT DSL. My router is D-Link DIR-825. I am using wired connection however. Please let me know if I need to include more information. Thanks

---

### Post by formaldehyde_spoon on 2010-09-27
That's a lot of information, but what is the actual problem? ''having trouble'' isn't very informative....

---

### Post by andrewthomas on 2010-09-27
> **rre12 said:**
> 

I have read the documentation at [**https://help.ubuntu.com/7.04/**internet/C/connect-to-internet.html]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")

and followed the PPPoE modem section, but after running 
```
sudo pppoeconf
```it tried to detect access point concentration, but failed. It did detect my ethernet card though. 

My ISP is ATT DSL. My router is D-Link DIR-825. I am using wired connection however. Please let me know if I need to include more information. Thanks
You are not using 7.04 so that documentation is not going to apply to your version of ubuntu.

---

### Post by cap10Ibraim on 2010-09-27
are you connected to a modem ? DSL ? what type of cnx ?

---

### Post by andrewthomas on 2010-09-27
> **cap10Ibraim said:**
> are you connected to a modem ? DSL ? what type of cnx ?
> **rre12 said:**
> I just installed Kubuntu 64-bits latest version and am having trouble connecting to the [B]internet via ethernet cable.

My ISP is ATT DSL. My router is D-Link DIR-825[/B]. I am using wired connection however. Please let me know if I need to include more information. Thanks
from OP

---

### Post by cap10Ibraim on 2010-09-27
can you access your modem(or Router)  by typing it's ip adress in a web browser ?

---

### Post by rre12 on 2010-09-27
I just fixed it by shutting my computer down completely instead of always putting it in Hybrid Sleep. Thanks for the help though guys

---

