---
title: "DNSMAQ + DHCP with virtual network"
date: 2024-06-18
forum: Networking &amp; Wireless
---

### Post by pw442 on 2024-06-18
Hya,

my ubuntu server box have two NIC's one the public interface and the other the internal. I prefer the traditional model, network interfaces instead of the netplan, and it works well.

By eth0, i created the eth0:0 virtual interface with another ip address.

By dnsmasq, i have the following dhcp entries:

```
[FONT=monospace][COLOR=#000000]interface=eth0[/COLOR]
interface=eth0:0
interface=eth1
interface=wap0
[/FONT][FONT=monospace][COLOR=#000000]listen-address=192.168.80.4[/COLOR]
listen-address=192.168.58.4
listen-address=192.168.28.4
listen-address=127.0.0.1
.....
[/FONT][FONT=monospace][COLOR=#000000]dhcp-option=eth0,3,192.168.80.4[/COLOR]
dhcp-option=eth0:0,3,192.168.80.4
dhcp-option=wap0,3,192.168.80.4
dhcp-option=option:router,192.168.80.4
[/FONT][FONT=monospace].....
[/FONT][FONT=monospace][COLOR=#000000]dhcp-range=eth0,192.168.80.10,192.168.80.240,255.255.255.0,6h[/COLOR]
dhcp-range=eth1,192.168.58.10,192.168.58.240,255.255.255.0,6h
dhcp-range=wap0,192.168.28.10,192.168.28.240,255.255.255.0,6h
dhcp-range=eth0:0,192.168.58.100,192.168.58.240,255.255.255.0,6h
[/FONT]
```[FONT=monospace].....

But it seams that for eth0:0 the address allocation does not work.

Any hints?

Thx in advance!



[/FONT]

---

### Post by currentshaft on 2024-06-18
The ":" notation likely has a special meaning in the dnsmasq config:

-F, --dhcp-range=[tag:<tag>[,tag:<tag>],][set:<tag>,]<start-IPv6addr>[,<end-IPv6addr>|constructor:<in&#8208;
       terface>][,<mode>][,<prefix-len>][,<lease time>]

Can you give the virtual interface a different name without that character?

---

