---
title: "How to create post-up and pre-down routes in interfaces file?"
date: 2018-05-01
forum: Networking &amp; Wireless
---

### Post by brophy2 on 2018-05-01
I recently installed a new VM using Ubuntu 16.04, but I am unable to copy the `post-up` and `pre-down` rules that I use in my 14.04 install.

Can you please advise what to use? I've added a few notes to indicate what each of my edited out ips are

Example of the 14.04 config:

```
    # The primary network interface
    auto eth0
    iface eth0 inet static
            address x.x.x.109 #vm ip
            netmask 255.255.255.255
            broadcast x.x.x.109 #vm ip
            post-up route add x.x.x.254 dev eth0 #root machine gateway
            post-up route add default gw x.x.x.254 #root machine gateway
            pre-down route del x.x.x.254 dev eth0 #root machine gateway
            pre-down route del default gw x.x.x.254 #root machine gateway
            dns-nameservers 213.186.33.99 8.8.8.8
```

---

