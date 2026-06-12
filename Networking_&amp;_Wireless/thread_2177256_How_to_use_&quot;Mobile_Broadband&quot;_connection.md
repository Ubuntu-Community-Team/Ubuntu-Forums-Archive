---
title: "How to use &quot;Mobile Broadband&quot; connection with a 3G USB stick modem"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by PHP_Learner on 2013-09-28
[IMG]http://ubuntuforums.org/images/icons/icon3.png[/IMG]Dear all

I have a 3G USB stick modem (D-Link DWM-156) and it uses a 3G SIM with PIN enabled to connect to network. Detailed information about it is as follows:
> 
T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=7d00 Rev=02.00
S:  Manufacturer=D-Link,Inc  
S:  Product=D-Link DWM-156
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=01 Driver=usbfs
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=usbfs
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usbfs

> Hardware version: A6
Firmware version (printed on the back of the device): 6.0.3 ME
Firmware version (displayed in the Windows software): 2.2.2

[B]
Any one knows why these two firmware versions are not same?[/B]

For Windows OS, there is a driver and software called "D-Link Connection Manager" for using the device:[IMG]http://www.rightel.ir/content/images/help/rightel-dongle-14.jpg[/IMG]
 and it works properly in Windows:

But I do not know how to use this device in Ubuntu (13.04)?
Ubuntu help says:> Most mobile broadband devices should be recognized automatically when you connect them to your computer
I followed the steps in Ubuntu help to create a new "Mobile Broadband" connection using "Edit Connection" from menu bar.
After that, how i can connect using this connection? When I click the network menu in menu bar, the connection I created is not listed!

I also followed the steps described by "Alaa" in this link: [http://www.askubuntu.com/questions/168663/enabling-or-installing-d-link-dwm-156-broadband-modem/169144#169144](http://www.askubuntu.com/questions/168663/enabling-or-installing-d-link-dwm-156-broadband-modem/169144#169144)
But there whenever I enter the command: "usbdeviceswitchdlink" I receive following error:

```
file : usbdeviceswitchdlink.c
starting......................vid:8193 pid: 32000
vid:32903 pid: 32
vid:7531 pid: 2
vid:16700 pid: 33120
vid:16700 pid: 33122
vid:16700 pid: 33121
vid:2652 pid: 17664
vid:3141 pid: 25629
vid:32903 pid: 32
vid:7531 pid: 2
right_dev
usb_open
Error: could not access device. Aborting

ending......................
```

The result for "usbdeviceswitchdlink" command is the same either the modem is connected or not!

**I found an error in "dmesg<" output that may help to solve the problem:**
In dmesg output file, it is clear that the device VID/PID just after connecting to the machine is: 2001:a80b.
This VID/PID pair is listed in "/lib/udev/rules.d/40-usb_modeswitch.rules" and thus usb_modeswitch detects this device and is runned after connecting the device and it is listed in dmesg output.
after mode switch, VID/PID changes to 2001:7d00 and the device connects as a modem. But at the end it seems that an error occurs and prevents the device to work properly. dmesg output is as follows:
```
[ 1379.017488] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[ 1379.110308] usb 2-1.2: New USB device found, idVendor=2001, idProduct=a80b
[ 1379.110316] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1379.110322] usb 2-1.2: Product: D-Link DWM-156
[ 1379.110327] usb 2-1.2: Manufacturer: D-Link,Inc  
[ 1379.110331] usb 2-1.2: SerialNumber: 523254402666151
[ 1379.110979] scsi9 : usb-storage 2-1.2:1.0
[ 1380.109986] scsi 9:0:0:0: CD-ROM            HSPA USB SCSI CD-ROM      6229 PQ: 0 ANSI: 0 CCS
[ 1380.112144] sr1: scsi3-mmc drive: 0x/0x caddy
[ 1380.112440] sr 9:0:0:0: Attached scsi CD-ROM sr1
[ 1380.112630] sr 9:0:0:0: Attached scsi generic sg2 type 5
[ 1380.442868] usb 2-1.2: USB disconnect, device number 5
[ 1381.124580] usb 2-1.2: new high-speed USB device number 6 using ehci-pci
[ 1381.217917] usb 2-1.2: New USB device found, idVendor=2001, idProduct=7d00
[ 1381.217926] usb 2-1.2: New USB device strings: Mfr=5, Product=6, SerialNumber=0
[ 1381.217932] usb 2-1.2: Product: D-Link DWM-156
[ 1381.217936] usb 2-1.2: Manufacturer: D-Link,Inc  
[ 1381.219219] scsi10 : usb-storage 2-1.2:1.2
[ 1382.217013] scsi 10:0:0:0: Direct-Access     HSPA USB SCSI CD-ROM      6229 PQ: 0 ANSI: 0 CCS
[ 1382.217996] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1382.219455] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 1383.580900] usb_modeswitch_[5343]: segfault at 0 ip 00007f3016767c51 sp 00007fff650d1fa8 error 4 in libc-2.17.so[7f30166de000+1be000]
```

---

### Post by praseodym on 2013-09-28
Hi,

did you install usb-modeswitch? Obviously, the stick is in storage-mode:
```

sudo apt-get install usb-modeswitch
```

---

### Post by PHP_Learner on 2013-09-30
> **praseodym said:**
> Hi,

did you install usb-modeswitch? Obviously, the stick is in storage-mode:
```

sudo apt-get install usb-modeswitch
```

Yes, usb-modeswitch is installed on my machine.

---

### Post by praseodym on 2013-09-30
Can you remove the hard drive manually (unmount)?

---

