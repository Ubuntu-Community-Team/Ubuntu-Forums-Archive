---
title: "IPTABLES redirect to proxy"
date: 2019-04-24
forum: Networking &amp; Wireless
---

### Post by uthall on 2019-04-24
Hello,

I have a server that i want all requests to a specific domain, to be redirected to an external proxy server.

Details are

Internal Server ip: 192.168.1.4
proxy ip: 1.2.3.4
domain to redirect: example.com

So i want any request from server 192.168.1.4, to domain example.com, to redirect to the proxy server 1.2.3.4

How would i do this with IPTABLES?

---

### Post by SeijiSensei on 2019-04-24
Iptables largely relies on IP addresses and port numbers. If you're talking about proxying a specific service like HTTP you might have better options that recognize domains.

Squid knows how to send requests to upstream proxy servers, and you can write rules by domain.

Another possibility is the proxying features in Apache.  This sounds less suited to your request than Squid.

With iptables you could write a rule that relies on the IP address of example.com like this:

```
sudo iptables -t nat -A INPUT -p tcp -d ip.addr.example.com --dport 80 -j DNAT --to-destination 1.2.3.4:portno
```

That forwards port 80 TCP traffic for ip.addr.example.com to port "portno" on 1.2.3.4. It uses the "nat" table. See "man iptables" for details.

---

### Post by uthall on 2019-04-24
Thanks,

Yes i could use the IP address if i had to, just preferred to use domain name if possible.

That iptables rule looks ok, although id prefer all traffic to example.com, not just port 80.

Is it possible to use the squid box like a smart dns? I know with those, id use the squid box as the dns server, and it decides what to proxy and what not to proxy based on rules i set?

PS: Not quite sure, but im getting an invalid argument for

sudo iptables -t nat -A INPUT -p tcp -d 104.28.31.233 --dport 80 -j DNAT --to-destination 139.99.219.132:3128

---

### Post by SeijiSensei on 2019-04-24
Sorry.  How about

```
sudo iptables -t nat -A PREROUTING -p tcp -d 104.28.31.233 --dport 80 -j DNAT --to-destination 139.99.219.132:3128 
```

Iptables and most other proxies are designed to work on a service basis.  A quick Google search confirms that iptables still relies on numeric IP addresses and port numbers. I suspect you could write an ACL in Squid that would invoke relaying by domain name, but I've never used it's relay facility.

I write scripts for iptables and often have constructs like this to manage multiple similar rules. For example, if example.com has multiple server IPs:
```

#!/bin/bash

relayhost=10.10.10.10
relayport=3128
relayip="172.17.15.15 172.18.27.134"

for h in $relayip
do
     iptables -t nat -A PREROUTING -p tcp -d $h --dport 80 -j DNAT --to-destination $relayhost:$relayport
done

```
That will add a rule for each server IP in $relayip.

---

### Post by uthall on 2019-04-24
Thanks again,

running sudo tail -f /var/log/squid/access.log on my squid box shows no activity when i use that iptables rule.

However, if is use iptables -t nat -A OUTPUT --dst 104.28.31.233 -p tcp --dport 80 -j DNAT --to-destination 139.99.219.132:3128

i get activity on squid. 

Still but, when trying to access the ip [COLOR=#000000][FONT=&quot]104.28.31.233 on port 80, i still get time outs.

I feel there is something missing but i dont know what?[/FONT][/COLOR]

---

### Post by uthall on 2019-04-24
Just posted also asking for maybe a guide on setting up a dns proxy server, which may be better......just an fyi.

---

### Post by SeijiSensei on 2019-04-25
One thing to check. Did you enable IPv4 packet forwarding in /etc/sysctl.conf?  If not, try removing the hash mark from the beginning of the line in that file that reads
```
net.ipv4.ip_forward=1
```
and rebooting.

Squid works at the "application layer" so rules about packets don't matter to it.

Also try adding "-m tcp" to the options in the iptables rule.

I don't know what a "DNS proxy server" is.  However DNS could provide a solution.  Install BIND on the server and configure it and all the clients to use that server rather than what they use now.  Then create an entry for example.com with an A record that points to 139.99.219.132 instead of 104.28.31.233. That avoids any sort of proxying whatsoever.

---

### Post by uthall on 2019-04-25
Thanks ill check that out.

Re the dns thing, if i create the A record like that, then how will any packets ever get to the 104 address. Remember, i still want to reach that server, just using the 139 server a essentially a jump host.

---

