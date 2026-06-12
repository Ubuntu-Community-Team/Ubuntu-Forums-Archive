---
title: "Need help with ppp- pap/chap files permissions"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by randiroo76073 on 2007-04-18
Running Ubuntu 6.06 Dapper, just added my wife as a user on my puter but can't get her account online using gppp. Keep getting error msg as follows, no matter what I set file permissions at, even setting them at "rwxrwxrwx".

--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT18177259412
--> Waiting for carrier.
ATM0L0DT18177259412
CONNECT 42666 V44
--> Carrier detected. Waiting for prompt.
GlobalPOPS
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: my name
Password:
--> Looks like a password prompt.
--> Sending: (password)
Entering PPP Session.
IP address is 72.251.11.52
MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Sun Apr 15 09:13:16 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8220
--> Disconnecting at Sun Apr 15 09:13:16 2007
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

Can someone help me out of this quandry please?

---

