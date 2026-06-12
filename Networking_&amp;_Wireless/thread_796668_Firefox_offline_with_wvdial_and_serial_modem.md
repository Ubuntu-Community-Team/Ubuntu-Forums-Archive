---
title: "Firefox offline with wvdial and serial modem"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by danzac64 on 2008-05-16
Dear Ubunters,
I'm trying to connect to internet with an old-fashion serial modem and wvdial. I'm using Ubuntu 8.04 (as a beginner...). I successfully installed the modem with wvdialconf and I completed the wvdial.conf. When I launch wvdial I get connection, I receive the IP and DNS but Firefox stays offline.
Here's the output of the conf and wvdial (I tryed 'sudo wvdial' as well and I could overcome the pap/chap secret problem, but firefox remains offline). Any hint? Cheers
*****************************************************
daniele@daniele-ubuntu:/etc$ cat wvdial.conf
*****************************************************
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 7023456789
Modem = /dev/ttyS0
Username = myname
Password = mypassword
Baud = 115200

*****************************************************
daniele@daniele-ubuntu:/etc$ wvdial
*****************************************************
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT7023456789
--> Waiting for carrier.
ATDT7023456789
CONNECT 50666 V42bis
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri May 16 22:32:35 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6453
--> Using interface ppp0
--> pppd: [1f][7f]
--> pppd: [1f][7f]
--> pppd: [1f][7f]
--> pppd: [1f][7f]
--> pppd: [1f][7f]
--> local  IP address 62.11.231.193
--> pppd: [1f][7f]
--> remote IP address 213.205.24.21
--> pppd: [1f][7f]
--> primary   DNS address 213.205.32.70
--> pppd: [1f][7f]
--> secondary DNS address 213.205.36.70
--> pppd: [1f][7f]

---

### Post by danzac64 on 2008-05-17
No hint? Setting the serial modem from the Ubuntu GUI doesn't work either.

---

### Post by danzac64 on 2008-05-17
Solved...

---

### Post by naga.setiawan on 2008-11-17
i came up with the exact same problem as you do. would you kindly explain how you solved the problem? thank you for the help :)

---

