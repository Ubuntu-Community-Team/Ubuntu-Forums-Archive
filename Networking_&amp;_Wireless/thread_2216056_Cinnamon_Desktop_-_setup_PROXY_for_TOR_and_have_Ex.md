---
title: "Cinnamon Desktop - setup PROXY for TOR and have Exception for LAN"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2014-04-09
hello,


i have the following setup on my laptop.

i have installed TOR is running as a daemon at start up.

and i have setup Cinnamon/gnome3 to have a PROXY pointing to TOR port (9050)
***preferences > network > network proxy***

so for SOCKS (v5?) i have entered in Cinnamon:

```

socks host = 127.0.0.1
port = 9050

```

however, i think i have found that my local traffic is also redirected through the proxy as it is failing...

so i would like to find out how i can add an exception list to the proxy?

there is an entry for a configuration file, but i am *not* aware of its format.
any suggestions on how this can be done?


thanks,

---

