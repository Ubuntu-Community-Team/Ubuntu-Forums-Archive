---
title: "Wireless and modem networks slow/no connection"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by PotatoHead007 on 2014-07-21
Hello :)

I have been using Ubuntu 14.04 LTS since it came out. Until a few days ago, all networking worked perfect. But now, both my wireless and Huwaei modem have very bad internet conenction (less than 80kb/s). Since i live in South Africa, i don't expect 1500kb/s, but until now, i got a steady, much faster speed. 

For the Wireless network, i have tried many methods, such as this:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
and this:
```

sudo iwconfig wlan0 power off

```
Nothing worked.

For the modem, i have found no possible solutions.

Maybe it was an Update of the kernel? No idea :/ Any help appreciated, my school is online, and this does not help.

---

### Post by praseodym on 2014-07-21
Lets check:
```

lspci -nnk | grep -iA2 net
lsusb
usb-devices
lsmod
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by PotatoHead007 on 2014-07-21
lspci -nnk | grep -iA2 net:
```

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c652]
    Kernel driver in use: r8169

```
lsusb
```

Bus 002 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 004: ID e0ff:0005  
Bus 002 Device 010: ID 03f0:5912 Hewlett-Packard 
Bus 002 Device 009: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 008: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2232:1029  
Bus 001 Device 003: ID 19d2:0082 ZTE WCDMA Technologies MSM 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
usb-devices:
```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0082 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=P680A1ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2232 ProdID=1029 Rev=00.25
S:  Manufacturer=Generic
S:  Product=WebCam SC-13HDL11939N
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=32.98
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=03 Prnt=03 Port=01 Cnt=01 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04d9 ProdID=1605 Rev=01.01
S:  Manufacturer= 
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=03 Prnt=03 Port=02 Cnt=02 Dev#=  7 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=85.36
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=03 Prnt=03 Port=03 Cnt=03 Dev#=  8 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=058f ProdID=9254 Rev=03.12
S:  Manufacturer=ALCOR
S:  Product=Generic USB Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=04 Prnt=08 Port=00 Cnt=01 Dev#=  9 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=058f ProdID=9254 Rev=03.12
S:  Manufacturer=ALCOR
S:  Product=Generic USB Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=05 Prnt=09 Port=00 Cnt=01 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=5912 Rev=01.00
S:  Manufacturer=HP
S:  Product=Officejet Pro 8600
S:  SerialNumber=CN2CJBWK3605KC
C:  #Ifs= 4 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=e0ff ProdID=0005 Rev=00.01
S:  Manufacturer=Areson
S:  Product=USB Device
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0cf3 ProdID=3004 Rev=00.02
S:  Manufacturer=Atheros Communications
S:  Product=Bluetooth USB Host Controller
S:  SerialNumber=Alaska Day 2006
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

```
ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr e8:03:9a:f1:bf:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168769 (168.7 KB)  TX bytes:168769 (168.7 KB)

wlan0     Link encap:Ethernet  HWaddr 50:b7:c3:3b:97:d9  
          inet addr:10.0.0.7  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52b7:c3ff:fe3b:97d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:398187 (398.1 KB)  TX bytes:121416 (121.4 KB)

```
iwconfig:
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Griffin Wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:F1:DF:47:AE:1E   
          Bit Rate=135 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:93   Missed beacon:0

```
sudo iwlist chan(only pasted the scan my wireless network):
```

wlan0     Scan completed :
          Cell 01 - Address: AC:F1:DF:47:AE:1E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Griffin Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022e7f09287
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00104772696666696E20576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051600000000000000000000000000000000000000
                    IE: Unknown: DD090010180207F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```
cat /etc/resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Home

```

Most of this means nothing to me, but maybe you can make something out :)

---

### Post by praseodym on 2014-07-21
First thing: You have an Atheros card:

```
sudo rm /etc/modprobe.d/iwlwifi.conf
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Second: For the LAN device you may want to change the driver according to this (black boxes):
[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms)

Third: For WWAN check this checklist:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by PotatoHead007 on 2014-07-21
I am working on wireless first. I did what you told me, and it did not do what it should do. Instead, it made the speed even slower. What happens now is that the speed shoots up high for a few seconds when loading a web-page, then goes down to an incredibly slow speed. After this, i found another supposed solution and tried it:

[code]
sudo gedit /etc/nsswitch.conf
[code]
And replacing "hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4" with "hosts:          files dns"
This did not change the network speed either.

**Edit:**I read that updating the linux kernel can help, how do i do this manually?

---

### Post by PotatoHead007 on 2014-07-25
**Sovled: **Doing my updates, thus updating the kernel, solved the issue. Thanks for your help :)

---

