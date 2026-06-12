---
title: "BSNL 3G Data Card(Teracom) Confguration Problem"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by desaivarun_104lts on 2011-05-15
Hi,

Recently,i bought an BSNL 3G USB Data Card..The Details of the Data Card are : 
Hardware Version : V1.0
Software Version:LW273 V1.2
Manufacturer of the Device is: Teracom Ltd

The problem is i am unable to connect to the data card in ubuntu..When i insert the data card,initially the red light in the
data card glows for few seconds and then the green light glows.I tried to connect the device with Network Applet present in the panel.I selected new connection and added the device with all the deails(apn:bsnlnet,username,password,number=*99#).
Sometimes the network applet connects and it show's BSNl 3G Connection has been established.But it will not connect to the internet.The same device,in the same location with windows OS,it connects and the speed is also extremely good.I googled for this,but i cant found exact solution.

The Device consists a folder,i will attach the folder with this one,The output of the lsusb,usb-devices,nm-tool,etc., are also attached.
I am using Acer Aspire one 532H(A0532H) with ubuntu 11.04 Natty Narwahal.I am using 32 Bit.

The folder consists of a deb one,which i tri

Please,help me as early as possible.I cant buy any other Device once again,and for this only sake i am not ready to switch to Windows again..

Waiting for the help.

1) The output of the lsusb is 

-----------------------------------------------------------------------------------------------------------------------------

varun@varun-AO532h:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 230d:0001  
Bus 001 Device 002: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In the above one the 230d:0001 is my Data card
-----------------------------------------------------------------------------------------------------------------------------

2) The output of the nm-tool

----------------------------------------------------------------------------------------------------------------------------
varun@varun-AO532h:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        70:5A:B6:CD:D5:4F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        F0:7B:CB:7C:61:F5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: ttyACM3 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:

------------------------------------------------------------------------------------------------------------------------------

3) The output of the usb-devices



varun@varun-AO532h:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  3
P:  Vendor=230d ProdID=0001 Rev=00.00
S:  Manufacturer=HSPADataCard
S:  Product=HSPADataCard
S:  SerialNumber=8444311594054030
C:  #Ifs=10 Cfg#= 3 Atr=e0 MxPwr=20mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=09 Prot=01 Driver=cdc_wdm
I:  If#= 6 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 7 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=064e ProdID=a102 Rev=03.10
S:  Manufacturer=SuYin
S:  Product=WebCam
S:  SerialNumber=CN0316-S30C-OV11-VA-R03.01.00
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
-----------------------------------------------------------------------------------------------------------------------------
4) The Output of the ls -al /dev/serial/by-id is

-----------------------------------------------------------------------------------------------------------------------------
varun@varun-AO532h:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-05-15 08:41 .
drwxr-xr-x 4 root root 80 2011-05-15 08:41 ..
lrwxrwxrwx 1 root root 13 2011-05-15 08:41 usb-HSPADataCard_HSPADataCard_8444311594054030-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-05-15 08:41 usb-HSPADataCard_HSPADataCard_8444311594054030-if03 -> ../../ttyACM1
-----------------------------------------------------------------
5) The deb folder given in the Device

-----------------------------------------------------------------
[http://ubuntuone.com/p/tNG/](http://ubuntuone.com/p/tNG/)

-----------------------------------------------------------------

---

### Post by ramakicha@yahoo.com on 2011-06-14
Did you solve this problem. I am also having the same problem. If you have solved it kindly let me know how you solved it.

---

### Post by dineshs on 2011-06-17
Did you try network manager(rightclick network manager icon-edit connections-mobile broadband...) ?
You may also try wvdial and see [this]("http://ubuntuforums.org/showthread.php?t=1783650&highlight=pppoe") thread.
Note:For bsnl wvdial.conf may look like
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,,"bsnlnet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = 944*******
Username = 944*******
New PPPD = yes
Stupid Mode = yes
#Auto DNS = yes
```

---

