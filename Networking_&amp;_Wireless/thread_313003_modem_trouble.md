---
title: "modem trouble"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2006-12-05
OK I don't know if anyone can help on this but here it is.  I connect to the internet with wvdial and it is working ok but the read out when I connect is this.

ronbrooks@prodigy:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT5248571
--> Waiting for carrier.
ATDT5248571
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec  5 10:55:01 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5575
--> Using interface ppp0
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> local  IP address 4.252.39.110
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> remote IP address 209.247.21.109
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> primary   DNS address 209.244.0.3
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]
--> secondary DNS address 209.244.0.4
--> pppd: &#65533;[08][06][08]&#65533;[11][06][08]

I don't know why permission is denied.  Dose anyone know how to fix this.

---

### Post by IMELucky on 2006-12-05
Try prefixing wvdial with the command "sudo"

in other words:

sudo wvdail

It will ask you for your password.


There are also a lot of graphical frotends to dail-up in synaptic (KPPP for example)

Good Luck

---

### Post by daniminas on 2006-12-05
maybe your *.conf file.. or do: 
```
sudo wvdial
```

---

### Post by ronbrooks on 2006-12-05
Thank You It worked and I am going to down load kppp and see how that works.

---

