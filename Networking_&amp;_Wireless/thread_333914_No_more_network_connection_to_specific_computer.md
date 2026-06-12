---
title: "No more network connection to specific computer"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by Striatum on 2007-01-08
Hi all,

I have a notebook with Ubuntu 6.10 in my local lan connected via wlan to my router. The ip is 192.168.178.25.
Another notebook in my lan has Windows XP loaded and is also connected via wlan to my router, the IP is 192.168.178.27, a third PC (also wlan) is 192.168.178.20.

Since last week - without changing anything - I cannot connect from 192.168.178.25 to 192.168.178.27 any more - no ping, no VNC, no Samba. The other direction doesn't work either. I can, however, connect from 192.168.178.25 to 192.168.178.20 without problems. The internet connection also works fine from all hosts.
iptables -L shows not entry, /etc/hosts.deny is empty.
As said, I didn't change anything. Windows firewall is disabled on 192.168.178.27 and not other firewall is installed.
Anyone got an idea?

Thanks!
Dominik

---

### Post by hal10000 on 2007-01-08
Can you ping from 192.168.178.20 to 192.168.178.27?
If not, then your network card may be damaged.

You may install the traceroute package and try [COLOR="Red"]traceroute 192.168.178.27[/COLOR] from your ubuntu system to your window pc.

From windows you may use the tracert command (from the command line): [COLOR="Red"]tracert 192.168.178.25[/COLOR] and [COLOR="Red"]tracert 192.168.178.20[/COLOR] to check the routing steps.

---

### Post by Striatum on 2007-01-08
Ping from 192.168.178.20 <-> 192.168.178.27 works in both directions,
Ping from 192.168.178.20 <-> 192.168.178.25 works in both directions,
Ping from 192.168.178.25 <-> 192.168.178.27 works in no direction

Traceroute shows just one step in both directions as all hosts are just connected to the same wlan router.

I seems like Ubuntu blocks all connections to that IP for an unknown reason...

---

### Post by hal10000 on 2007-01-08
So it's not a damaged network card. Have you made any settings in your router?
Delete all settings in your firewall:
```

sudo iptables -F
sudo iptables -P input ACCEPT
sudo iptables -P forward ACCEPT
sudo iptables -P output ACCEPT

```
just to be sure it's not a firewall problem

---

