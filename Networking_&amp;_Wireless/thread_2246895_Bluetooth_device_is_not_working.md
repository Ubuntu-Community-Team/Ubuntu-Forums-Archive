---
title: "Bluetooth device is not working"
date: 2014-10-04
forum: Networking &amp; Wireless
---

### Post by Niladri_Banerjee on 2014-10-04
[COLOR=#000000][FONT=Verdana]Linux Distribution = Ubuntu 14.04 LTS Trusty Tahr, 64 bit

Hi All,

The Bluetooth device is not working. It worked however in Windows 7 Professional version 64 bit.

The error message is "No Adapters found for Bluetooth".

Can anyone help on this.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
dmesg output

niladri@niladri:~$ dmesg | grep -i blue
[ 23.753724] Bluetooth: Core ver 2.17
[ 23.753752] Bluetooth: HCI device and connection manager initialized
[ 23.753765] Bluetooth: HCI socket layer initialized
[ 23.753769] Bluetooth: L2CAP socket layer initialized
[ 23.753777] Bluetooth: SCO socket layer initialized
[ 23.758336] Bluetooth: RFCOMM TTY layer initialized
[ 23.758352] Bluetooth: RFCOMM socket layer initialized
[ 23.758358] Bluetooth: RFCOMM ver 1.11
[ 24.253529] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 24.253535] Bluetooth: BNEP filters: protocol multicast
[ 24.253549] Bluetooth: BNEP socket layer initialized


lspci output

niladri@niladri:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
[/FONT][/COLOR]

---

### Post by praseodym on 2014-10-04
Please show the output of "lsusb", too

---

### Post by Niladri_Banerjee on 2014-10-04
**lsusb output**

niladri@niladri:~$ lsusb
Bus 002 Device 003: ID 0461:4dfa Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2014-10-04
Weird. Please show more details:

```
lspci -nnk | grep -iA2 net
hciconfig --all
usb-devices
```

---

### Post by Niladri_Banerjee on 2014-10-04
**niladri@niladri-NV79:~$ lspci -nnk | grep -iA2 net**
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0139]
	Kernel driver in use: tg3
02:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6632]
	Kernel driver in use: ath9k


**niladri@niladri-NV79:~$ hciconfig --all**
niladri@niladri-NV79:~$


**niladri@niladri-NV79:~$ usb-devices**


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-36-generic ehci_hcd
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
P:  Vendor=064e ProdID=a103 Rev=05.00
S:  Manufacturer=SuYin
S:  Product=Video WebCam
S:  SerialNumber=CN0314-SN30-OV035-VA-R05.00.00
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-36-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=32 #Cfgs=  1
P:  Vendor=0461 ProdID=4dfa Rev=01.01
S:  Product=Wireless Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
niladri@niladri-NV79:~$

---

### Post by praseodym on 2014-10-04
Obviously, the device is not recognized. Check the BIOS settings if it can be activated there

---

### Post by Niladri_Banerjee on 2014-10-08
The BIOS Settings does not have Bluetooth settings. The dmesg output shows Bluetooth device

[COLOR=#000000][FONT=Verdana]niladri@niladri:~$ dmesg | grep -i blue[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753724] Bluetooth: Core ver 2.17[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753752] Bluetooth: HCI device and connection manager initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753765] Bluetooth: HCI socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753769] Bluetooth: L2CAP socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753777] Bluetooth: SCO socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758336] Bluetooth: RFCOMM TTY layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758352] Bluetooth: RFCOMM socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758358] Bluetooth: RFCOMM ver 1.11[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253529] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253535] Bluetooth: BNEP filters: protocol multicast[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253549] Bluetooth: BNEP socket layer initialized[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-08
> **Niladri_Banerjee said:**
> The BIOS Settings does not have Bluetooth settings. The dmesg output shows Bluetooth device

[COLOR=#000000][FONT=Verdana]niladri@niladri:~$ dmesg | grep -i blue[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753724] Bluetooth: Core ver 2.17[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753752] Bluetooth: HCI device and connection manager initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753765] Bluetooth: HCI socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753769] Bluetooth: L2CAP socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.753777] Bluetooth: SCO socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758336] Bluetooth: RFCOMM TTY layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758352] Bluetooth: RFCOMM socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 23.758358] Bluetooth: RFCOMM ver 1.11[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253529] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253535] Bluetooth: BNEP filters: protocol multicast[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][ 24.253549] Bluetooth: BNEP socket layer initialized[/FONT][/COLOR]

Unfortunately that does not show a bluetooth device present, I see the same results on a laptop that does not have any bluetooth device in Ubuntu or Windows.

With the wifi chipset you have I would have expected to see a device in lsusb with a manufacturer code of 0cf3, so maybe check for ```
dmesg | grep 0cf3
``` might show something

---

### Post by Niladri_Banerjee on 2014-10-09
[COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep 0cf3 did not show any output. I tried that. But how the Bluetooth works in Windows 7 Service Pack 1. Is it ubuntu driver issue?[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-09
> **Niladri_Banerjee said:**
> [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep 0cf3 did not show any output. I tried that. But how the Bluetooth works in Windows 7 Service Pack 1. Is it ubuntu driver issue?[/FONT][/COLOR]

If you are dual booting with Win 7, boot it up and go to device manager/bluetooth radios, select the adapter and bring up the properties page.  Then select the Details tab, use the dropdown menu under property to select Hardware Ids.  It should be USB\VID_****&PID_****, we just need to find out what the **** are so they can be searched for in dmesg

---

### Post by Niladri_Banerjee on 2014-10-09
No I do not have dual boot. I only have Ubuntu 14.04 LTS. I had Windows earlier and it worked there.. The Bluetooth is there in my machine..

---

### Post by jeremy31 on 2014-10-09
I wonder if editing boot parameters might make bluetooth show up ```
sudo gedit /etc/default/grub
``` Find the line that looks like this ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and change it to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux"
``` save and exit the program then ```
sudo update-grub
``` and reboot

I saw something similar a month or so ago when I was experimenting with my Atheros AR9485 card that has bluetooth, when I use it with the Lenovo it was originally installed in and due to a whitelist it is the only card that works in my main laptop.  When installed in my Toshiba the bluetooth didn't appear in lsusb but I found evidence of it in the syslog but the USB info didn't look correct and unfortunately I haven't had the time to investigate/experiment more

---

### Post by Niladri_Banerjee on 2014-10-10
I do not have dual OS machine. Running only Ubuntu 14.04 LTS.

---

