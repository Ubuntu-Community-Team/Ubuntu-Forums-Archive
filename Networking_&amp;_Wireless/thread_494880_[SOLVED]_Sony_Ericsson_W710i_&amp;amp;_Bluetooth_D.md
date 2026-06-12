---
title: "[SOLVED] Sony Ericsson W710i &amp;amp; Bluetooth Dialup"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by xluryan on 2007-07-07
Hey Everyone... I've been trying to get my bluetooth dialup working, but am stuck...

Here is what I get:

```

ryan@freedom$ pon BluetoothDialup
AT
OK
AT+CGDCONT=1,"IP","wap.voicestream.com"
OK
ATD*99***1#
CONNECT
Serial connection established.
using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
rcvd [LCP ConfReq id=0x1 <auth chap MD5> <accomp> <pcomp> <asyncmap 0x0> <magic 0x3dd2cd4c>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x920dfb32> <pcomp> <accomp>]
sent [LCP ConfNak id=0x1 <auth pap>]
rcvd [LCP ConfReq id=0x2 <auth chap MD5> <accomp> <pcomp> <asyncmap 0x0> <magic 0x3dd2cd4c>]
sent [LCP ConfNak id=0x2 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x920dfb32> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x3 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0x3dd2cd4c>]
sent [LCP ConfAck id=0x3 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0x3dd2cd4c>]
sent [LCP EchoReq id=0x0 magic=0x920dfb32]
sent [PAP AuthReq id=0x1 user="freedom" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x3dd2cd4c]
rcvd [PAP AuthAck id=0x1 "Congratulations!"]
Remote message: Congratulations!
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1]
sent [IPCP ConfNak id=0x1 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <addr 10.174.48.194> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.174.48.194> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
rcvd [IPCP ConfReq id=0x2]
sent [IPCP ConfAck id=0x2]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.174.48.194> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
Could not determine remote IP address: defaulting to 10.64.64.64
not replacing existing default route via 192.168.1.1
Cannot determine ethernet address for proxy ARP
local  IP address 10.174.48.194
remote IP address 10.64.64.64
primary   DNS address 66.94.9.120
secondary DNS address 66.94.25.120
Script /etc/ppp/ip-up started (pid 18063)
Script /etc/ppp/ip-up finished (pid 18063), status = 0x0

Terminating on signal 2
Connect time 0.1 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 18078)
sent [LCP TermReq id=0x2 "User request"]
Script /etc/ppp/ip-down finished (pid 18078), status = 0x0
rcvd [LCP TermAck id=0x2]
Connection terminated.

```

What I'm really looking at are the lines:

```

Could not determine remote IP address: defaulting to 10.64.64.64
not replacing existing default route via 192.168.1.1
Cannot determine ethernet address for proxy ARP

```

But I'm not sure if that's what's wrong or not. When the script is done working I am still not able to ping out or get an internet connection. Any ideas?

---

### Post by xluryan on 2007-07-08
SWEETNESS! I got it. And I'm actually posting this with no interfaces plugged in aside from my bluetooth USB dongle :)

Here was the problem (what a fool I am...): I had the wrong service plan with T-Mobile. Apparently you have to have the $29.99 internet plan as opposed to the $5.99 T-MobileWeb plan.

So now that everything works, here are my settings. I am using a Kensington bluetooth USB dongle, and my phone is a Sony Ericsson w710i (very nice phone):

/etc/ppp/peers/BluetoothDialup:
```

debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"
usepeerdns
/dev/rfcomm0 115200
defaultroute
crtscts
lcp-echo-failure 0

modem -detach
noccp
ipcp-accept-remote
ipcp-accept-local
noipdefault
```

/etc/chatscripts/BluetoothDialup:
```

TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=2,"IP","internet2.voicestream.com"'
OK      ATD*99***1#
CONNECT ""
```

There were no settings to change on my phone, I just went into the Bluetooth menu, and made sure the bluetooth internet option was set to "SEMC GPRS".

When I run the command "pon BluetoothDialup", this is what I get:
```

AT
OK
AT+CGDCONT=2,"IP","internet2.voicestream.com"
OK
ATD*99***1#
CONNECT
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x355665ed> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <auth chap MD5> <accomp> <pcomp> <asyncmap 0x0> <magic 0x4fc94908>]
sent [LCP ConfNak id=0x2 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x355665ed> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x3 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0x4fc94908>]
sent [LCP ConfAck id=0x3 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0x4fc94908>]
sent [LCP EchoReq id=0x0 magic=0x355665ed]
sent [PAP AuthReq id=0x1 user="freedom" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x4fc94908]
rcvd [PAP AuthAck id=0x1 "Congratulations!"]
Remote message: Congratulations!
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1]
sent [IPCP ConfNak id=0x1 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <addr 10.172.113.153> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.172.113.153> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
rcvd [IPCP ConfReq id=0x2]
sent [IPCP ConfAck id=0x2]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.172.113.153> <ms-dns1 66.94.9.120> <ms-dns3 66.94.25.120>]
Could not determine remote IP address: defaulting to 10.64.64.64
not replacing existing default route through eth0
Cannot determine ethernet address for proxy ARP
local  IP address 10.172.113.153
remote IP address 10.64.64.64
primary   DNS address 66.94.9.120
secondary DNS address 66.94.25.120
Script /etc/ppp/ip-up started (pid 6407)
Script /etc/ppp/ip-up finished (pid 6407), status = 0x0
```

Now I'm on the net! I get about 30Kb down and 18Kb up. Not too shabby for bluetoothing through a GPRS connection ;)

Hope this helps some people :)

---

