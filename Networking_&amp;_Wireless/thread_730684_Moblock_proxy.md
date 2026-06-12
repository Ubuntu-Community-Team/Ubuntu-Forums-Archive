---
title: "Moblock proxy?"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Gendo Ikari on 2008-03-21
I have ubuntu server 7.10 running on a PII 300 with 196MB's of memory. I'm using webmin to control it since I can't figure out how to run VNC and control it from my windows machine.

Basically I want to have all my traffic pass thru this machine running moblock, which will be placed between my router and hub.

Help?

---

### Post by jre on 2008-03-21
I can't tell you how to make it a proxy. But about MoBlock:

Keep in mind that a proxy means that the traffic from your other machines will be filtered in the FORWARD chain.
MoBlock often blocks traffic from your LAN (this means that you can't access that proxy from your other machines and that all traffic will be filtered).
So I suggest to whitelist your LAN IPs in the INPUT and OUTPUT chains to** make sure that you always can access your proxy** (The IPs are an example for my LAN):here):
```
WHITE_IP_IN="192.168.178.0/24"
WHITE_IP_OUT="192.168.178.0/24"
WHITE_IP_FORWARD=""
```
I guess if you did this also for the FORWARD chain then no traffic at all would be blocked.
But anyway, first try to also whitelist the FORWARD chain. If this really means whitelisting everything and whithout it means blocking everything then you still can find the responsible line in the blocklist and remove it with IP_REMOVE.

All these variables are in /etc/moblock/moblock.conf. If you don't want to readd them after every package update I suggest to insert them to /etc/default/moblock.

---

### Post by Gendo Ikari on 2008-03-29
Does anyone know how I can go about doing this?
I also can't get VNC server to work under Xubuntu so I can connect to it from MS Windows.

---

### Post by Gendo Ikari on 2008-04-15
How do I configure my two network cards to forward traffic, such as the gateway setting for each.

---

