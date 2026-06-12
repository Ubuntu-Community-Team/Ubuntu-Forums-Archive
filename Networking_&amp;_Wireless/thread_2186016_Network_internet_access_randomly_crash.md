---
title: "Network internet access randomly crash"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by moisesbelda on 2013-11-05
I have a ubuntu 13.10 64 bit fresh intallation in my quad core PC.

Randomly internet lost with any reason. Browse pages, downloads, streaming music, all lost for a few minutes, browser says.... "Resolving host".

- I test ping to another ip inside my local lan => ping works (eth0 works)
- I test ping to [www.google.com](www.google.com) => ping not works (other devices worked at same moment).
- I test ping to external ip in internet => ping not works.

I have eth device and lan connection, but internet is lost for few moments. 

I see /var/log/syslog and I don't see any error.

The network adapter is => Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)

What's the matter?

Thanks

---

### Post by varunendra on 2013-11-06
Welcome to the forums moisesbelda !

How is your ethernet port connected to the router and other devices on your lan? Via a network switch or directly plugged into the router?

If it is directly connected to the router, and you can ping other devices while not even an external IP (try 8.8.8.8 for example), then it sounds like a routing problem. Check your router settings first.

Have you enabled any custom services like QoS or firewall in the router?

---

### Post by moisesbelda on 2013-11-06
Thanks!

But I thing there is no problem with router.

I have 3 pcs (1 windows, 2 ubuntu 12.10) that works well with network configured with same parameters (dhcp). And 3 devices (phones, tablets) too. All connected to the same router.

When internet works normally, I can ping to 8.8.8.8 and another external ips, but randomly for a few minutes that ubuntu 13.10  fails (can make ping to local ip but not remote).

I check router, change conectors, and nothing works. I didn't enabled any firewall or security service.

---

### Post by varunendra on 2013-11-06
Please post the outputs of -
```
sudo ethtool eth0
ifconfig -a
nm-tool
```

I'm not sure if ethtool is installed by default or not in 13.10. If not, install it with -
```
sudo apt-get install ethtool
```

---

