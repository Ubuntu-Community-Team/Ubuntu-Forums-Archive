---
title: "Problem's in connecting my N91 in Ubuntu 8.04LTS"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by mystic1716 on 2008-11-18
Hey guys i have a problem in connecting my Nokia N91 as a USB modem in Ubuntu 8.04LTS 32 bit edition.

I have followed the methods to create the wvdial stuffs and all. I continue from where i got problems.

First i had my values for wvdial as follows
```
[Dialer Defaults]

Init1=ATZ

Init2=ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Modem Type=USB Modem

Baud=460800

New PPPD=Yes

Modem=/dev/ttyACM0

ISDN=0

Phone=*99***1#

Password=A

Username=B

Stupid Mode=yes
```

Then when i tried in terminal typing ```
$ sudo wvdial
```

it gives the following response

```
--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.
--> Sending: ATDT*99***1#

--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Tue Nov 18 17:26:33 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied

--> --> PAP (Password Authentication Protocol) may be flaky.

--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied

--> --> CHAP (Challenge Handshake) may be flaky.

--> Pid of pppd: 5805

--> Using interface ppp0

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> Disconnecting at Tue Nov 18 17:26:38 2008

--> The PPP daemon has died: A modem hung up the phone (exit code = 16)

--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


```

Then i googled it out and in some forum it tells me to try the following command

```
ls -als /etc/ppp/pap-secrets
ls -als /etc/ppp/chap-secrets

```

Which gives me the following result when i tried 

```
ls -als /etc/ppp/pap-secrets

4 -rw-rw-rw- 1 root root 1664 2008-11-18 23:39 /etc/ppp/pap-secrets


ls -als /etc/ppp/chap-secrets

4 -rw------- 1 root root 110 2008-11-18 19:41 /etc/ppp/chap-secrets


```


After i tried this code when i tried to run wvdial it gaves me the following output

```
--> WvDial: Internet dialer version 1.60

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Tue Nov 18 23:43:23 2008

--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied

--> --> CHAP (Challenge Handshake) may be flaky.

--> Pid of pppd: 6092

--> Using interface ppp0

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> pppd: &#65533;&#65533;[06][08]

--> Disconnecting at Tue Nov 18 23:43:28 2008

--> The PPP daemon has died: A modem hung up the phone (exit code = 16)

--> man pppd explains pppd error codes in more detail.

--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.



```

Did i have to do anything else :confused:i saw the pap-secrets error gone this time but what i still have chap-secret problem.:(


I don't have anyother ISP providers here and i just have to go for this mobile GPRS.. Also my carrier is AIRTEL-INDIA and here we don't have username or passwords for GPRS account.


Am new to Ubuntu.. So any expertise can help me out with this one ... Waiting for the replies.. Thanx in advance for all..

---

