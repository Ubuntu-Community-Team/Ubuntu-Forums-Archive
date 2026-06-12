---
title: "Automatically geting static-routes through dchp problem"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by mdgap on 2007-10-14
Ubuntu 7.04.

I use VPN to connect to the internet and my ISP provides some static-routes through dchp (to ensure that local resources traffic won't go through VPN).

So I use network-manager and network-manager-pptp to establish VPN connection. Everything is alright in here.

Then I addded "static-routes" to "request" option in /etc/dhcp3/dhclient.conf and put a script in dhclient-exit-hooks.d to actually add thouse routes.

So when i manually "sudo dhclient" it gets and adds thouse routes okay.

But how do a I make dhclient to make it automatically??

I don't wanna "sudo dhclient" on every log on and every now and than (in case some of those routes will be changed or something).

What did I miss? Doesn network-manager actually use dhclient at all or get dhcp ip and all somehow by himself?

Thanks!

(Sorry for my english and possibly stupid questions, i'm not much of a pro in network technologies nor linux.)

---

