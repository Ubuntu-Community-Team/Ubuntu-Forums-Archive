---
title: "Bluetooth connection"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by steveredshaw on 2017-07-23
I have just started using UbuntuStudio 17.04 on my Sony Vaio. I cannot get a bluetooth connection. I know my laptop can connect to bluetooth devices as I have successsfully done this under Mint. The process goes up to pairing, but does not connect - I have tried this on several bluetooth devices (all headsets or music speakers). The devices have been added to my bluetooth list, but error reports that Protocol is not available.

Is there something else I need to install or tweak?

I did look at Local Services and saw that no DHCP servers were installed - is that anything to do with the problem?

---

### Post by praseodym on 2017-07-24
Please show these outputs:
```

hciconfig --all
lspci -nnk
lsusb
usb-devices
lsmod
```

---

### Post by steveredshaw on 2017-07-24
Here goes;

```
steve@steve-ubuntu-studio:~$ hciconfig --allhci0:	Type: Primary  Bus: USB
	BD Address: 88:9F:FA:E3:AB:29  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN 
	RX bytes:3857 acl:28 sco:0 events:151 errors:0
	TX bytes:4115 acl:26 sco:0 commands:98 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'steve-ubuntu-studio'
	Class: 0x00010c
	Service Classes: Unspecified
	Device Class: Computer, Laptop
	HCI Version: 2.1 (0x4)  Revision: 0x254
	LMP Version: 2.1 (0x4)  Subversion: 0x4203
	Manufacturer: Broadcom Corporation (15)


steve@steve-ubuntu-studio:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
	Subsystem: Sony Corporation Core Processor DRAM Controller [104d:9071]
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
	Subsystem: Sony Corporation Core Processor Integrated Graphics Controller [104d:9071]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset HECI Controller [104d:9071]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [104d:9071]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset High Definition Audio [104d:9071]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [104d:9071]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation HM55 Chipset LPC Interface Controller [8086:3b09] (rev 05)
	Subsystem: Sony Corporation HM55 Chipset LPC Interface Controller [104d:9071]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [104d:9071]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset SMBus Controller [104d:9071]
	Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
	Subsystem: Sony Corporation 5 Series/3400 Series Chipset Thermal Subsystem [104d:9071]
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
	Subsystem: Sony Corporation MMC/SD Host Controller [104d:9071]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci_pci
03:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [1180:e230]
	Subsystem: Sony Corporation R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [104d:9071]
03:00.4 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822]
	Subsystem: Sony Corporation MMC/SD Host Controller [104d:9071]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci_pci
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
	Subsystem: Sony Corporation Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [104d:9071]
	Kernel driver in use: sky2
	Kernel modules: sky2
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
	Subsystem: Sony Corporation Core Processor QuickPath Architecture Generic Non-core Registers [104d:9071]
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
	Subsystem: Sony Corporation Core Processor QuickPath Architecture System Address Decoder [104d:9071]
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
	Subsystem: Sony Corporation Core Processor QPI Link 0 [104d:9071]
3f:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
	Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [104d:9071]
3f:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
	Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor Reserved [104d:9071]
3f:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
	Subsystem: Sony Corporation 1st Generation Core i3/5/7 Processor Reserved [104d:9071]
steve@steve-ubuntu-studio:~$ lsusb
Bus 002 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 001 Device 003: ID 0c45:6409 Microdia Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
steve@steve-ubuntu-studio:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.10
S:  Manufacturer=Linux 4.10.0-19-lowlatency ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=6409 Rev=9c.30
S:  Manufacturer=USB 2.0 Camera_FLV14
S:  Product=USB 2.0 Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e00f Rev=05.96
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth Device
S:  SerialNumber=889FFAE3AB29
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.10
S:  Manufacturer=Linux 4.10.0-19-lowlatency ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.03
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid



```

---

### Post by steveredshaw on 2017-07-24
:)
[FONT=arial]
Did another search and came up with another reference in Ubuntu forums and this - [https://github.com/blueman-project/blueman/issues/547](https://github.com/blueman-project/blueman/issues/547)

[COLOR=#24292E]The steps are first: remove bluetooth device, second: run [/COLOR][/FONT]```
[FONT=arial]sudo apt install pulseaudio-bluetooth-module[/FONT]
```[FONT=arial][COLOR=#24292E] from a terminal and third: [/COLOR][/FONT]```
[FONT=arial]killall pulseaudio[/FONT]
```[FONT=arial][COLOR=#24292E] or restart your session, then try again. Worked for me.[/COLOR][/FONT]

---

