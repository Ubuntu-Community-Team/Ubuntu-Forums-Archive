---
title: "Hurricane Electric HE-IPV6 Tunnel issue with Ubuntu 18.04.3 LTS"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by silicon11 on 2019-11-08
I am having issues with getting Hurricane Electric HE-IPV6 Tunnel to work with Ubuntu 18.04.3 LTS, Here is my tunnel config:

```

    tunnels:
      he-ipv6:
        dhcp4: no
        dhcp6: no
        mode: sit
        remote: 216.218.226.238
        local: 192.168.0.9
        nameservers:
          addresses: [ '2001:4860:4860::8888', '2001:4860:4860::8844' ]
        addresses: [ '2001:470:x:000::2/64' ]
        gateway6: 2001:470:x:000::1

```

Has anyone able to get this working?

---

### Post by jeremy31 on 2019-11-08
Ubuntu 12.04 is no longer supported as support ended in 2017

---

### Post by silicon11 on 2019-11-09
Sorry I meant Ubuntu 18.04.3 LTS, Netplan wasn't even in Ubuntu 12.04.5 LTS Precise Pangolin to my knowledge but that was the version I was able to get it working with ifupdown

---

