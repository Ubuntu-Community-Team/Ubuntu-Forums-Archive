---
title: "PING problems"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by frapic on 2005-05-25
[B]Hi guys,
I have problems pinging hosts by using Bash shell.
(Maybe it's a very little & stuopid thing)

I'm behind an internal http proxy server (192.168.17.3).
If I launch
> ping 127.0.0.1
(my loopback) it works.

If I launch
> ping 192.168.17.15
(my computer) it works.

But if I ping any other ip address it doesn't work.

However, if I use Firefox, with the right proxy settings, everything works fine.
My settings are rceieved by DHCP.

May anyone help me?
I cannot explain why I can browse the whole web via Firefox, but I cannot ping anything via my shell...

Please, help me soon...
Francesco
[/B]

---

### Post by rmjokers on 2005-05-25
It might help if we knew what types of hosts you are trying to ping and what your network connectivity is to those hosts.  Could there be a firewall inbetween that is interfering with the ping packets in route to the destinations or the responses to those packets?

---

