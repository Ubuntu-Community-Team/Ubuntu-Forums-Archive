---
title: "[SOLVED] internet connection via bluetooth"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by KMuchane on 2008-05-17
Hi,

I would like to connect to the internet via bluetooth, right now I am using a USB connected cellphone with a cable to dialup. I have looked at a few howtos but they tend to miss some valuable details.

1) With the bluetooth dongle connected when I run lsusb, I get:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0e5e:6622  
Bus 001 Device 001: ID 0000:0000 

Shouldn't it indicate there  is a bluetooth device connected?

2) When I run hcitool scan, the computer discovers my the phone and outputs 
its MAC address.


3) When I run sdptool browse <MAC address here>, I get:

sdptool browse 00:1A:1B:06:98:1D 
Browsing 00:1A:1B:06:98:1D ...
Service RecHandle: 0x0
Service Class ID List:
  "SDP Server" (0x1000)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "SDP" (0x0001)
Profile Descriptor List:
  "SDP Server" (0x1000)
    Version: 0x0100

Service Name: Dial-up Networking Gateway
Service Description: Dial-up Networking Gateway
Service Provider: Motorola
Service RecHandle: 0x10001
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Sprache Gateway
Service Description: Headset Audio Gateway
Service Provider: Motorola
Service RecHandle: 0x10003
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Freisprechen über Bluetooth
Service Description: Freisprechen über Bluetooth
Service Provider: Motorola
Service RecHandle: 0x10007
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0101

Service Name: OBEX Objekt senden
Service Description: OBEX Objekt senden
Service Provider: Motorola
Service RecHandle: 0x10008
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: OBEX File Transfer
Service Description: OBEX File Transfer
Service Provider: Motorola
Service RecHandle: 0x10009
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Bild-Push
Service Description: Bild-Push
Service Provider: Motorola
Service RecHandle: 0x1000a
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x6465
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6e6c
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100
4) My /etc/bluetooth/rfcomm.conf file looks like this:

#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
	bind yes;
#
#	# Bluetooth address of the device
	device  00:1A:1B:06:98:1D;
#
#	# RFCOMM channel for the connection
	channel	1; 
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}

I tend to think that it is not complete
5) The /etc/wvdial.conf file has the following contents:


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","safaricom"
Phone = *99***1#
Password =''

Modem Type = USB Modem
Stupid mode = on
Baud = 460800
New PPPD = yes
Modem = /dev/rfcomm0
ISDN = 0
Username = saf
Carrier check = no

I also think I have something missing in there because when you dial using wvdial it should have an argument but I do not know what it is or how to get it!

6) And I almost forgot, dmesg gives me a screen-full of this:

 4279.920000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.928000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.928000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.928000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.940000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.940000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.940000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.944000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.944000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.944000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 4279.944000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92

Would someone kindly guide me on how to sort this out...

Thanks!

---

### Post by nicedude on 2008-05-17
Hey man here is a link to a thread where they show how to do this in ubuntu. Some of the posts are not in english but the important ones are so look down that page for your answers.

[http://ubuntuforums.org/showthread.php?t=777015](http://ubuntuforums.org/showthread.php?t=777015)

Hope this helps you out, and good luck.

---

### Post by KMuchane on 2008-05-17
Hi,

I am so grateful nicedude, that link did it! Connected on the very first attempt ! Thanks!

---

