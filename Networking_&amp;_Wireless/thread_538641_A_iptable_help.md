---
title: "A iptable help"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by rsync on 2007-08-30
I have two network cards in a PC running Dapper:

NIC1 - 10.0.0.1
NIC2 - 192.168.2.1

I want to forward all traffic on port 3899 of NIC1 to port 3899 of NIC2.

It's that simple...unfortunately, I can't seem to get it working.

---

### Post by f00buntu on 2007-08-30
I think you can make it work with only two iptables rules:

```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3899 -j DNAT --to-destination 192.168.2.1:3899
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

And enable ip forwarding:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

To make ip forwarding persistent uncomment *#net/ipv4/ip_forward=1*in /etc/sysctl.conf

Add your iptables commands to /etc/network/interfaces as 'up' commands  (man interfaces) or put them in a script in /etc/network/if-up.d

---

### Post by rsync on 2007-08-30
Thanks a lot!!! :)

---

