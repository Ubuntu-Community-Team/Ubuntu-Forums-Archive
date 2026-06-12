---
title: "Cannot connect using gnome-ppp"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by agro1986 on 2005-11-06
My uncle has a 56 Kbps modem. I can connect to the internet using System - Administration  - Networking. However it is a bit inconvenient since the user has to enter a password to see the dialog and there is no icon on the notification area for quick disconnect (Windows has it).

I tried installing gnome-ppp (gnome-ppp_0.3.21-1_i386.deb), however it fails to connect with this log:

```

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT21878000
--> Waiting for carrier.
ATM1L1DT21878000
CONNECT 115200
CCC 
CBNnet (cbn.net.id) POP Jatinegara Access Server 
Unauthorized Access Prohibited 
This system is the property of PT Cyberindo Aditama (CBNnet) 
Disconnect IMMEDIATELY if you are not an authorized user ! 
User Access Verification
login:
--> Carrier detected.  Waiting for prompt.
login:
--> Looks like a login prompt.
--> Sending: chrisutomo
chrisutomo
password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed
login:
--> Looks like a login prompt.
--> Sending: chrisutomo
chrisutomo
password:
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Nov  6 18:26:40 2005
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 7717
--> Using interface ppp0
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> Disconnecting at Sun Nov  6 18:26:53 2005
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

```

What bedazzles me is that why does the authetication fail? I use the same port (/dev/ttyS0), phone number, username, and password! Oh, btw before using gnome-ppp I disabled the "Modem Connection"  from the "Networking" dialog (by clicking properties and then unchecking "enable this connection").

Any kind of help is appreciated (if my uncle's satisfied with Ubuntu, he will install it on his office which has around 30 computers :).

Thanks a lot!

---

### Post by bruce147 on 2005-11-06
I don't know about this in any detail, but I saw CHAP and PAP in your modem post and looking in 
wvdial.conf(5) - Linux man page
I see discussion of those parameters

---

