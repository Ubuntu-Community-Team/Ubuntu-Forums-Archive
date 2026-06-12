---
title: "Can not log into BT GPS device..."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by electronbee on 2009-06-13
It's a Holux M-1000 and when I try to telnet in I get this:

> telnet localhost 2947
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

sdptool gives me:

> sdptool browse 00:1B:C1:00:F8:7D
Browsing 00:1B:C1:00:F8:7D ...
Service Name: SPP slave
Service RecHandle: 0x10000
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100


I am totally clueless. Any ways, I am running 9.04, a Zoom USB Bluetooth adapter model 4322, and a Holux M-1000 GPS.

---

### Post by gsocker on 2009-06-13
The protocol description list contains "RFCOMM (0x0003)". This means the GPS appears as a "virtual" serial port. Telnet doesn't have anything to do with it - BTW "localhost" always refers to the machine you ran the command on.
You will need to bind the device to a port,
then use a terminal program such as minicom.
There are other ways if all you want to do is display the GPS output.
Binding  is done via the "rfcomm" command.
Example:
```
rfcomm bind 0 <00:00:00:00:00> 5
```
In your case,
```
rfcomm bind 0 00:1B:C1:00:F8:7D
```
"Channel" can be left out in this case since it defaults to 1 and that is what your GPS uses.
You will probably get a request for the PIN(probably 0000).
This should create /dev/rfcomm0 or possibly /dev/bluetooth/rfcomm0. 
You can then use minicom to view the data.
```
cat /dev/name/here 
``` will probably also work, since if I remember correctly the BT serial code ignores port speed and other stuff.
The "rfcomm" command will need to be run via sudo. 
Viewing the data may also require sudo depending on permissions.
If any of this doesn't work, please post any error messages you receive, along with the command line that caused them.
There is probably a way to do this via a GUI, but I run KDE on Gentoo so someone else will have to explain that :-)

---

### Post by Hobgoblin on 2009-06-14
Do you have [gpsd](http://gpsd.berlios.de/gpsd.html) installed/configured?

---

### Post by electronbee on 2009-06-14
Yup, I did bind the rfcomm and I do have GPSD installed and configured. I forgot to include the two links that I went to first:

[http://ubuntuforums.org/archive/index.php/t-200142.html](http://ubuntuforums.org/archive/index.php/t-200142.html)
[http://gpsd.berlios.de/bt.html](http://gpsd.berlios.de/bt.html)

Here is my hcid.conf:
> #
# HCI daemon configuration file.
#

# HCId options
options {
# Automatically initialize new devices
autoinit yes;

# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security user;

# Pairing mode
# none - Pairing disabled
# multi - Allow pairing with already paired devices
# once - Pair once and deny successive attempts
pairing multi;

# PIN helper
pin_helper /usr/bin/bluepin;

# D-Bus PIN helper
#dbus_pin_helper;
}

# Default settings for HCI devices
device {
# Local device name
# %d - device id
# %h - host name
name "mobile";

# Local device class
class 0x3e0100;

# Default packet type
#pkt_type DH1,DM1,HV1;

# Inquiry and Page scan
iscan enable; pscan enable;

# Default link mode
# none - no specific policy
# accept - always accept incoming connections
# master - become master on incoming connections,
# deny role switch on outgoing connections
lm accept;

# Default link policy
# none - no specific policy
# rswitch - allow role switch
# hold - allow hold mode
# sniff - allow sniff mode
# park - allow park mode
lp rswitch,hold,sniff,park;

# Authentication and Encryption (Security Mode 3)
#auth enable;
#encrypt enable;
}


Here is my rfcomm:
> #
# RFCOMM configuration file.
#

rfcomm0 {
	# Automatically bind the device at startup
	bind yes;

	# Bluetooth address of the device
	
device 00:1B:C1:00:F8:7D;

	# RFCOMM channel for the connection
	channel	1;

	# Description of the connection
	comment "HOLUX M-1000 GPS";
}

I may have looked at two different things from two different times and gotten some confusion in there. However, the device is configured to be rfcomm0 through and through.

eb

---

### Post by gsocker on 2009-06-14
You did start GPSD, right?
Try running ```
/etc/init.d/gpsd start
```
Since it's an "optional" service it will not be started by default.

---

### Post by electronbee on 2009-06-14
I believe I did start it but I ran it anyway and this is what I got:

> 
/etc/init.d/gpsd start
 * Not starting GPS (Global Positioning System) daemon gpsd              [ OK ] 
~$ /etc/init.d/gpsd stop
 * Not stopping GPS (Global Positioning System) daemon gpsd              [ OK ] 


I also ran it as sudo and same response.

eb

---

### Post by gsocker on 2009-06-15
FYI, when starting system services (anything that has a script in /etc/init.d fits), you will always need to be root(via sudo or other methods). 
Check /var/log/messages for any errors.
Also try running, via sudo, ```
gpsd -N -D2
```.
This will send debugging info to the screen; you can see if it works this way. If so, then the next problem is to figure out why the init script isn't working correctly.

---

