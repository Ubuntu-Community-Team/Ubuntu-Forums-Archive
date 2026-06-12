---
title: "Mobile Broadband Connection Problem"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by Gustavo_Rojas on 2014-06-02
Hello ubuntu community, im a nob in linux. I just installed my first linux based OS a week ago, Ubuntu 14.04. Im trying to connect to internet with a Huawei USB mobile broadband 3G dongle, model EC156.
I have search, research and try some posibles solutions, but none have functioned to me.

1.First i tried usb_modeswitch creating a config file into /etc/usb_modeswitch.d with these data:
[ATTACH=CONFIG]253678[/ATTACH]
> DefaultVendor=  0x12d1
DefaultProduct= 0x140c
MessageContent="55534243123456780000000000000011062000000100000000000000000000"



Here the information of modeswitch:


gauchorojas@GustavoRojasSatellite:~$ cd /etc/usb_modeswitch.d
gauchorojas@GustavoRojasSatellite:/etc/usb_modeswitch.d$ sudo usb_modeswitch -I -W -c 12d1\:140c
[sudo] password for gauchorojas: 


Read config file: 12d1:140c


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.1.1 (C) Josua Dietze 2014
 * Based on libusb1/libusbx


 ! PLEASE REPORT NEW CONFIGURATIONS !


DefaultVendor=  0x12d1
DefaultProduct= 0x140c
MessageContent="55534243123456780000000000000011062000000100000000000000000000"

NeedResponse=0


InquireDevice=1


Look for default devices ...
  found USB ID 12d1:140c
   vendor ID matched
   product ID matched
  found USB ID 8087:0020
  found USB ID 1d6b:0002
  found USB ID 064e:d104
  found USB ID 8087:0020
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 006 on bus 002
Current configuration number is 1
Use interface number 0
Use endpoints 0x02 (out) and 0x82 (in)
Error: can't use storage command in MessageContent with interface 0;
       interface class is 255, expected 8. Abort


2.Then i tried this of modprobe option and echo:
[ATTACH=CONFIG]253679[/ATTACH]
T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140c Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 5 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
root@GustavoRojasSatellite:/etc/usb_modeswitch.d# modprobe option
root@GustavoRojasSatellite:/etc/usb_modeswitch.d# echo 12D1 140C > /sys/bus/usb-serial/drivers/option1/new_id
root@GustavoRojasSatellite:/etc/usb_modeswitch.d# 

I can see the usb in the section of "Disks", but when i plugged in the USB, nothing happens. 
Somehelp?
Thankyou,
Gustavo Rojas

PS: i had connected to internet and used correctly the usb mobile broadband connection in Windows 7.

---

