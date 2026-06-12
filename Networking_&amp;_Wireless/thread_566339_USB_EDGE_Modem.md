---
title: "USB EDGE Modem"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by shafikulazamkhan on 2007-10-03
Please anyone can help me how to configure EST-610U USB EDGE Modem

---

### Post by Lambert on 2007-10-03
> **shafikulazamkhan said:**
> Please anyone can help me how to configure EST-610U USB EDGE Modem

There is not a whole lot of information about this device out there. And I'm not sure there will be a driver available to use this. It can be researched but not sure there will be anything found.

Open a terminal and run the following commands and post output here.

```

cat /proc/bus/usb/devices

sudo lshw -C bus

```

you can also call the vendor and ask them about support for linux and see what they can offer.

---

### Post by shafikulazamkhan on 2007-10-04
root@bulan-desktop:~# cat /proc/bus/usb/devices

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-15-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=067b ProdID=0610 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  10 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms


root@bulan-desktop:~# sudo lshw -C bus
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


My vendor ! They have no idea

---

### Post by Lambert on 2007-10-04
Was the modem plugged in to a port when you ran those commands?

If so it wasn't recognized at all. If that is the case and no driver that makes two negatives here and I don't see anyway to get this working under linux.

---

### Post by shafikulazamkhan on 2007-10-05
Yes the modem (EST-610U) was plugged in to a port . . .

My wvdial is:
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

 
bulan@bulan-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Please Help

---

### Post by imyousuf on 2007-12-05
did/do you have any entry with /dev/ttyACM0? Btw I have the same modem. If you are using the modem with Ubuntu please let me know how you did it.

---

