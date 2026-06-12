---
title: "Nokia N82, modem not working via Bluetooth, rfcomm, wvdial,"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Sceiron on 2009-05-27
I can not get my N82 modem working with my laptop. And maybe someone here can help me solve the issue.

I have a thinkpad T61 w/bluetooth. The bluetooth is working, i can browse items on the phone. But when i'm trying to initiate the Dialup connection i get the following:
```

$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/rfcomm0: Host is down


```

when i run "spdtool browse :**:**:**:**:**:**:", i get the following:

```

Service Name: Dial-Up Networking
Service RecHandle: 0x1002b
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

```

```

cat /etc/bluetooth/rfcomm.conf
#
# RFCOMM configuration file.
#

rfcomm0 {
	# Automatically bind the device at startup
	bind yes;

	# Bluetooth address of the device
	device xx:xx:xx:xx:xx:xx;

	# RFCOMM channel for the connection
	channel	4;

	# Description of the connection
	comment "Ubuntu Jaunty";
}

```

```

 cat /etc/wvdial.conf
[Dialer Bluetooth]
Baud = 115200
Modem = /dev/rfcomm0

[Dialer Cable]
Baud = 460800
Modem = /dev/ttyACM0

[Dialer Defaults]
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,”IP”,”telenor"
Modem = /dev/rfcomm0
New PPPD = true
Password = *phone_nr*
Phone = *99#
Username = *phone_nr*

```

MY ISP is Telenor, and I have this working on my laptop provided by my employer, but that is running XP...

I have tried GNOME PPP, but it does not recognise my modem.
As from the command wvdial its reporting that the host is down, is the N82 the host in this case, so it has no contact with the modem at all. How can I test this?

Also, how to test status of rfcomm0 ?

Thanks for any response
Sceiron

---

### Post by Sceiron on 2009-05-29
Bump...

---

### Post by guhpraset on 2009-05-30
have you try to restart the bluetooth?
sudo /etc/init.d/bluetooth restart

then re bind the rfcomm0:
sudo rfcomm unbind 0
sudo rfcomm bind 0

i recently have a success with jaunty bluetooth dialup

---

### Post by Sceiron on 2009-06-01
Hey,

After trying out that, i still can not connect to the phones modem. wvdial still reports "Host is down".
What is the host in this case, it the modem in my phone right??

Anyway, when i just run the command: rfomm
I get the following answer:
xx.xx.xx.xx.xx Channel 4 closed.

This must mean that the program finds the connection, but is not able to use channel 4.
Maybe i need to pair my phone with my laptop in another way??

Thanks for the respons dude!

---

