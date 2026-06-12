---
title: "UDP: short packet: From"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Jense on 2008-03-06
Hi everybody,
I have this weired problem in my local network. dmesg spits out endless lines of errocode like this:
```

[15521.404000] UDP: short packet: From 195.50.140.252:80 27800/55 to 192.168.0.162:50891
[15841.824000] UDP: short packet: From 195.50.140.252:80 50974/62 to 192.168.0.162:47564
[16162.764000] UDP: short packet: From 195.50.140.252:80 15112/63 to 192.168.0.162:50667
[18836.264000] UDP: short packet: From 195.50.140.252:80 25687/62 to 192.168.0.162:39865
[19465.484000] UDP: short packet: From 202.101.100.69:80 1749/70 to 192.168.0.162:54899
```

The target IP is my internal network ip. The message varies for other people in this network with respect to their target IP. The source IP changes. 
We have P2P software running, but this appears when it's tuned off as well. A router reboot (with new IP) doesn't fix this. So I am wondering wether this might be an attack of some kind. The internet is sometimes really slow and maybe that is the source.

Any ideas?

Thx

---

### Post by Jense on 2008-03-07
nobody?

---

### Post by alexanderzubin on 2008-06-22
I'm afraid I have another instance of such error but in my case this is a DNS server

UDP: short packet: 202.206.64.33:53 2875/145 to 193.188.97.212:30203

UDP: bad checksum. From 213.97.61.212:53 to 193.188.97.212:32851 ulen 128

UDP: short packet: 201.6.0.136:53 182/180 to 193.188.97.212:33097

UDP: short packet: 89.148.44.54:30151 292/36 to 193.188.97.212:53

UDP: short packet: 77.69.196.161:33601 256/36 to 193.188.97.212:53

UDP: short packet: 201.6.0.136:53 166/164 to 193.188.97.212:33097

UDP: short packet: 84.255.188.27:30185 292/36 to 193.188.97.212:53

UDP: short packet: 84.255.188.27:30190 298/42 to 193.188.97.212:53


Any ideas what is a cause for this? It appears that a certain number of these errors can cause a disruption in service. It is also a old kernel (2.4) we talking about. Any help will be appreciated

---

