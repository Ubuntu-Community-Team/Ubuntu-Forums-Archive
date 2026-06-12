---
title: "Connection failed: Activation of network connection failed after network changes"
date: 2018-10-12
forum: Networking &amp; Wireless
---

### Post by thecorrupted on 2018-10-12
A couple days ago, I was following along with a community help article on using [dnsmasq]("https://help.ubuntu.com/community/Dnsmasq") and foolishly forgot to make backups of the files I was changing. Since then, I've been locked into one wifi network, and upon trying to connect to another I get: **Connection failed Activation of network connection failed.**

[ATTACH=CONFIG]281323[/ATTACH]

As such I'm wondering if there is a way I can reset the network, DNS, and DHCP settings for the system back to its default without reinstalling Ubuntu or jumping back to a previous state? I believe the changes I made to dhclient.conf, dnsmasq.conf, and resolv.conf are the problem, but it's hard to tell, as the day the changes were made, I was still able to connect to all visible networks. It wasn't until a couple days later that I started getting this error.

[wireless-info.txt]("https://paste.ubuntu.com/p/rffm6K6CNK/")

---

