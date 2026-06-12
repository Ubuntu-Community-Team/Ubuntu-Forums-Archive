---
title: "connecing a sony ericsson mobile to get internet"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by hemajith on 2008-08-03
I have asked the same question before regarding connecting a Nokia and I've got a brilliant answer which really worked. Since then I have changed my mobile to a new Sony Ericsson K530i. I tried setting up the connection same way but it does not connect! This is what comes up when I run wvdial,

--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&7!}.p[0e]}3~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Aug  3 20:14:52 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6038
--> Using interface ppp0
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> pppd: h&#65533;[06][08] &#65533;[06][08]
--> Disconnecting at Sun Aug  3 20:14:53 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 40 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

and the on the mobile it says 'connecting' first and then 'connection failure, check settings. If problem consists, contact your operator,  
and wvdial keeps on retrying to establish the connection. Does anybody know how to set this mobile up to get internet?

---

### Post by hemajith on 2008-08-04
ok I worked it out! Sony Ericsson's need a script to get connected to my mobile service provider, even in Windows. So I added the script to my wvdial.conf file as an experiment. This is how it looks like after I add the 'Script',

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = username
Password = password
Script = AT+CGDCONT=1,"IP","www.dialogsl.com",,0,0
Stupid Mode = 1

Just after I insert the line Script, VIOLA! the thing immediately started working!
Hope someone finds this solution helpful!

---

