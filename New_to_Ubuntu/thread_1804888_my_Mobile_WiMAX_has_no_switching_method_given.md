---
title: "my Mobile WiMAX has no switching method given"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by olderek on 2011-07-15
hello guys, 
i have a little problem with my mobile wimax adapter. when i research on ways of installing it, i get messages asking me to install usb_modeswitch, which i already have installed on my ubuntu 11.04. my machine is an acer aspire 55732z. when using other modems, i get no problems, coz i just click on the network icon and install the modem. but for this one, its different. when i plug it in, usb_modeswitch is supposed to switch it from storage to modem device, but nothing happens, not even an icon of the modem. my wimax adapter has no storage capabilities. 

when i run **lsusb **this is what i get.

olderek@old5732Z:~$ sudo lsusb
[sudo] password for olderek: 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 198f:0220 Beceem Communications Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
olderek@old5732Z:~$ sudo usb_modeswitch -v 198f -p bccd
[sudo] password for olderek: 

Looking for default devices ...
 No devices in default mode found. Nothing to do. Bye.

olderek@old5732Z:~$ sudo usb_modeswitch -v 198f -p 0220

Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 003 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x02 (out) and 0x81 (in)
Using endpoints 0x02 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: Beceem Communications
     Product: BCSM250 Mobile WiMAX
  Serial No.: 123456789012345678901234567890
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

olderek@old5732Z:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 198f:0220 Beceem Communications Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

when i look through to usb_modeswitch folder in my **/usr/share/usb_modeswitch**, i get this ########################################################
# Beceem BCSM250

DefaultVendor= 0x198f
DefaultProduct=0xbccd

TargetVendor=  0x198f
TargetProduct= 0x0220

CheckSuccess=20

MessageContent="55534243f0298d8124000000800006bc626563240000000000000000000000"

NoDriverLoading=1

-------------------------------------------
somebody pliz help me and let me know what to do with my modem to get it working coz i really need to use the data on the modem for a lot of work. pliz

---

### Post by gandaran on 2011-07-15
well, if usb-modeswitch doesn't support your wimax modem yet then you should try install a newer version or even download the source code, adapt the source code to include the wimax modem model then compile the source code, (I used to do that on the libccid package to make a usb card reader work in Linux) or see if the wimax modem brand website provides Linux drivers.
sorry if this didn't help.

edit:
[check this]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=2103&sid=2192ce6ba8b6277f3443ed6d320babe7")

---

### Post by olderek on 2011-07-15
hey, this is what i get when i run this command
[B]
olderek@old5732Z:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.[/B] [B]

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   [/B] [B]
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?[/B]  [B]
Did you configure it properly with setserial?
[/B]
why is it that non of my serial ports cant detect my modem? yet when i plug in other modems, it works without any trouble.
somebody please tell me how to make my mobile wimax moden be detected. pliz pliz pliz
when i plug in my modem, nothing happens in ubuntu. not even an icon or anything changes, everything stays still. no icon in network manager, no storage device shows up, although it doesnt have a storage device. does this mean that there may not be any drivers for my modem?

---

### Post by olderek on 2011-07-20
anybody pliz help...

---

