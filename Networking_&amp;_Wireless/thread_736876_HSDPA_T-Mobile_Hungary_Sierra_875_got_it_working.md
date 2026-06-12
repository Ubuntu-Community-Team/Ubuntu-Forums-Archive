---
title: "HSDPA T-Mobile Hungary Sierra 875 got it working"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by bean1975 on 2008-03-27
I got a Sierra 875 working with T-Mobile Hungary. This is not easy because T-mobile Hungary requires no username and password and I could not get wvdial to not require a password, no matter what I set username to in wvdial.conf. Here are my configuration files:

/etc/ppp/peers/hsdpa

```

hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/hsdpa"
debug
/dev/ttyUSB0
921600
defaultroute
noipdefault
remotename hsdpa
ipparam hsdpa

usepeerdns
noauth

```

/etc/chatscripts/hsdpa

```

ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
'' ATZ OK 'ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0' OK 'AT+CGDCONT=1,"IP","internet"
OK-AT-OK "ATDT*99#"
CONNECT

'' \d\c

```

and then sudo pon hsdpa makes it happen.

Edit: I suspect this is the same for every T-Mobile out there.

---

### Post by bean1975 on 2008-04-12
Note that in later usage I found that stopping existing dhclient processes and/or killing avahi is necessary. Not sure which of the two helped.

---

