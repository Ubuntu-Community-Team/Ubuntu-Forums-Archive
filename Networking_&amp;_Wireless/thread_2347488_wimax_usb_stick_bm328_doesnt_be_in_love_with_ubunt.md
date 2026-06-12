---
title: "wimax usb stick bm328 doesnt be in love with ubuntu"
date: 2016-12-25
forum: Networking &amp; Wireless
---

### Post by abukhshaim on 2016-12-25
Hello guys : I'm on Ubuntu 14.04 LTS (64BIT) with kernel 4.4.0-58-generic and  this my first time using Ubuntu. Before I wrote this thread I did a wide  search in Ubuntu forums and also outside Ubuntu looking to sort up my  problem but I couldn't find any solution. I have a Wimax usb stick BM328  "dongle" with a Beceem Communications Inc chipset .. when I plug it  nothing happened. I tried a lot of solutions,some of them say I have to  switch modem i did it but nothing changed . the others say I shouldn't  switch modem because it's already switched.so I'm completely confused .. any help would be really appreciated  here are my command' results :

  [```
CODE]   musab@musab-OptiPlex-360:~$ [COLOR=#ff0000]lsusb[/COLOR]
[COLOR=#008000]**Bus 001 Device 010: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter**[/COLOR]
Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:c10a A4Tech Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
musab@musab-OptiPlex-360:~$ 
```

```
musab@musab-OptiPlex-360:~$[COLOR=#ff0000] usb-devices[/COLOR]

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-58-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=8178 Rev=02.00
S:  Manufacturer=802.11n
S:  Product=USB WLAN
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8192cu

[COLOR=#008000]T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=198f ProdID=0220 Rev=00.01
S:  Manufacturer=HUAWEI
S:  Product=WiMAX USB Stick
S:  SerialNumber=0
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
[/COLOR]
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-58-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a12 ProdID=0001 Rev=19.58
C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-58-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=09da ProdID=c10a Rev=03.14
S:  Manufacturer=A4Tech
S:  Product=USB Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-58-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=2003 Rev=03.06
S:  Manufacturer=Dell
S:  Product=Dell USB Keyboard
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=70mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=04.04
S:  Manufacturer=Linux 4.4.0-58-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
musab@musab-OptiPlex-360:~$
```

[COLOR=#ff0000]and thanks in advance  [/COLOR]

---

### Post by wildmanne39 on 2016-12-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by abukhshaim on 2016-12-25
Thanks for the notification O:)

---

### Post by praseodym on 2016-12-26
Hi,

it already switched into modem mode. Is it shown as "wired connection" in the network-manager settings? Does it have a web interface to configure?

Please also check

```
mmcli -m [COLOR="#FF0000"]0[/COLOR] | grep -Ev "imei|equipment|Numbers"
```
No output? Increase the "0" to "1", "2", etc

---

### Post by abukhshaim on 2016-12-26
Hi,
No, it doesn't appear in the network manager settings ans also doesn't have interface
this is the result of the commend :

```
musab@musab-OptiPlex-360:~$ mmcli -m 1 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/1'
musab@musab-OptiPlex-360:~$ mmcli -m 2 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/2'
musab@musab-OptiPlex-360:~$ mmcli -m 3 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/3'
musab@musab-OptiPlex-360:~$ mmcli -m 4 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/4'
musab@musab-OptiPlex-360:~$ mmcli -m 5 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/5'
musab@musab-OptiPlex-360:~$ mmcli -m 6 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/6'
musab@musab-OptiPlex-360:~$ mmcli -m 7 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/7'
musab@musab-OptiPlex-360:~$ mmcli -m 8 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/8'
musab@musab-OptiPlex-360:~$ mmcli -m 9 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/9'
musab@musab-OptiPlex-360:~$ mmcli -m 10 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/10'
musab@musab-OptiPlex-360:~$ mmcli -m 11 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/11'
musab@musab-OptiPlex-360:~$ mmcli -m 12 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/12'
musab@musab-OptiPlex-360:~$ mmcli -m 13 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/13'
musab@musab-OptiPlex-360:~$ mmcli -m 14 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/14'
musab@musab-OptiPlex-360:~$ mmcli -m 15 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/15'
musab@musab-OptiPlex-360:~$ mmcli -m 16 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/16'
musab@musab-OptiPlex-360:~$ mmcli -m 17 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/17'
musab@musab-OptiPlex-360:~$ mmcli -m 18 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/18'
musab@musab-OptiPlex-360:~$ mmcli -m 19 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/19'
musab@musab-OptiPlex-360:~$ mmcli -m 20 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/20'
musab@musab-OptiPlex-360:~$ 
```
 thanks for reply

---

### Post by abukhshaim on 2016-12-28
more than 400 views  :confused:  please help 
what does this out put mean ?
```
root@musab-OptiPlex-360:/home/musab# dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.758646] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[   13.145792] usbserial: USB Serial support registered for GSM modem (1-port)
[   13.178598] option 1-8:1.0: GSM modem (1-port) converter detected
[   13.178812] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
root@musab-OptiPlex-360:/home/musab#
```

---

### Post by abukhshaim on 2017-01-02
;)

---

