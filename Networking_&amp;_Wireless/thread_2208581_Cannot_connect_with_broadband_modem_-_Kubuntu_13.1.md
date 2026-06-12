---
title: "Cannot connect with broadband modem - Kubuntu 13.10"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by Ray6010 on 2014-03-01
I am attempting to connect my Kubuntu 13.10 64 bit machine to the internet using a broadband Huawei E303 modem. I have installed usb-modeswitch, gnome-ppp, modemmanager, and network-manager among other things.

I cannot connect and I need to find the port that is being used.

I believe the modeswitch is running based on the fact that a **lsusb** initially gives a:
Bus 001 Device 016: ID 12d1:1f01 Huawei Technologies Co., Ltd.
but later gives a:
Bus 001 Device 017: ID 12d1:14db Huawei Technologies Co., Ltd.

I get the following responses:
**usb-devices**
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14db Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI HiLink
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=06 Prot=00 Driver=cdc_ether

**dmesg | tail**
[ 8119.221926] systemd-udevd[5595]: NAME="hwcdrom" ignored, kernel device nodes can not be renamed; please fix it in /etc/udev/rules.d/10-Huawei-FlashCard.rules:15
[ 8119.534997] systemd-udevd[5595]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 8119.535015] systemd-udevd[5595]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 8119.671257] usb 1-2: USB disconnect, device number 12
[ 8120.844154] usb 1-2: new high-speed USB device number 13 using ehci-pci
[ 8120.977903] usb 1-2: New USB device found, idVendor=12d1, idProduct=14db
[ 8120.977926] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[ 8120.977938] usb 1-2: Product: HUAWEI HiLink
[ 8120.977949] usb 1-2: Manufacturer: HUAWEI
[ 8120.982705] cdc_ether 1-2:1.0 eth2: register 'cdc_ether' at usb-0000:00:12.2-2, CDC Ethernet Device, 58:2c:80:13:92:63

When I do a sudo **gnome-ppp**, and enter a random username and password and phone number, and click Setup then try to detect a modem, I get a message no modem was found on your system.

When I do an **ifconfig** (with the modem plugged in), I get 
eth3      Link encap:Ethernet  HWaddr 58:2c:80:13:92:63  
          inet6 addr: fe80::5a2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7562 (7.5 KB)  TX bytes:15483 (15.4 KB)
          
The modem light is on as if it is connected to the service provider.
Note! eth3 only appears after I plug the modem in.

I am looking to get a connection and also I need to determine the port number so that I can feed this to some SMS software. Does anyone have an idea how to proceed?

Thanks,

Ray

---

