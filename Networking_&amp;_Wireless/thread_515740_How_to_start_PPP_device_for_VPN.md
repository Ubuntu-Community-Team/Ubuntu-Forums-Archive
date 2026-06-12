---
title: "How to start PPP device for VPN?"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2007-08-02
Hi,
I hope somebody can help me. I'm trying to connect to a VPN. I've got all the config files I need and copied them over to the right locations. When I manually start /etc/init.d/ipsec and then do "ipsec auto --up myvpn" then it also connects properly. But I also need to start xl2tpd manually. When I then tell xl2tpd to connect, I get error messages. I guess this is because the PPP device is not up. I've got this config file snippet which I added to /etc/network/interfaces:

```

iface ppp1 inet manual
        pre-up /etc/init.d/ipsec restart
        pre-up /etc/init.d/xl2tpd restart
        up sleep 5 && echo "c sedocologne" >/var/run/xl2tpd/l2tp-control
        up sleep 10 && ip r add 10.0.0.0/8 dev ppp1
        up ip r add 172.16.0.0/12 dev ppp1

```

It's clear to me what this all means, but how the hell do I start this PPP device? Entering ifconfig ppp1 up doesn't help, it tells me "no such device". Can anybody help me with this?

Tom

---

