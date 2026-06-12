---
title: "Squid proxy hits the Internet with internal IP addresses !"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by tamiral on 2007-05-10
I have a NAT'ed Linux router using IPTABLES and I also recently added a transparent Squid cache proxying to it as an added capability.
I'd like all employees at my workplace using the cached Proxy server so I can log each and every web page they visit
(BTW: A great Squid monitoring program is: [http://www.squint.com/](http://www.squint.com/))

Problem is that whenever the transparent proxy is active, outgoing TCP headers saves the Internal IP address instead of swapping it to the router's external IP.

When the proxy is up, if I go:
```

$ lynx -dump www.whatismyip.org
```
I get: 192.168.1.207

When the proxy is down, if I go:
```

$ lynx -dump www.whatismyip.org
```
I get: 213.8.xx.xx (which is the correct public IP that I have, NAT'ed)

I have an IPTABLES rule which should replace source address (SNAT) to the external (public) IP in the following way:
```

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 213.8.xx.xx
```
and it does, as long as the Squid proxy is down...

The rule I've initiated to make the proxy transparent is:
```

iptables -t nat -A PREROUTING -i eth1 --src 192.168.0.0/16 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

Could you think of a solution for me? I've tried Googlin' it but no luck so far.
This is extremely problematic for me since it's not very secure to have private IPs running all over the Internet...

---

