---
title: "Atheros card not finding any networks"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by AstronomyDomine on 2007-09-23
I've just installed Kubuntu Feisty Fawn on a Toshiba A35-S159 with an internal Atheros wireless card.  lspci -v lists it as  an "AR5212 802.11abg NIC"  and it seems to work with network manager.  It is named ath0.

However, it can never find or connect to any wireless networks.  Running iwlist ath0 scan always returns "ath0 No scan results" instantly, it seems as if it doesn't even try to scan.  Even configuring my network manually through /etc/network/interfaces, then running ifdown and ifup, does nothing.

It almost seems to be a hardware problem, but I thought I'd try here first, just in case anyone has encountered this before and knows of an answer.

Any ideas would be greatly appreciated.

---

