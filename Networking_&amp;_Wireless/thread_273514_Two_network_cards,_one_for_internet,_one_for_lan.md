---
title: "Two network cards, one for internet, one for lan"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by factor on 2006-10-08
Hi, i'm trying to use one card for internet, and another one for lan. My board is an ASUS A8N32-SLI Deluxe, so both cards are integrated. One is from the nforce4 chipset (eth1), and the other one is a marvell (Eth0).

I'm using firestarter for that, i have enabled ICS. The external router uses the network 192.168.0.192/254, and i think here lies the problem.

I have followed instructions from firestarter to configure, and here is my config:

eth1 (internet): 192.168.0.2, gateway 192.168.0.1 (router), mask 255.255.255.0

eth0(lan): 192.168.0.5, mask 255.255.255.0, no gateway.

eth0 is connected to a switch, and that switch is connected to another computer. The reason i don't connect thru the router is that the router is 10mbps for lan, and it's way too slow for my needs.

The setup for the other computer is:

192.168.0.100,mask 255.255.255.0, gateway 192.168.0.5

I think the problem is that router and lan are using the same ip ranges, but i'm not sure. What could i do to solve that?

THanks in advance for your help.

Regards.

---

### Post by factor on 2006-10-08
Btw, internet is working perfectly, the problem lies in lan, i can't even ping the other computer, when i try i get the following error:

PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
(repeat until i close the terminal)

Regards.

---

### Post by mips on 2006-10-08
You can NOT have both interfaces in the same network, 192.168.0.0.

Change Eth0 to 192.168.1.0 Eth0s gateway is then specified as the IP address of Eth1.

---

### Post by factor on 2006-10-09
Thanks for replying, i found for myself a fer minutes after tho, but it will be useful for other people.

I used 10.0.0.1 in my case, with different subnet mask, should i use same subnet mask? it already works but i've seen a tutorial on internet saying i should use same subnet mask, i don't know why tho

Regards.

---

### Post by mips on 2006-10-09
No, you don't need the same subnet mask.

---

