---
title: "Problem with my Dicota USB Network Interface"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by sonic_275 on 2006-08-25
I recently installed an Ubuntu 6.06 with all latest upgrades (current kernel 2.6.15-26-386).

Every 2 seconds, I get dozens of lines of the following output to the console :
```
[<current time>] pegasus 3-1.2:1.0: ctrl_callback, status -71

```

It happens that I use a Dicota Replicator 2.0, which is a USB device with additional USB ports, PS/2 mouse and keyboard ports, serial port and ethernet port. The kernel module supporting the ethernet port is atually pegasus. From /proc/bus/usb/devices I get
```
T:  Bus=03 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=07a6 ProdID=8515 Rev= 1.01
S:  Manufacturer=ADMtek
S:  Product=USB To LAN Converter
S:  SerialNumber=0001
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=160mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=00 Driver=pegasus
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=125us
```

The Ethernet Interface of this USB device is up on the system, but it doesn't work and I can't get any answer as I try to get an IP adress via DHCP. Moreover I get a weird MAC adress (00:05:00:05:00:05)

My other Ethernet interface, built-in on my laptop, works perfectly with the same network cable.

Is there any way I can get my USB Ethernet interface to work and to stop this error output on my console ?

Thanks.

---

