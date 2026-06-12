---
title: "Wvdial USB Modem Issue (Sony Ericsson K850i AT&amp;T 3G)"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by amd is the best on 2008-03-25
Hello Everyone,

I am using my cell phone (Sony Ericsson K850i) as a modem using AT&T's wireless network.  I had everything working properly last week using wvdialconf to setup the modem and wvdial using these settings:


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = CINGULAR1
Username = [email]wap@cingulargprs.com[/email]

Output of wvdialconf:

nick@AMDTL60:/etc$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Sony Ericsson K850
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
ttyACM1<*1>: Modem Identifier: ATI -- Sony Ericsson K850
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


This past weekend, I ended up having to reformat the hard drive on my laptop and now for whatever reason it is not working properly.  It will connect and assign an IP just as it would before without an issue.  I can browse the web and talk on an instant messenger without an issue.  The issue comes when trying to transfer a larger file (seems to be 300k or larger).  Like I said, this was not a problem before using the same settings.  I also know that it does transfer larger files when using it in windows (so that eliminates any potential issues with AT&T themselves).

This is the output when I connect:

nick@AMDTL60:/etc$ sudo wvdial
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
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: ~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&:[16]Q}?Fx~
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&:[16]Q}?}*}5~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue Mar 25 04:20:35 2008
WvDial<Notice>: Pid of pppd: 10789
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 10.155.109.116
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 66.209.10.201
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 66.102.163.231
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]


Any help or info would be greatly appreciated!!!

Thanks in advance,
Nick

---

### Post by amd is the best on 2008-03-26
Anyone have any input?  I may just try and reformat again and see if it works properly then.

Does this line look incorrect: "WvModem<*1>: Cannot get information for serial port."

---

### Post by amd is the best on 2008-03-28
SOL I suppose?

---

### Post by hunter_te on 2008-04-01
I am currenty connected with a K750i phone

Here is wvdial file

The phone number was told to me by service provider.

```

[Dialer Defaults]

Modem = /dev/ttyACM0

**Phone = *99***4*1#  **

Username = abc

Password = xyz

Baud = 460800

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

ISDN = 0

Modem Type = Analog Modem

Carrier Check = No

```


Here is what i can see in the opened termial, u gotta keep the terminal open until u want to disconnect..

```

XYZ@The-C2D-Machine:~$ wvdial
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
WvDial<*1>: Sending: ATDT*99***4*1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***4*1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3cD7~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3c[08]Z~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue Apr  1 08:53:24 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 6225
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 117.98.65.11
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 202.56.230.5
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 202.56.240.5
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]


```

There has been no help, so i thought i should post my settings here, maybe could help.

Here is the guide to setup from scratch  [http://ubuntuforums.org/showpost.php?p=4568287&postcount=5](http://ubuntuforums.org/showpost.php?p=4568287&postcount=5)


EDIT::

Hey man i just remember now. 
i dont have to do anything when i connect my k790i model. And urs is a more latest one.

When i connect my k790, it asks if i want to run it in file transfer mode or phone mode. I just select phone mode. And i have also done some edit in phone menu. Like connect to internet whenever the USB cable is connected. and make sure for all types of connections u have selected a working profile in the phone menu. 

I hope it works.

Good luck

---

### Post by vladimirck on 2008-04-29
Hi, I got the very same problem. I've been trying the fix that problem, with no success. I was thinking that it was something to do with flow control, but now that you mentioned, it was working just fine before, because I could update my system with no issues. However, I didn't reformat my hd, it just happened. I even made a clean install in linux to avoid this problem, but it still persist.

I was wondering if the problem could be with pppd, but I have no solution yet. Please, let me know if you already solved the issue. Thank you.

---

### Post by KemexMiraz on 2008-04-29
> **hunter_te said:**
> I am currenty connected with a K750i phone

Here is wvdial file

The phone number was told to me by service provider.

```

[Dialer Defaults]

Modem = /dev/ttyACM0

**Phone = *99***4*1#  **

Username = abc

Password = xyz

Baud = 460800

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

ISDN = 0

Modem Type = Analog Modem

Carrier Check = No

```


Here is what i can see in the opened termial, u gotta keep the terminal open until u want to disconnect..

```

XYZ@The-C2D-Machine:~$ wvdial
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
WvDial<*1>: Sending: ATDT*99***4*1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***4*1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3cD7~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3c[08]Z~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue Apr  1 08:53:24 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 6225
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 117.98.65.11
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 202.56.230.5
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 202.56.240.5
WvDial<*1>: pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]


```

There has been no help, so i thought i should post my settings here, maybe could help.

Here is the guide to setup from scratch  [http://ubuntuforums.org/showpost.php?p=4568287&postcount=5](http://ubuntuforums.org/showpost.php?p=4568287&postcount=5)


EDIT::

Hey man i just remember now. 
i dont have to do anything when i connect my k790i model. And urs is a more latest one.

When i connect my k790, it asks if i want to run it in file transfer mode or phone mode. I just select phone mode. And i have also done some edit in phone menu. Like connect to internet whenever the USB cable is connected. and make sure for all types of connections u have selected a working profile in the phone menu. 

I hope it works.

Good luck

I Have the same problem, but im using an Franklin EVDO USB Card, it connected to the provider, but when i try to load a page, i just doesnt load!. (Firefox RSS feeds are updated in the process). Ping works resolving the IP Address, but the result is 100% of Packages sent where lost.

---

### Post by h4mx0r on 2008-05-22
You don't have to keep the terminal open until you want to disconnect use it like "wvdial &" that should fix it or start it in its own tty by pressing ctrl alt f2 and starting it there then going ctrl alt f7 to get back to desktop.

---

