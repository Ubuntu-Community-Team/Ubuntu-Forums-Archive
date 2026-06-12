---
title: "ESTON 610U EDGE Modem"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by shafikulazamkhan on 2007-10-12
Please any one can help me how to configure ESTON 610U EDGE Modem in Linux.

Modem description is:
Brand: Eston
Model: 610U
FEATURE 
Quad-band radio card suitable for use on EGRPS/GPRS/GSM networks worldwide 
EGRPS 180 kbps high-speed data performance, GPRS/GSM data speeds to 85.6 kbps (Network dependent) 
Compatible with most notebooks providing a Type II PC-Card slot and utilizing Microsoft Windows Operating Systems 
ESTON software (Connections Manager ,CALL and SMS centre) 
SPECIFICATIONS 

.A EDGE/GPRS/GSM Air interface: 
Quad-band operation GSM850, EGSM 900, DCS 1800, PCS 1900 
GSM Power Class 4 (2W) for 850/900 bands, GSM Power Class 1 (1W) for 1800/1900 bands 
EDGE class E2 (+27dBm in 850/900 bands, +26dBm in 1800/1900 bands) 
GSM/GPRS Rel '97; PCS1900 Rel '98; EGPRS Rel '99 compliant 
B EGPRS/GPRS (PS) feature set: 
GPRS/EGPRS Multislot Class 12 
GRPS/EGPRS Class B Type 1 MT 
GPRS CS1-CS4; EGPRS MCS1-MCS9 
C GSM feature set: 
GSM Circuit Switched data: 14.4 and 9.6 kbps 
D Terminal Equipment interfaces: 
Operating Systems: Windows 2000/XP Home/XP Pro 
AT interface with standard modem emulation for compatibility with terminal programs/dialers and non-Microsoft operating systems 
HARDWARE SPECIFICATIONS 
Card Type: USB INTERFACE 
Antenna: Flexible antenna with 360 degree rotate able 
LED indication:Power LED,Active LED 
SIM card interface: 3.0V interface

**My wvdial is:**
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","gpinternet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Username =
Password =


**bulan@bulan-desktop:~$ wvdial**
--> WvDial: Internet dialer version 1.56
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

root@bulan-desktop:~# **cat /proc/bus/usb/devices**

T: Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=480 MxCh= 6
B: Alloc= 0/800 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 2.00 Cls=09(hub ) Sub=00 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-15-generic ehci_hcd
S: Product=EHCI Host Controller
S: SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 4 Ivl=256ms

T: Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 2
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S: Product=UHCI Host Controller
S: SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 2
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S: Product=UHCI Host Controller
S: SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#= 1 Spd=12 MxCh= 2
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S: Product=UHCI Host Controller
S: SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms

T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 2 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
P: Vendor=067b ProdID=0610 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E: Ad=81(I) Atr=03(Int.) MxPS= 10 Ivl=1ms
E: Ad=02(O) Atr=02(Bulk) MxPS= 64 Ivl=0ms
E: Ad=83(I) Atr=02(Bulk) MxPS= 64 Ivl=0ms


root@bulan-desktop:~# **sudo lshw -C bus**
*-core 
description: Motherboard
product: P4B533-X
vendor: ASUSTeK Computer INC.
physical id: 0
version: Rev 1.xx
serial: MB-1234567890
slot: USB1
*-usb:0
description: USB Controller
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@00:1d.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: ioport:eec0-eedf irq:16
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-15-generic uhci_hcd
physical id: 1
bus info: usb@1
logical name: usb1
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb:1
description: USB Controller
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
vendor: Intel Corporation
physical id: 1d.1
bus info: pci@00:1d.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: ioport:ef40-ef5f irq:17
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-15-generic uhci_hcd
physical id: 1
bus info: usb@2
logical name: usb2
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb:2
description: USB Controller
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@00:1d.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0
resources: ioport:ef80-ef9f irq:18
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-15-generic uhci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb:3
description: USB Controller
product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
vendor: Intel Corporation
physical id: 1d.7
bus info: pci@00:1d.7
version: 02
width: 32 bits
clock: 33MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
resources: iomemory:ffaff400-ffaff7ff irq:19
*-usbhost
product: EHCI Host Controller
vendor: Linux 2.6.20-15-generic ehci_hcd
physical id: 1
bus info: usb@4
logical name: usb4
version: 2.06
capabilities: usb-2.00
configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
*-serial UNCLAIMED
description: SMBus
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@00:1f.3
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
resources: ioport:400-41f

---

### Post by mambazo on 2008-07-12
Shafik, I have the very same EDGE modem. Bought it used from a friend. It works great in Windows, but I, too, am struggling to get it working in Linux (Ubuntu Hardy Heron).

I assume you used "modprobe usbserial vendor=0x067b product=0x0611 first. My wvdial.conf is as follows.

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Init1 = AT
Init2 = ATE0
Init3 = AT+IFC=2,2
Init4 = AT+CGDCONT=1,"IP","gpinternet"
Init5 = ATS0=0
ISDN = 0
Modem Type = EDGE 611U MODEM
Phone = *99***1#
Username = any
Password = any
Stupid Mode = 1

The modem init sequences are THE EXACT SAME ONES USED IN WINDOWS. I know this because I extracted them from the modem logs in windows. However, I get the same results as you: "Modem not responding".

I _suspect_ that the broken step we are doing is loading the generic usbserial module. On windows, a 3rd-party driver "usbdrv.sys" or "usb2drv.sys" is used (installed from the included cd) to communicate with the modem, which I don't think would be necessary if the modem did actually use a generial serial over usb interface (like most of the nokia phones that we see in all the bangladeshi blogs about configuring edge modems in linux).

I am now investigating using usbdrv.sys using ndiswrapper, and will continue perusing the web for more info. Worst case scenario, we might have to implement our own customized usbserial module for this modem (as opposed to the generic one we are using). :-) Let's use this forum to add any additional info either of us gets until we nick this problem!

---

### Post by mambazo on 2008-07-12
Sorry, I made a slight blunder. The modem I have is a 611U, not a 610U. However, the hardware is all the same. They use the same drivers. Check out this page:

[http://www.estonwireless.com/english/product-edge-611u.htm](http://www.estonwireless.com/english/product-edge-611u.htm)

The 610U is there as well.

---

