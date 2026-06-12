---
title: "Huawei EVDO 616"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Com_2_Reset on 2011-01-10
How can i make my Huawei USB modem (Huawei EVDO 616) works in Ubuntu 10.10. ?

---

### Post by vivek.pandey on 2011-01-10
> **Com_2_Reset said:**
> How can i make my Huawei USB modem (Huawei EVDO 616) works in Ubuntu 10.10. ?

can you tell in brief wat all things have you tried to connect it to net?
the basic step is to make a vpn connection using broadband option.. then edit the settings and enter the password and username ..hope u have done this.. if yes then tell the problems u faced:P

---

### Post by Com_2_Reset on 2011-01-11
When I plug Huawei EVDO 616 wireless modem into the laptop, nothing happened. It looks that not recognized by Ubuntu 10.10.

By running several commands (while usb plug in), I got the following results:
```
usb-devices
```T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
[COLOR=Black]P: [/COLOR][COLOR=Black] Vendor=21f5 ProdID=1000 Rev=00.00
[COLOR=Red]S:  Manufacturer=Qualcomm, Incorporated
S:  Product=StrongRising.CO[/COLOR][/COLOR]
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

[COLOR=Blue]Note: [/COLOR][COLOR=Blue] Manufacturer [/COLOR][COLOR=Blue](Qualcomm)[/COLOR][COLOR=Blue] and [/COLOR][COLOR=Blue]Product of the usb (StrongRising.CO) are shown.
[/COLOR] 
```
lsusb
```[COLOR=Blue]
[/COLOR]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 005 Device 005: ID 21f5:1000  [/COLOR]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 05dc:a701 Lexar Media, Inc. JumpDrive FireFly
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[COLOR=Blue]Note: The third line has no description.

[/COLOR]```
dmesg -c
```[ 2423.091671] sr: Sense Key : Hardware Error [current] 
[ 2423.091677] sr: Add. Sense: No additional sense information
[ 2423.204180] usb 5-1: reset full speed USB device using uhci_hcd and address 4
[ 2423.456165] usb 5-1: reset full speed USB device using uhci_hcd and address 4
[ 2423.708284] usb 5-1: reset full speed USB device using uhci_hcd and address 4
[ 2423.960168] usb 5-1: reset full speed USB device using uhci_hcd and address 4
[ 2619.841514] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[ 2707.584179] usb 5-1: USB disconnect, address 4
[ 2712.312170] usb 5-1: new full speed USB device using uhci_hcd and address 5
[ 2712.470435] scsi9 : usb-storage 5-1:1.0
[COLOR=Red][ 2713.472385] scsi 9:0:0:0: CD-ROM            CDROM    StrongRising.CO  2.31 PQ[/COLOR]

[COLOR=Blue]Note: The last line has CDROM and StrongRising.CO (product ID of the usb)
 What does it means?[/COLOR]

Another thing I found under /dev folder is : when I plug the usb, a file called cdrom appered.
If I unplug the usb, it will disappear.

---

