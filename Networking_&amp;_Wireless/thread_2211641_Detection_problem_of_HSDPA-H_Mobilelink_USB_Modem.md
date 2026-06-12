---
title: "Detection problem of HSDPA-H Mobilelink USB Modem"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by jc2254 on 2014-03-17
I have following the answer detailing in the thread ([3G USB Modem Not Working in 12.04]("http://askubuntu.com/questions/143989/3g-usb-modem-not-working-in-12-04")) to detect my USB modem, HSDPA-H Mobilelink. (Qualcomm incorporated, 20a6:f00e is the product ID I get with lsusb and usb-devices)


[LIST=1]
[*]sudu do
[*]nano /usr/bin/usbModemScript and type
#!/bin/bashecho 20a6 f00e > /sys/bus/usb-serial/drivers/option1/new_id

Then save and exit.
[*]chmod +x /usr/bin/usbModemScript
[*]nano /etc/udev/rules.d/option.rules and type
ATTRS{idVendor}=="20a6", ATTRS{idProduct}=="f00e", RUN+="/usr/bin/usbModemScript"
ATTRS{idVendor}=="20a6", ATTRS{idProduct}=="f00e", RUN+="/sbin/modprobe option" 

Then save and exit.
[*]sudo reboot
[/LIST]

After the reboot, the modem can be detected and I am able to connect to the internet. However, sometimes when I turn on my computer, the modem cannot be detected, and I need to reboot my computer, and after reboot, it shows up in the Network manager again. The modem cannot be detected again once I plugged off it and re-plug again.  
This also happens when I hibernate my computer. Before hibernate, the modem can be detected but after hibernate it cannot. I have already try re-plug the USB modem and restart the network manager: sudo service network-manager restart, but it still cannot work.

Is there anyway that I can detect my USB modem again without reboot? I am using Ubuntu 12.04 in HP Pavilion dv4-1015TX.

This is the information from usb-devices.

T:  Bus=02 Lev=01 Prnt=01 Port=01Cnt=01 Dev#=  4 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=20a6 ProdID=f00e Rev=00.00 
S:  Manufacturer=Modem 
S:  Product=Modem Device 
S:  SerialNumber=000000000002 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage

---

### Post by jc2254 on 2014-03-18
Anybody have an ideal how to approach the problem?

---

