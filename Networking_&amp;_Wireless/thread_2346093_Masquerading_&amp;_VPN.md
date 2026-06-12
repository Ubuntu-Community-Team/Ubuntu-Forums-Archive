---
title: "Masquerading &amp; VPN"
date: 2016-12-11
forum: Networking &amp; Wireless
---

### Post by damianv2 on 2016-12-11
Hi Everyone,

I am trying to setup my Ubuntu server, which is connected to a VPN server that sits on the internet to "share" this VPN connection with another client that sits on the same LAN as the Ubuntu server.

My setup should work like this:

Client --> Ubuntu (VPN) --> Router --> Internet

So this is what I have done so far:

I have enabled default forwarding policy ```
DEFAULT_FORWARD_POLICY="ACCEPT"
```

Then as a test, I setup to allow other LAN clients to connect through my Ubuntu server.
Modiefied: /etc/ufw/before.rules

```
# nat Table rules*nat
:POSTROUTING ACCEPT [0:0]


# Forward traffic from eth1 through eno1.
-A POSTROUTING -s 192.168.1.0/24 -o eno1 -j MASQUERADE


# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
```

This worked fine, my client, with its gateway set to the Ubuntu server can connect to the internet through the Ubuntu server using it's gateway.

But now, once I connect the VPN on my Ubuntu server "Tun0" I hit a wall and I am not sure how I will allow traffic from my client through the VPN.

Do I add additional firewall rules or routing?

If anyone can point me in the right direction, I would really appreciate it.

Thank you.

PS. Please let me know if my explanation above is not clear enough.

---

### Post by kpatz on 2016-12-11
What's the intention here?  To route all internet bound traffic through the VPN or just traffic to certain IPs or IP ranges?

For all traffic, change your forwarding rule to use tun0 instead of eno1.

For just certain IP ranges, you'll need additional rules.  First rule(s) would forward traffic to the IP range through tun0, and the last would route the remainder through eno1.

Note I added rules for the FORWARD chain to allow routing to the appropriate IP ranges (if your FORWARD default policy is ACCEPT then you don't need the FORWARD rules).

So, if you want to route all traffic through to the VPN, use:```
-A FORWARD -s 192.168.1.0/24 -j ACCEPT
-A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE
```

To route just traffic going to 172.16.50.0/24 to the VPN, use:```
-A FORWARD -s 192.168.1.0/24 -d 172.16.50.0/24 -j ACCEPT
-A FORWARD 192.168.1.0/24 -d 172.16.50.0/24 -j ACCEPT
-A POSTROUTING -s 192.168.1.0/24 -o tun0 -d 172.16.50.0/24 -j MASQUERADE
-A POSTROUTING -s 192.168.1.0/24 -o eno1 -j MASQUERADE
```

---

### Post by damianv2 on 2016-12-11
Hi,

Thanks for the input.

I want to route all traffic from client through Ubuntu over VPN onto the Internet.

I tried changing the forwarding rule to tun0 but it does not forward the clients traffic.
I added the line as suggested:
```
[COLOR=#000000][FONT=&amp]-A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE[/FONT][/COLOR]
```

But no luck.

Regards

---

### Post by kpatz on 2016-12-11
I don't use ufw but I do use iptables, so I don't know if this option is applicable, but if you add **-t nat** to your postrouting masquerade rules does that help?

For example:

```
-A POSTROUTING -t nat -s 192.168.1.0/24 -o tun0 -j MASQUERADE
```

Adding a routing table entry may do the trick as well:

```
ip route add default via a.b.c.d 
``` where a.b.c.d is the router IP on the other side of the VPN.

If that doesn't work, post the output of **ip route** while connected and also while disconnected from the VPN.

---

### Post by damianv2 on 2016-12-12
Hi,

OK, I tried with the ```
[COLOR=#000000][FONT=&quot]-t nat[/FONT][/COLOR]
``` but it prevents the VPN from connecting at all.
I then tried adding the route, but still no luck.

I reset everything and changed the iptable rule back to: ```
-A POSTROUTING  -s 192.168.1.0/24 -o tun0 -j MASQUERADE
``` and for some odd reason it is working.. 8-[

I am glad it is working, but not sure what the solution was.

Thanks for you help [COLOR=#000000]kpatz[/COLOR]

---

