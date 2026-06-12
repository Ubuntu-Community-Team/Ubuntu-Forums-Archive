---
title: "[SOLVED] SE K750i gprs connection."
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by richlyn9 on 2008-06-28
Hi!
i am trying to connect SE K750i phone using airtel gprs via the usb cable(though havent come across  anyone with the same exact instance),Have tried all resources on the forums.

I opened Terminal and typed *sudo wvdialconfig *
which returns *command not found*

pls advice future action plan.

---

### Post by prshah on 2008-06-28
> **richlyn9 said:**
> *sudo wvdialconfig *


You're looking for ```
sudo wvdialconf
```

---

### Post by richlyn9 on 2008-06-28
richlyn@richlyn-personal:~$ sudo wvdialconf 
[sudo] password for richlyn: 
Editing `/etc/wvdial.conf'. 

Scanning your serial ports for a modem. 

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud 
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud 
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port. 
ttyACM0<*1>: ATQ0 V1 E1 -- OK 
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK 
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK 
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK 
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyACM0<*1>: Modem Identifier: ATI -- Sony Ericsson K750 
ttyACM0<*1>: Speed 4800: AT -- OK 
ttyACM0<*1>: Speed 9600: AT -- OK 
ttyACM0<*1>: Speed 19200: AT -- OK 
ttyACM0<*1>: Speed 38400: AT -- OK 
ttyACM0<*1>: Speed 57600: AT -- OK 
ttyACM0<*1>: Speed 115200: AT -- OK 
ttyACM0<*1>: Speed 230400: AT -- OK 
ttyACM0<*1>: Speed 460800: AT -- OK 
ttyACM0<*1>: Max speed is 460800; that should be safe. 
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
WvModem<*1>: Cannot get information for serial port. 
ttyACM1<*1>: ATQ0 V1 E1 -- OK 
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK 
ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK 
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK 
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyACM1<*1>: Modem Identifier: ATI -- Sony Ericsson K750 
ttyACM1<*1>: Speed 4800: AT -- OK 
ttyACM1<*1>: Speed 9600: AT -- OK 
ttyACM1<*1>: Speed 19200: AT -- OK 
ttyACM1<*1>: Speed 38400: AT -- OK 
ttyACM1<*1>: Speed 57600: AT -- OK 
ttyACM1<*1>: Speed 115200: AT -- OK 
ttyACM1<*1>: Speed 230400: AT -- OK 
ttyACM1<*1>: Speed 460800: AT -- OK 
ttyACM1<*1>: Max speed is 460800; that should be safe. 
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 

Found an USB modem on /dev/ttyACM0. 
Modem configuration written to /etc/wvdial.conf. 
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" 
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" 
richlyn@richlyn-personal:~$ 
richlyn@richlyn-personal:~$ 
richlyn@richlyn-personal:~$ 




Then I edited the wvdial.conf and saved it

richlyn@richlyn-personal:~$ sudo gedit /etc/wvdial.conf 
[sudo] password for richlyn: 
richlyn@richlyn-personal:~$ wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT*99# 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATDT*99# 
WvDial Modem<*1>: CONNECT 
WvDial Modem<*1>: ~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&[1f]R.hx5~ 
WvDial<*1>: Carrier detected.  Waiting for prompt. 
WvDial Modem<*1>: ~[7f]}#@!}!}"} }8}#}$@#}(}"}'}"}"}&} } } } }%}&[1f]R.h2'~ 
WvDial<*1>: PPP negotiation detected. 
WvDial<Notice>: Starting pppd at Sat Jun 28 17:19:40 2008 
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied 
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky. 
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied 
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky. 
WvDial<Notice>: Pid of pppd: 5815 
WvDial<*1>: Using interface ppp0 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: local  IP address 117.98.36.156 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: remote IP address 10.64.64.64 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: primary   DNS address 202.56.230.5 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: secondary DNS address 202.56.240.5 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
Caught signal 2:  Attempting to exit gracefully... 
WvDial<*1>: Terminating on signal 15 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: Connect time 1.5 minutes. 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08] 
WvDial<*1>: Disconnecting at Sat Jun 28 17:21:08 2008 
richlyn@richlyn-personal:~$ 


ithis has get resolved,,..........
i am now working fine in ubuntu....
and writing this in firefox...

---

### Post by prshah on 2008-06-28
> **richlyn9 said:**
> r
ithis has get resolved,,..........
i am now working fine in ubuntu....
and writing this in firefox...

Do you mean that this issue is solved (looks like it). In that case, please mark the thread solved:
click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

