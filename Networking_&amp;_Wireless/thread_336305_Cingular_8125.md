---
title: "Cingular 8125"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by echosyp on 2007-01-11
These are the steps I used on Edgy to use my Cingular (HTC) 8125 Dial-up networking using bluetooth.  

FIrst off you need to have bluetooth and BlueZ.

# hcitool scan
Scanning ...
        FF:FF:FF:FF:FF:FF       Cingular 8125

Now use the mac address of the device with sdptool to show services
(I used "sdptool records" because "sdptool browse" didn't return anything)

$ sdptool records macAddressOfDevice 
...
Service Name: Dial-up Networking
Service RecHandle: 0x10005
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

You are looking for the part that says  "Channel: 4" 

Now you will edit rfcomm.conf to create a connection interface.

 $ sudo gedit /etc/bluetooth/rfcomm.conf

rfcomm0 {
#	# Automatically bind the device at startup
#	bind yes;
#
#	# Bluetooth address of the device
	device FF:FF:FF:FF:FF:FF;
#
#	# RFCOMM channel for the connection
	channel	4;
#
#	# Description of the connection
	comment 'BT DUN';
#
}

Now you should be able to connect to the phone using:
(When you connect to the phone be quick entering the PIN or it won't connect.  I found it easier to use the phone to establish a partnership before running the following command.)

$ rfcomm connect 0

If all goes well you should see the following:

Connected /dev/rfcomm0 to FF:FF:FF:FF:FF:FF on channel 4

Now that there is a connection I used kppp to create a new modem:
[http://ubuntuforums.org/attachment.php?attachmentid=22756&stc=1&d=1168540283](http://ubuntuforums.org/attachment.php?attachmentid=22756&stc=1&d=1168540283)
Then use KPPP to create an accnt
[http://ubuntuforums.org/attachment.php?attachmentid=22757&stc=1&d=1168540283](http://ubuntuforums.org/attachment.php?attachmentid=22757&stc=1&d=1168540283)

The login information for cingular is:
username: [email]wap@cingular.net[/email]
password: cingular1

Now hit connect and rfcomm0 should be connected. You can verify by using ifconfig.

Hope this helps. If anyone has had success using this phone in linux another way please post.

---

### Post by D_invictus on 2008-01-05
How do I tether my 8125 via usb? my laptop doesn't have bluetooth.

---

### Post by setdosa on 2008-01-14
That was a great post. Thanks a lot for that. I am able to succesfully connect, but why am i not able to go online. I have gotten an IP address and everything. Any ideas?

---

### Post by setdosa on 2008-01-14
You know, i disconnected and connected again and it worked. This time though, I disabled networking in the networkmanager before I connected to the phone. Again, thanks a lot ecosyp. You made my day

---

