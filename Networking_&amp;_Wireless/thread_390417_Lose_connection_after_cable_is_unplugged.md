---
title: "Lose connection after cable is unplugged"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by pwnb0t on 2007-03-21
Did some searching and didn't find the answer to this problem.

I installed Ubuntu server 6.10 and then installed xubuntu-desktop

I have two ethernet cards.  The server is acting as a router (no wireless cards or anything) and I'll refer to it as the 'ubuntu router.'

eth0 connects to the Internet while eth1 connects to my internal network and forwards traffic to the Internet.  Everything works but I have a problem which may cause some trouble in the future.

When I unplug the ethernet cable from eth1 and then try to plug it back in (or if I restart the switch that is connected to eth1) then the connection is lost meaning no clients connected in the internal network can talk to the ubuntu router to get to the internet or even receive a dhcp address.

I found that if I can get the network to work by either:
[LIST]
[*]unplugging the switch, then 'ifconfig eth1 down' then plug the switch back in and 'ifconfig eth1 up'
[*]keeping everything plugged in and restarting the ubuntu router
[/LIST]


So I would like it if the connection would fix itself after restarting the switch (breaking the eth1 connection and reconnecting).

Any responses are appreciated!

---

### Post by pwnb0t on 2007-03-22
I've found that if I unplug my statically assigned eth0 (Internet iface) and replug it back in, then the internet connection is still active.

---

### Post by pwnb0t on 2007-03-23
I've also found, that when I run
/etc/init.d/networking restart
that eth1 is not configured (it gives some error at the very end:
"SIOCADDRT:Network is unreachable
Failed to bring up eth1."

So it seems that ubuntu is not handling eth1, is there a way to fix that?

---

