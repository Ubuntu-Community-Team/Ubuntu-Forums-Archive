---
title: "Modules 3G Sierraless MC7710 not detected by network manager"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by isma3 on 2014-03-04
Hello everybody,

Networking manager could not recognize Sierraless MC7710 wireless card although I can see it with an ifconfig -a. I am on Ubuntu 13.10.

I tried different commands

uname -r
```
3.11.0-17-generic

```

lsusb:
```
Bus 001 Device 002: ID 1199:68a3 Sierra Wireless, Inc. MC8700 Modem
```

usb-devices:
```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a3 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
S:  SerialNumber=358178041213754
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra_net
```


dmsg | grep 1-1
```
[    1.684038] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.817692] usb 1-1: config 1 has an invalid interface number: 7 but max is 5
[    1.817702] usb 1-1: config 1 has no interface number 5
[    1.819686] usb 1-1: New USB device found, idVendor=1199, idProduct=68a3
[    1.819694] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[    1.819700] usb 1-1: Product: MC7710
[    1.819706] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
[    1.819711] usb 1-1: SerialNumber: 358178041213754
[    4.648877] sierra 1-1:1.0: Sierra USB modem converter detected
[    4.685581] usb 1-1: Sierra USB modem converter now attached to ttyUSB0
[    4.685687] sierra 1-1:1.1: Sierra USB modem converter detected
[    4.686324] usb 1-1: Sierra USB modem converter now attached to ttyUSB1
[    4.686412] sierra 1-1:1.2: Sierra USB modem converter detected
[    4.687094] usb 1-1: Sierra USB modem converter now attached to ttyUSB2
[    4.687187] sierra 1-1:1.3: Sierra USB modem converter detected
[    4.693067] usb 1-1: Sierra USB modem converter now attached to ttyUSB3
[    4.693167] sierra 1-1:1.4: Sierra USB modem converter detected
[    4.693876] usb 1-1: Sierra USB modem converter now attached to ttyUSB4
[    4.794496] sierra_net 1-1:1.7 wwan0: register 'sierra_net' at usb-0000:00:1a.7-1, Sierra Wireless USB-to-WWAN Modem, 1a:04:fa:80:01:07
[    5.336923] hid-generic 0003:413C:2011.0003: input,hidraw2: USB HID v1.10 Keyboard [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:1d.1-1.1/input0
[    5.353038] hid-generic 0003:413C:2011.0004: input,hidraw3: USB HID v1.10 Device [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:1d.1-1.1/input1

```

rfkill list:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

ls -l /dev/serial/by-id:
```
lrwxrwxrwx 1 root root 13 Mär  3 14:26 usb-Sierra_Wireless__Incorporated_MC7710_358178041213754-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 Mär  3 14:26 usb-Sierra_Wireless__Incorporated_MC7710_358178041213754-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 Mär  3 14:26 usb-Sierra_Wireless__Incorporated_MC7710_358178041213754-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 Mär  3 14:26 usb-Sierra_Wireless__Incorporated_MC7710_358178041213754-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root 13 Mär  3 14:26 usb-Sierra_Wireless__Incorporated_MC7710_358178041213754-if04-port0 -> ../../ttyUSB4
```

Connection to the device via minicom on ttyUSB2 and ttyUSB3 fails and even make the terminal unresponsive (must close the tab). 

I also tried to install driver from mycusthelp ([http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?aid=44](http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?aid=44)) but it doesn't compiled.

Is the firmware causing this ?Any idea ?

---

### Post by varunendra on 2014-03-05
Welcome to the forums isma3!

Please read these threads thoroughly, they contain both the explanation and solution to the problem (understanding the explanation helps deciding what would be the best approach for you) :
[http://ubuntuforums.org/showthread.php?t=2165362](http://ubuntuforums.org/showthread.php?t=2165362)
[http://ubuntuforums.org/showthread.php?t=2121838](http://ubuntuforums.org/showthread.php?t=2121838)

If you have problem following the suggestions in them, or they don't work for you, feel free to add a post in them with a short description to your problem and a link to this thread. Hopefully, bmork would be interested in helping you out since you are using one of the latest kernels.

---

### Post by isma3 on 2014-03-05
Thank you for your reply varunendra. I studied both of link you send me but I think the problem is different because in both case the Sierra module uses the cdc_mbim driver while in my case it uses the official driver (Sierra).
So any suggestion ?

---

### Post by bmork on 2014-03-06
> **isma3 said:**
> I studied both of link you send me but I think the problem is different because in both case the Sierra module uses the cdc_mbim driver while in my case it uses the official driver (Sierra).


Yes, I agree. You are using the MC7710 in DirectIP mode (notice that the USB PID is different from QMI/MBIM mode: 68a3 != 68a2) with the sierra and sierra_net drivers, and all should be fine from the kernel/driver point of view.  I guess that makes this a ModemManager/NetworkManager problem.  I don't know how to solve that.

Regarding the problems with ttyUSB2 and ttyUSB3, I believe that is expected. Only some of the serial functions are AT command speaking modem functions, and even some of those can have limited functionality.  The other ports are CnS, NMEA or something else and may appear unresponsive in minicom.

But ModemManager should be able to probe the correct ports, and also support the sierra_net DirectIP driver.

---

### Post by isma3 on 2014-04-01
Hi all,

I have great news about the sierraless. I just updated the firmware thanks to their tools on serra wireless website. 
It's just available on windows.

---

