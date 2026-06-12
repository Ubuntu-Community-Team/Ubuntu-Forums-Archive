---
title: "apt.conf file help"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by russell23 on 2007-07-15
Dear ubuntu users,

i am new to linux and i installed ubuntu-7.04 inmy machine with intel x86_64 machine. i am try9ing to configure the apt-get utility but i could not able to find the file apt.conf in /etc/atp. can any one psot thier file, so that it would be very helpful to me? one more thing, i am behind a proxy and it would better if i can get some tip to how to configure with proxy information. many thanks in advance

---

### Post by spd106 on 2007-07-16
Sure, mine looks like this.
```
Acquire::http::Proxy="http://squid-proxy.local:3128";
```

It allows me to use my squid proxy server to download packages indirectly. I used apt-proxy for a while, but it seemed redundant so now I just use squid.

Instead of this you can configure Synaptic to use a proxy separately, but then the apt command line tools won't work as well. By using the apt.conf file all apt utilities that use it will work.

---

