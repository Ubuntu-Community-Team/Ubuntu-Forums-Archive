---
title: "PPP ignores persist"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by Beatinu on 2006-09-28
Hi,

on my Ubuntu box I have an DSL Internet connection. The /etc/ppp/peers configuration was created by pppoeconf and it contains

```

persist

```

I want this connection to be up 24/7. From time to time (about once every month) there's a connection problem and pppd just gives up. This is what I get:

```

pppd[26081]: Modem hangup
pppd[26081]: Connect time 765.4 minutes.
pppd[26081]: Sent 118144429 bytes, received 108371123 bytes.
pppd[26081]: Connection terminated.
pppd[26081]: Terminating on signal 15
pppd[26081]: Exit.

```

I've tried a lot and also played with maxfail, but pppd doesn't reconnect. On my Debian sarge box the same peers and option files work fine.

There are some solutions with reconnect scripts which check the Internet connection from time to time but I'd like to get pppd working the way it should.

Thanks for any help!

---

### Post by atmurray on 2007-01-05
I've detailed how to fix the bug where ppp connections are not persistent due to a bug in udev here:

[http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html]("http://rants.atmurray.net/2007/01/pppd-persist-not-so-persist-with-udev.html")

I hope this kills this problem once and for all and we see see this bug squashed in an update soon.

---

