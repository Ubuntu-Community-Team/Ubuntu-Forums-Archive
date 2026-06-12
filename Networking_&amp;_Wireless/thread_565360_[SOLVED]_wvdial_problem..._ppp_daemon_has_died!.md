---
title: "[SOLVED] wvdial problem... ppp daemon has died!"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by hyacinth on 2007-10-02
hi,

I have successfully installed and configured a driver for my Conexant modem,
but some error occurred while using the "wvdial" command...
here's what I get:
```

**XXX@XXX-laptop:~$ sudo wvdial**
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT195
--> Waiting for carrier.
ATDT195
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
ascend% 
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend% 
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend% 
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend% 
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend% 
--> Hmm... a prompt.  Sending "ppp".
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue Oct  2 12:59:50 2007
--> Pid of pppd: 5809
--> Using interface ppp0
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> pppd: &#65533;[06][06][08]P[11][06][08]
--> Disconnecting at Tue Oct  2 13:00:21 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
```


and here is the **/etc/wvdial.conf**:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 195
Modem = /dev/modem
Username = XXX
Carrier Check = no
Password = XXX
Baud = 460800
```

I have no clue what's wrong...so, any help will be appreciated!

---

### Post by tiwag on 2007-10-03
have the same problem with my Conexant D110 hsf-modem on Ubuntu 7.04
using the Dell-Support driver (hsfmodem_7.60.00.06oem_i386.deb from Linuxant)

it seems no one has found the source of the problem till now 
and therefore no solution till now ... sorry

---

### Post by hyacinth on 2007-10-04
Adding these two lines to **/etc/wvdial.conf** seemed to solve the problem...

```

Stupid Mode = yes
Auto DNS = yes

```

---

### Post by tiwag on 2007-10-13
> **hyacinth said:**
> Adding these two lines to **/etc/wvdial.conf** seemed to solve the problem...

```

Stupid Mode = yes
Auto DNS = yes

```


thanks for your hint, but this did'nt solve my problem,

after studying the syslog messages, i found out after a while, 
that my lost connection was caused by a pppd "Lost compression sync" error

from the **syslog**
> 
Oct 13 09:27:54 DB pppd[6329]: Lost compression sync: disabling compression
Oct 13 09:27:54 DB pppd[6329]: sent [CCP TermReq id=0x2"Lost compression sync"]
Oct 13 09:27:54 DB pppd[6329]: rcvd [Compressed data] 00 15 c4 56 5d 4f c2 30 ...
Oct 13 09:27:55 DB pppd[6329]: rcvd [CCP TermAck id=0x2]
Oct 13 09:27:56 DB pppd[6329]: Modem hangup



the solution for this problem, was to disable deflate compression in pppd options

by adding the line 
```
nodeflate
```
to the file **/etc/ppp/options**

brgds

---

