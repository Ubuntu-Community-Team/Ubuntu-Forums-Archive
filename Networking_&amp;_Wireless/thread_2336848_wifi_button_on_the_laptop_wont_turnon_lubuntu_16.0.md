---
title: "wifi button on the laptop wont turnon lubuntu 16.04 [SOLVED]"
date: 2016-09-12
forum: Networking &amp; Wireless
---

### Post by avisaziz123 on 2016-09-12
Hi today i install lubuntu 16.04 but i cant conect to my wifi my laptop has wifi button but its always orange(off) i try to run nm-applet but get 

error retrieving accesbility bus address: org.freedesktop.dbus.error.serviceunknown: the name org.ally.bus was not provided by any service

I have'nt try to reinstall ubuntu

```
Wireless info

########## wireless info START ##########

Report from: 11 Sep 2016 22:19 EDT -0400

Booted last: 11 Sep 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
	Subsystem: Hewlett-Packard Company 88E8042 PCI-E Fast Ethernet Controller [103c:308c]
	Kernel driver in use: sky2

06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:1508]
	Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2142     1  0 21:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8042 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWAR
```

---

### Post by howefield on 2016-09-12
Thread moved to the "*Networking & Wireless*" forum, for a better fit.

Please read this s[ticky thread]("https://ubuntuforums.org/showthread.php?t=370108") and run the wireless info script as described.

---

### Post by avisaziz123 on 2016-09-12
I have reinstall lubuntu and wifi still doesn work

---

### Post by jeremy31 on 2016-09-12
Try installing the firmware for wifi ```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by avisaziz123 on 2016-09-12
I also try to get update and there is a massage

Unable to locate package

Jeremy i try that and still unable to locate package firmware-b43-installer the laptop doesnt connect to ethernet

---

### Post by jeremy31 on 2016-09-12
See [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978) and see if you can put the zip file on a thumb drive and get it installed

---

### Post by avisaziz123 on 2016-09-12
Still cant detect wifi
The wifi button on the laptop stays orange(off)

---

### Post by jeremy31 on 2016-09-12
Please post results for ```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by avisaziz123 on 2016-09-12
Sure
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
	Subsystem: Hewlett-Packard Company 88E8042 PCI-E Fast Ethernet Controller [103c:308c]
	Kernel driver in use: sky2
	Kernel modules: sky2
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:1508]
	Kernel driver in use: b43-pci-bridge

---

### Post by jeremy31 on 2016-09-12
Lets see ```
dmesg | grep b43
```

---

### Post by avisaziz123 on 2016-09-12
Go to website ???
[code]
[   12.287350] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.317650] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   12.317668] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 2, Version 0
[   12.406993] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2
[   12.407029] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2
[   12.407498] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2
[   12.407516] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2
[   12.407522] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   12.407525] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   12.407528] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website

---

### Post by jeremy31 on 2016-09-12
```
locate ucode15.fw
```
Should tell us if the firmware file is present

---

### Post by avisaziz123 on 2016-09-12
That command shows nothing on the terminal

---

### Post by jeremy31 on 2016-09-12
Did you have trouble with the b43.zip file

---

### Post by avisaziz123 on 2016-09-12
Yes my laptop can loacte and install it

---

### Post by jeremy31 on 2016-09-12
So if you use the file manager and go to Computer-lib/firmware/ is there a b43 folder?  Does it have an X on the icon?

---

### Post by avisaziz123 on 2016-09-12
Yes there is b43 folder WITHOUT X ON THE ICON but when i open it there is nothing inside

Jeremy do i have to copy the b43 to the lib ????

---

### Post by wildmanne39 on 2016-09-12
Hi if you downloaded the file to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here.

Open a terminal and copy and paste the commands one line at a time into the terminal after the commands is finished go the the next line and do the same thing if there are errors keep going until you have run all commands:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo modprobe -rv b43 
sudo modprobe -v b43
```
if it does not come on reboot.
Thanks

---

### Post by avisaziz123 on 2016-09-12
Thank you so much thank you thank you
To all who helped me especially JEREMY and WILD MAN im so happy that my wifi worked

I guess this is solved

---

### Post by wildmanne39 on 2016-09-12
Your welcome! please use thread tools at the top of the page to mark solved.
Enjoy!

---

### Post by ecologito on 2016-11-04
Thank you for posting all the commands to copy the library into the right place. It took me a little while to figure it out but now is up and running. 

GRACIAS!

---

