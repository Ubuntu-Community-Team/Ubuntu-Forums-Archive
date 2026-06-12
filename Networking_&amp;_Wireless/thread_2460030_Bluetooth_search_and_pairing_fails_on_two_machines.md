---
title: "Bluetooth search and pairing fails on two machines new installs of 20.04"
date: 2021-03-31
forum: Networking &amp; Wireless
---

### Post by Tim_Johnson on 2021-03-31
Overview:
Search for device fails on two machines both with fresh installs of 20.04. One of the machines is a 2011 mac mini which previously
had 16.04 and on that version bluetooth worked flawlessly. The other machine is a new HUNSN i5.
The device - a wireless keyboard that pairs successfully with tablets and smartphones, and did pair successfully and work well on the
previous version of 16.04 on the mac mini.

Diagnostics - bear in mind that I am six years retired from web development on linux platforms and as they say - if you don't use it
a lot, you lose it a lot. :(

Code follows
status
```
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2021-03-25 16:20:27 AKDT; 5 days ago
       Docs: man:bluetoothd(8)
   Main PID: 767 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9338)
     Memory: 2.1M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;767 /usr/lib/bluetooth/bluetoothd

Mar 30 16:37:08 mini bluetoothd[767]: Endpoint registered: sender=:1.918 pa…/sbc
Mar 30 16:37:08 mini bluetoothd[767]: Endpoint registered: sender=:1.918 pa…/sbc
Mar 30 16:44:19 mini bluetoothd[767]: Endpoint unregistered: sender=:1.918 …/sbc
Mar 30 16:44:19 mini bluetoothd[767]: Endpoint unregistered: sender=:1.918 …/sbc
Mar 30 16:44:19 mini bluetoothd[767]: Endpoint registered: sender=:1.965 pa…/sbc
Mar 30 16:44:19 mini bluetoothd[767]: Endpoint registered: sender=:1.965 pa…/sbc
Mar 30 16:44:30 mini bluetoothd[767]: Endpoint unregistered: sender=:1.965 …/sbc
Mar 30 16:44:30 mini bluetoothd[767]: Endpoint unregistered: sender=:1.965 …/sbc
Mar 30 16:44:51 mini bluetoothd[767]: Endpoint registered: sender=:1.1004 p…/sbc
Mar 30 16:44:51 mini bluetoothd[767]: Endpoint registered: sender=:1.1004 p…/sbc
Hint: Some lines were ellipsized, use -l to show in full.
```
dmesg
```
dmesg | grep -i bluetooth
[    3.595368] Bluetooth: Core ver 2.22
[    3.595400] Bluetooth: HCI device and connection manager initialized
[    3.595405] Bluetooth: HCI socket layer initialized
[    3.595408] Bluetooth: L2CAP socket layer initialized
[    3.595413] Bluetooth: SCO socket layer initialized
[    3.661703] Bluetooth: hci0: read Intel version: 370810011003110e32
[    3.661706] Bluetooth: hci0: Intel device is already patched. patch num: 32
[    5.154398] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.154401] Bluetooth: BNEP filters: protocol multicast
[    5.154406] Bluetooth: BNEP socket layer initialized
[   18.797688] Bluetooth: RFCOMM TTY layer initialized
[   18.797699] Bluetooth: RFCOMM socket layer initialized
[   18.797706] Bluetooth: RFCOMM ver 1.11
[429794.858320] Bluetooth: hci0: Ignoring error of Inquiry Cancel command
[432924.543959] Bluetooth: hci0: HCI reset during shutdown failed

```
hcitool
```
hcitool dev
Devices:
    hci0    4C:34:88:B5:54:22
```
lsmod
```
lsmod | grep -i bluetooth
bluetooth             581632  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth

```
rfkill
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```
In addition, crashes are associated with both the use of the Control Center feature and the applet.
Attempts to pair have made on both MATE and GNOME.
Hopefully some of this code will edify wiser heads than I, 
and I can get my bluetooth back.
Thanks
Tim

---

### Post by praseodym on 2021-04-02
What hardware is it?!
```

lspci -nnk
lsusb
usb-devices
hciconfig --all 
```

---

### Post by Tim_Johnson on 2021-04-04
Thanks for the reply.
Apologies to paseodym for taking so long to reply. I must have neglected my settings for notifications. 
Code follows:
tim@mini:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
	Subsystem: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04]
	Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0a1e] (rev 0b)
	DeviceName:  Onboard IGD
	Subsystem: Intel Corporation Device [8086:0a1e]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
	Subsystem: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
	Subsystem: Intel Corporation 8 Series USB xHCI HC [8086:9c31]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
	Subsystem: Intel Corporation 8 Series HD Audio Controller [8086:9c20]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 4 [8086:9c16] (rev e4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series USB EHCI #1 [8086:9c26] (rev 04)
	Subsystem: Intel Corporation 8 Series USB EHCI [8086:9c26]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
	Subsystem: Intel Corporation 8 Series LPC Controller [8086:9c43]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
	Subsystem: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
	Subsystem: Intel Corporation 8 Series SMBus Controller [8086:9c22]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
	Subsystem: Intel Corporation Wireless 3165 [8086:8010]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
tim@mini:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 8087:0a2a Intel Corp. 
Bus 002 Device 005: ID 03f0:8811 HP, Inc Deskjet 1000 J110 series
Bus 002 Device 004: ID 0480:a00c Toshiba America Inc External USB 3.0
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 040b:0a67 Weltrend Semiconductor Weltrend USB Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tim@mini:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.08
S:  Manufacturer=Linux 5.8.0-48-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.04
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 9
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.08
S:  Manufacturer=Linux 5.8.0-48-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=040b ProdID=0a67 Rev=00.01
S:  Product=Weltrend USB Mouse
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#=0x1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00

---

