---
title: "Broadcast IP"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by Elijah_Tan on 2014-06-26
Hi,

I just want to know the example in your server guide about network configuration,

```
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

Why do we need to specify network and broadcast in /etc/network/interfaces? Is it mandatory?
If not, what is the main purpose or when is the good time for us to use it?

I thought it could work well without these lines, as I always go without them,
because I believe the server is able to calculate the network and broadcast itself.

Thanks.

---

