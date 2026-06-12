---
title: "Wireless service frequent disconnections"
date: 2018-04-26
forum: Networking &amp; Wireless
---

### Post by krishnan t s on 2018-04-26
I have a dual boot of elemntary os and a fresh installation of Ubuntu 16.04.4 LTS. In both my setups, my wifi stops working every 5 minutes and starts working only when i click the wifi again(The wifi status still shows connected though). My other devices(oneplus one, iPhone and Windows Desktop) are connected and working fine on the same network. I have already disabled power management for my network, added additional dns adresses to my ipv4 connection and disabled my ipv6 connection by following threads similar to mine on this forum. 
Is there anything else i can do?

---

### Post by kerry_s on 2018-04-26
is your connection hidden? linux is not very good with hidden connections.

---

### Post by krishnan t s on 2018-04-26
No. Its not hidden. The status shows as connected but i'mnot able to load any webpages unless reconnect by clicking my Wifi name.

---

### Post by kerry_s on 2018-04-26
do you have bluetooth?

there was a bug were bluetooth would mess up wireless, disabling bluetooth helped.

---

### Post by krishnan t s on 2018-04-27
Yes. That seems to have done the trick. My connection has been stable for the last 12 hours. My internet is a tad slow though than what I get on my phone or tablet. Is that normal for ubuntu? Its been a while since I used Ubuntu, so I don't know.

---

### Post by kerry_s on 2018-04-27
no most of that is fixed in newer versions. you might want to consider grabbing the new 18 lts. take for a spin live see how it does.

---

### Post by jeremy31 on 2018-04-27
Post results for ```
lspci -nnk | grep -iA3 net; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by krishnan t s on 2018-04-27
> **kerry_s said:**
> no most of that is fixed in newer versions. you might want to consider grabbing the new 18 lts. take for a spin live see how it does.

I did one better. I installed it a few hours back, got the same issue, switched off bluetooth and got a stable connection. Should i report a bug for bluetooth? The connection is still slightly slower than i'm used to on my other devices

---

### Post by krishnan t s on 2018-04-27
> **jeremy31 said:**
> Post results for ```
lspci -nnk | grep -iA3 net; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```


```
02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3806]
    Kernel driver in use: alx
    Kernel modules: alx
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo AR9485 Wireless Network Adapter [17aa:3218]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
[connection]
wifi.powersave = 3

```

---

### Post by jeremy31 on 2018-04-27
See if disabling Network Managers ability to enable wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf && systemctl restart network-manager.service
```

---

