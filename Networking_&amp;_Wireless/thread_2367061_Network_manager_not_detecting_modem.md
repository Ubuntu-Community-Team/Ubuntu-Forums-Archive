---
title: "Network manager not detecting modem"
date: 2017-07-25
forum: Networking &amp; Wireless
---

### Post by Jeyaprakash on 2017-07-25
I am having problem with the usb modem. Sometimes it gets recognised and sometimes I have to unplug and replug or restart the computer to get it recognised. I am using 16.04.2 (32 bit) on my 64 bit desktop computer. I installed just recently. When I installed, everything was fine. After installing all the available updates, the problem started.

with the usb-devices command in terminal, this is what I get when it gets recognised:

```
T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=02 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fff1 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Tech
C:  #Ifs= 6 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```
This is what I get when it does not get recognised:

```
Bus=03 Lev=01 Prnt=01 Port=09 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fff5 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=USB Storage
S:  SerialNumber=000000000002
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

```
I searched google and found one thread where the problem was fixed.

And executed these commands, obtaining from that thread:

sudo su
gedit /usr/bin/option_19d2:fff1 (a blank file opened)

#! /bin/bash
echo 19d2 fff1 > /sys/bus/usb-serial/drivers/option1/new_id (copied this there and saved)

chmod +x /usr/bin/option_19d2:fff1

gedit /etc/udev/rules.d/option.rules (again a blank file opened)

ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff1", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff1", RUN+="/usr/bin/option_19d2:fff1" (pasted this, saved and closed)

Restarted the computer and the problem still remains. 

Kindly help me fix this issue..

---

### Post by praseodym on 2017-07-25
Try
```

sudo service udev reload
sudo service udev restart
```
Did you install usb-modeswitch?

---

### Post by Jeyaprakash on 2017-07-25
Yes usb-modeswitch is already installed. Thats why sometimes it acts as modem. When I turned on the computer, it recognised. Then, I unplugged the modem and plugged again. It did not recognise. Then, I typed the code you had given. It did not help. It is not changing from fff5 to fff1. I typed modprobe option. It also did not change fff5 to fff1. Not sure what I should be doing..

---

### Post by Jeyaprakash on 2017-07-25
I find that when I restart the computer, it works most of the time. Only when I unplug it and insert again, it has problem recognising as modem. At such times, I type in terminal, usb-devices, it gives

```
Bus=03 Lev=01 Prnt=01 Port=09 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fff5 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=USB Storage
S:  SerialNumber=000000000002
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

```
But when I go into disks, it shows this [https://www.dropbox.com/s/jgfk9rndvce5u6v/Screenshot%20at%202017-07-26%2006%3A56%3A52.png?dl=0](https://www.dropbox.com/s/jgfk9rndvce5u6v/Screenshot%20at%202017-07-26%2006%3A56%3A52.png?dl=0)

So, in terminal is shows fff5 and Devices show as fff1. May be some bug?

---

