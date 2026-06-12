---
title: "Turn a proxy connection into a direct connection"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Ububurns on 2007-02-22
I can access the internet at full speed using 192.168.1.254:2728 as a proxy.

Is there any way I can route (?) this connection so that my computer treats it as a normal connection to the internet?

---

### Post by Dumdideldum on 2007-02-22
that depends on, what protocols the proxy supports.
But you can set using http and ftp over this proxy by:
export http_proxy=192.168.1.254:2728
export ftp_proxy=192.168.1.254:2728

and add this into /etc/init.d/rc.local for instance.

Not sure if there is a config file for proxies though.

---

