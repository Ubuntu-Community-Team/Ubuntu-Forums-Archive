---
title: "Bluetooth not finding devices, 14.04 LTS"
date: 2015-02-28
forum: Networking &amp; Wireless
---

### Post by Oyb on 2015-02-28
Hi, 

Just bought a Gigabyte Brix GB-BXBT-1900, to use as a htpc. I've got a logitech diNovo Edge Keyboard with bluetooth that I'd like to pair, as the BT dongle that comes with it is a bit shaky. 
Can't seem to get ubuntu to find the keyboard, or my mobile phone(or be visible). 

Tried searching around, but no solutions worked yet, tried all recommendations from [http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts]("http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts") , but no luck. 

I'd post more info if i knew the commands, but sadly i do not. 

Any help? Thanks.

---

### Post by jeremy31 on 2015-02-28
If it is a broadcom or atheros, I might be able to help.  I would like you to open a terminal window and post the results from the following commands
```
 lspci -nnk | grep -iA2 net
``````
lsusb
``````
sudo cat /sys/kernel/debug/usb/devices
```

---

### Post by Oyb on 2015-02-28
Okay, seems it's realtek: 

```
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: AzureWave Device [1a3b:2159]
	Kernel driver in use: rtl8723be
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

```

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 003: ID 13d3:3410 IMC Networks 
Bus 001 Device 005: ID 046d:c714 Logitech, Inc. diNovo Edge Keyboard
Bus 001 Device 004: ID 046d:c713 Logitech, Inc. 
Bus 001 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 1
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev= 3.13
S:  Manufacturer=Linux 3.13.0-32-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.13
S:  Manufacturer=Linux 3.13.0-32-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12   MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=0b04 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c713 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
S:  SerialNumber=001F2011FFDE
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  5 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c714 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
S:  SerialNumber=001F2011FFDE
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=2ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12   MxCh= 0
D:  Ver= 2.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3410 Rev= 2.00
S:  Manufacturer=Realtek 
S:  Product=Bluetooth Radio 
S:  SerialNumber=00e04c000001
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=03 Dev#=  6 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1058 ProdID=1021 Rev=20.02
S:  Manufacturer=Western Digital
S:  Product=Ext HDD 1021
S:  SerialNumber=574341545231333738333534
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
```

---

### Post by jeremy31 on 2015-03-01
[https://github.com/lwfinger/rtl8723au_bt/tree/troy](https://github.com/lwfinger/rtl8723au_bt/tree/troy) might work

---

### Post by Oyb on 2015-03-02
Tried following the readme, but ran into a problem. 

I downloaded the zip and unzipped the package. Navigated terminal to the folder, and ran the commands. 
Encountered a problem here: 

(2)	Remove and blacklist btusb module using
	sudo modprobe -rv btusb
	su -c "echo \"blacklist btusb\" > /etc/modprobe.d/50-btusb.conf"

I get su: Authentication failure.

And now I can't turn on the bluetooth without getting a crash message.

EDIT: Tried uninstalling as listed in readme, but now bluetooth won't turn on. Have I blacklisted something?

---

### Post by jeremy31 on 2015-03-02
Lets see if btusb was indeed blacklisted
```
cat /etc/modprobe.d/50-btusb.conf
```

---

### Post by Oyb on 2015-03-02
No such file or directory. 

Guessing it's not blacklisted then.

---

### Post by jeremy31 on 2015-03-02
Did you reboot after uninstalling?

---

### Post by Oyb on 2015-03-02
Well, turned on bluetooth after uninstalling, when I saw the crash message i rebooted.

---

