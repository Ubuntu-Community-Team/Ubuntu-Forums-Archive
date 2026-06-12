---
title: "Feisty WiFi problem"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by amphet on 2007-05-13
I just did a fresh install to feisty, downloaded linux-wlan-ng and all related packages to setup my wifi like I had it in edgy, it gets recognized and all, connects to the router but it won't connect to the internet :confused: 

any ideas?

---

### Post by PCE_Moose on 2007-05-13
If it connects to the router than the problem lies in your router settings.
The router connects to the internet, so look into your router manufacturers help/support.

PCE_Moose

---

### Post by amphet on 2007-05-13
> **PCE_Moose said:**
> If it connects to the router than the problem lies in your router settings.
The router connects to the internet, so look into your router manufacturers help/support.

PCE_Moose

how can that be, I didn't changed anything in my router configuration.

The adapter was working fine under edgy with the same router.

---

### Post by amphet on 2007-05-13
Listening on LPF/wlan0/00:50:f2:cf:bc:71
Sending on   LPF/wlan0/00:50:f2:cf:bc:71
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
*ip length 314 disagrees with bytes received 534. 
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
*ip length 314 disagrees with bytes received 534.
*accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 968415157 seconds.
                                                                         [ OK ]

I belive the lines I marked with a * it's my problem but can anyone interpret that for me?

---

### Post by amphet on 2007-05-13
FIXED

anyone else who has this problem

sudo aptitude remove network-manager

and you should be fine.

---

