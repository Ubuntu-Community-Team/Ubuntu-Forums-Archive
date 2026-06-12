---
title: "Set up a transparent squid but it is not transparent"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by rolandpish on 2007-05-06
Hi there,

I just set up a proxy server squid to be transparent.
My network configuration:
eth0 = 192.168.1.2 connected to internet
eth1 = 192.168.2.1 connected to lan

I added the corresponding lines to squid.conf:
http_port 192.168.2.1:3128 transparent
acl lan src 192.168.1.2 192.168.2.0/24
http_access allow lan

Activated forward bit:
echo 1 > /proc/sys/net/ipv4/ip_forward
Executed iptables command:
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

The problem is that client machines can't navigate Internet. In order to let them navigate I have to setup each client browser to connect using the proxy on 192.168.2.1:3128. After this, client computer navigates successfully and proxy works properly.  That's why I think the problem is with iptables, but I have two days in this, googled a lot and tried different combinations of iptables but with no success.

I would really appreciate your help in this.

Best Regards

Roland

---

### Post by rolandpish on 2007-05-07
I decided to stop squid service and try if internet sharing was possible between the two nics. I wasn't possible, so I started to worry a lot.
I was close to rip my hair out but I think I solved the problem after days of fighting with this, what was the problem? I forgot to install bind9!!!

After I installed bind9 internet sharing started to work perfectly (exactly the way it worked before).
Tonight I'll install squid and I'll see if it works as expected.

Best Regards

Roland

---

