---
title: "Port forwarding to different hosts"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by MattNuzum on 2007-04-28
I have a network card that has two aliases. For example, in /etc/network/interfaces:
```
iface eth0 inet static
    ....
iface eth0:1 inet static
    ....
iface eth0:2 inet static
    ....
```

This host is kind of a router, and it uses iptables for NAT and port forwarding. I'd like to have, for example, 
[LIST]
[*]port 80 on eth0 go to one host, 
[*]port 80 on eth0:1 go to a different host and 
[*]port 80 on eth0:2 go to yet another host.
[/LIST]

I've never done this before. I thought I'd use a command like
```
iptables -A PREROUTING -t nat -p tcp -i eth0:1 --dport 80 -j DNAT --to 192.168.1.10:80
```

But this gives the rather self explanatory error:
```
Warning: weird character in interface `eth0:1' (No aliases, :, ! or *).
```

Can anyone suggest how I can set up these iptables rules so that I can get the desired effect?

---

### Post by MattNuzum on 2007-04-28
OK, this seems to work:
```
iptables -t nat -A PREROUTING -p tcp -i eth0 -d $external_ip --dport 80 --sport 1024:65535 -j DNAT --to $ip_to_forward_to:80
```

---

