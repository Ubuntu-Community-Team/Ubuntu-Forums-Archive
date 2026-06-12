---
title: "Strange output from wvdial?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by Knosse on 2006-12-22
Hi all !
What is the "--> pppd: &#65533; [06][08][10][0b][06][08]" lines? How can i get rid of thees lines?


--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: at+cgdcont=1,"IP","online.telia.se"
at+cgdcont=1,"IP","online.telia.se"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 1800000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec 23 00:41:41 2006
--> Pid of pppd: 5107
--> Using interface ppp0
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> local  IP address 10.177.29.88
--> pppd: &#65533; [06][08][10][0b][06][08]
--> remote IP address 212.181.254.226
--> pppd: &#65533; [06][08][10][0b][06][08]
--> primary   DNS address 10.11.12.13
--> pppd: &#65533; [06][08][10][0b][06][08]
--> secondary DNS address 10.11.12.14
--> pppd: &#65533; [06][08][10][0b][06][08]
--> Connect time 0.1 minutes.
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> local  IP address 10.177.29.88
--> pppd: &#65533; [06][08][10][0b][06][08]
--> remote IP address 212.181.254.226
--> pppd: &#65533; [06][08][10][0b][06][08]
--> primary   DNS address 10.0.0.1
--> pppd: &#65533; [06][08][10][0b][06][08]
--> secondary DNS address 10.0.0.2
--> pppd: &#65533; [06][08][10][0b][06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533; [06][08][10][0b][06][08]
--> Connect time 0.4 minutes.
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> pppd: &#65533; [06][08][10][0b][06][08]
--> Disconnecting at Sat Dec 23 00:42:15 2006

/
Patrik

---

### Post by highvoltage on 2008-07-17
I'd love to know as well. Previous versions of wvdial didn't do this.

---

