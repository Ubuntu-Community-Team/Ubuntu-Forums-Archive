---
title: "IPs Ping but missing from IFCONFIG"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by Bashed on 2016-11-25
I ran a script below to route 20 x /24 subnets for VPN use.

```
for i in $(seq 2 254);
        do ip addr add xxx.xxx.3.$i/24 dev em1
        ip addr add xxx.xxx.58.$i/24 dev em1
        ip addr add xxx.xxx.65.$i/24 dev em1
        ip addr add xxx.xxx.80.$i/24 dev em1
        ip addr add xxx.xxx.90.$i/24 dev em1
        ip addr add xxx.xxx.21.$i/24 dev em1
        ip addr add xxx.xxx.31.$i/24 dev em1
        ip addr add xxx.xxx.30.$i/24 dev em1
        ip addr add xxx.xxx.40.$i/24 dev em1
        ip addr add xxx.xxx.50.$i/24 dev em1
        ip addr add xxx.xxx.60.$i/24 dev em1
        ip addr add xxx.xxx.70.$i/24 dev em1
        ip addr add xxx.xxx.81.$i/24 dev em1
        ip addr add xxx.xxx.1.$i/24 dev em1
        ip addr add xxx.xxx.6.$i/24 dev em1
        ip addr add xxx.xxx.16.$i/24 dev em1
        ip addr add xxx.xxx.17.$i/24 dev em1
        ip addr add xxx.xxx.29.$i/24 dev em1
        ip addr add xxx.xxx.34.$i/24 dev em1
        ip addr add xxx.xxx.70.$i/24 dev em1        
done

ip addr show
```

They all ping fine, but ifconfig output does not list them.

I'd like to fix that and need someone's help please.

---

