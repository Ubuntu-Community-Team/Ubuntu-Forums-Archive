---
title: "having trouble port forwarding with iptables"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by asteway on 2016-07-21
I have the following interfaces configured on my gateway running iptables:

eth0 - 6.7.8.9 (public ip)
eth1 - 10.0.10.1 (Internal LAN)

I want to host a web server on 10.0.10.6 from my internal LAN to be accessible from outside my LAN (the internet) via port 80.

I am assuming I need to forward port 80 on my gateway to port 80 in my internal web server. (please correct me if I am wrong or if I have any other option).

I run the following commands on my gateway to forward and NAT both incoming and outgoing traffic to my web server but I still can't reach my web server from outside.

```

iptables -A FORWARD -i eth0 -o eth1 -m state -p tcp -d 10.0.10.6 --dport 80 --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -p tcp -A PREROUTING -i eth0 --dport 80 -j DNAT --to-destination 10.0.10.6
iptables -t nat -p tcp -o eth0 -A POSTROUTING -s 10.0.10.6 --dport 80 -j SNAT --to-source 6.7.8.9

```


FYI: I already have ip_forward enabled.
        I have no other iptables rules on my gateway.

Thanks for your help

---

### Post by asteway on 2016-07-25
Doug S ;
Thanks for the private message.


First of all, I wrongly typed the address. I meant to use 6.7.8.9 instead. I have corrected that in the original post.
So it should all read
```

iptables -t nat -A POSTROUTING -p tcp -o eth0 -j SNAT --to-source 6.7.8.9

```
Secondly, I don't think that should prevent my site from being accessed from the internet as far as my PREROUTING rule is correct. i.e. incoming packets are being forwarded correctly. However, I am taking your advice and changing that to


```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```


Let me know if you have a better suggestion.

[QUOTE=Doug S]Problems with forums right now are preventing me from posting my reply.
Here is my reply:

I believe your POSTROUTING rule is incorrect. Specifically, the destination port for the return packet wouldn't be 80. I would suggest a more generic POSTROUTING rule:
```
iptables -t nat -A POSTROUTING -p tcp -o eth0 -j SNAT --to-source 213.55.103.202
```
And note that you do not actually need the FORWARD rule, unless your default policy for the FORWARD chain is DROP.[/QUOTE]

---

