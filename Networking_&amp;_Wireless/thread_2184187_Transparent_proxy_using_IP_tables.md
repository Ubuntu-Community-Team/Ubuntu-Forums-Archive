---
title: "Transparent proxy using IP tables"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by rthijssen on 2013-10-28
G'day,

I've been struggling today to get the following working:

"I would like to redirect all my (http) traffic through my proxy application using iptables"

At first, most online docs say I should add the following iptables rule:

    ```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```

Unfortunately this rule doesn't work for traffic originating from localhost. Since (apparently) this traffic isn't hitting PREROUTING
Therefore I added the following rule:


    ```
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 8080
```

When this rule is active I can see the HTTP requests originating for my system popping up in my proxy. But, it looks like my proxy is not receiving the response.
Does anyone have an idea on why this is not happening? 

Cheers.

FYI, I have set sysctl -w net.ipv4.ip_forward to '1'

---

### Post by SeijiSensei on 2013-10-28
Use a PREROUTING rule instead:
```
/sbin/iptables -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
```

If you want to restrict the rule to specific subnets, use a "source IP" directive like "-s 192.168.1.0/24" in the list.

At a client site we pipe hundreds of workstations through Squid with a rule like this every day.

---

### Post by rthijssen on 2013-10-28
Thanks for your reply. But unfortunately I think this rule only works for external systems. I'm trying to redirect requests from my local machine through my proxy application. And I think local traffic (even to an external system) is not going through the PREROUTING chain.

---

### Post by Newbunto on 2013-10-29
For local traffic can you use a *non*-transparent proxy?

Anyway, if you use a transparent proxy on local traffic, how does the proxy application manage to get its requests to go out without having them in turn redirected?

Traffic to localhost probably isn't hitting 'eth0'. It would be hitting 'lo'?

---

