---
title: "Bt_port"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by psykotrol on 2008-06-30
Alright, so after seeing that I could fix my comcast seeding problems with torrents, I stupidly typed in my terminal

```
BT_PORT=
```

with no ports, to see what options it might give me, it gave me none, and then proceeded to type in the corresponding ports.

```
BT_PORT=57436
```

or whatever other ports I was using. I immediately noticed that I could upload just fine, but could not download anything. Im using deluge, so I tested the ports and every single one I use is closed. saying TCP port 57436 closed on 98.210.***.**

so, is there any way to reverse this? or if not, how to get my downloads working again?

edit: also, heres the code used to work around the comcast throttling

```
#!/bin/sh
#Replace 6883 with you BT port
BT_PORT=6883

#Flush the filters
iptables -F

#Apply new filters
iptables -A INPUT -i lo -j ACCEPT
#Comcast BitTorrent seeding block workaround
iptables -A INPUT -p tcp -dport $BT_PORT -tcp-flags RST RST -j DROP
iptables -A INPUT -m state -state ESTABLISHED,RELATED -j ACCEPT
#BitTorrent
iptables -A INPUT -m state -state NEW -m tcp -p tcp -dport $BT_PORT -j ACCEPT
iptables -A INPUT -m state -state NEW -m udp -p udp -dport $BT_PORT -j ACCEPT
iptables -A INPUT -j REJECT -reject-with icmp-host-prohibited
```

whenever I get to 

```
iptables -A INPUT -p tcp -dport $BT_PORT -tcp-flags RST RST -j DROP
```

it says 

```
Bad argument 'RST'
```

I tried googling it, but came up with nothing.

---

