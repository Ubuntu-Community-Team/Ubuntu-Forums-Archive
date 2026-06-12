---
title: "Problem in modem"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Vampiree on 2009-01-21
Hello.I installed Ubuntu 8.10.I downloaded new modem driver for it & I install it & set Username & password for it but when I want to connect to the Internet it want username.How do I can?

> behzad@Dand:~$ wvdial

--> WvDial: Internet dialer version 1.60

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Modem initialized.

--> Sending: ATDT9713637

--> Waiting for carrier.
ATDT9713637
CONNECT 50666

--> Carrier detected.  Starting PPP immediately.

--> Unable to run /usr/sbin/pppd.

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

User Access Verification
Username:

---

### Post by Michael.Godawski on 2009-01-21
hi,

can you please post the output of these terminal commands?

```
sudo lshw -C network
lspci
```

---

### Post by ieee488 on 2009-01-21
You need to run *wvdial* with sudo

---

### Post by Vampiree on 2009-01-21
This is what do yo want.

---

