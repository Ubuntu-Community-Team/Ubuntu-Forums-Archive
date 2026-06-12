---
title: "bluetooth - Vaio VGN-TT11WN and belkin dongle - can't connect"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by grumblesnakes on 2016-07-14
I've recently switched to Ubuntu from Win 10, mostly because it runs a  lot better on this laptop, but unfortunately it has some issues, one of  which is that I can't get my Microsoft 3600 bluetooth mouse paired. 
The  internal bluetooth 2.0 adapter doesn't work at all, as such I had  bought a Belkin 4.0 bluetooth dongle, but I can't seem to get it to work  on Ubuntu. 
I've used Linux on occasion, but my knowledge is  still very limited. I 've searched around and tried to follow  instructions from people with similar issues, but I think It is time I  get some personalized help.
I've seen certain commands repeated several times, as such I'm posting a few of those beforehand. 


   lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````

Bus 007 Device 005: ID 0421:06fb Nokia Mobile Phones 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 050d:065a Belkin Components F8T065BF Mini Bluetooth 4.0 Adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0af0:7601 Option Globetrotter MO40x 3G Modem (GTM 382)
Bus 001 Device 003: ID 05ca:18b1 Ricoh Co., Ltd Sony Vaio Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 044e:3017 Alps Electric Co., Ltd BCM2046 Bluetooth Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

rfkill list all:
```
0: sony-wifi: Wireless LAN
``````

Soft blocked: no
Hard blocked: no
1: sony-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: sony-wwan: Wireless WAN
Soft blocked: no
Hard blocked: no
5: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
6: hso-0: Wireless WAN
Soft blocked: no
Hard blocked: no
7: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```

usb-devices:
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
``````

D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05ca ProdID=18b1 Rev=10.00
S:  Manufacturer=Ricoh co. Ltd.
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0af0 ProdID=7601 Rev=00.00
S:  Manufacturer=Option N.V.
S:  Product=Globetrotter HSUPA Modem
C:  #Ifs=10 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 5 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 6 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 7 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 8 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 9 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=147e ProdID=1000 Rev=00.33
S:  Manufacturer=TouchStrip        
S:  Product=Fingerprint Sensor   
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=044e ProdID=3017 Rev=02.27
S:  Manufacturer=Broadcom Corp
S:  Product=BCM2046 Bluetooth Device
S:  SerialNumber=00214FB6CD6E
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)


T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=050d ProdID=065a Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM20702A0
S:  SerialNumber=5CF3706FE069
C:  #Ifs= 0 Cfg#= 0 Atr= MxPwr=
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bInterfaceNumber': No such file or directory
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bAlternateSetting': No such file or directory
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bNumEndpoints': No such file or directory
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bInterfaceClass': No such file or directory
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bInterfaceSubClass': No such file or directory
cat: '/sys/bus/usb/devices/usb6/6-1/6-*:?.*/bInterfaceProtocol': No such file or directory
/usr/bin/usb-devices: line 79: printf: (none): invalid number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=() Sub= Prot= Driver=


T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=07 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0421 ProdID=06fb Rev=01.00
S:  Manufacturer=Nokia
S:  Product=Nokia 215 (RM-1111)
S:  SerialNumber=534638607040920
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)


T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

lsmod|grep blue:
```
bluetooth             520192  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
``````


```

hcitool dev:
```
Devices:
``````

hci0    00:21:4F:B6:CD:6E

```

hciconfig:
```
hci0:    Type: BR/EDR  Bus: USB
``````

BD Address: 00:21:4F:B6:CD:6E  ACL MTU: 1021:8  SCO MTU: 64:1
UP RUNNING 
RX bytes:637 acl:0 sco:0 events:44 errors:0
TX bytes:4040 acl:0 sco:0 commands:44 errors:0

```


I would appreciate any help I can get.

EDIT: Please ignore the excissive use of code-boxes, the page seems to be adding its own without my consent.

---

### Post by praseodym on 2016-07-15
Please show:
```

modprobe -c | grep -i "050d.*065a"
modprobe -c | grep -i "044e.*3017"
```

---

### Post by jeremy31 on 2016-07-15
Post the result for ```
dmesg | egrep -i 'blue|firm
```

The Ubuntu 16.04 kernel does support your new bluetooth device ```
Bus 006 Device 003: ID 050d:065a Belkin Components F8T065BF Mini Bluetooth 4.0 Adapter
```
But it may need firmware that needs to be converted from hex files in windows drivers
Pilot6 posted a basic how to [http://askubuntu.com/a/632348/300665](http://askubuntu.com/a/632348/300665)

---

