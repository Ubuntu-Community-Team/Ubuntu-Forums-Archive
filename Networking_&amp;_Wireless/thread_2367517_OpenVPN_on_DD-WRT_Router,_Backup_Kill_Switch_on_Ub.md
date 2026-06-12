---
title: "OpenVPN on DD-WRT Router, Backup Kill Switch on Ubuntu UFW"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by linux-lion2 on 2017-07-31
I have DD-WRT on my router with my OpenVPN  and a working kill switch. While rebooting my router I notice it leaked my real ip once. Never saw it leak again afterwards. Therefore, I want to create a backup kill switch with UFW in my Ubuntu desktop. I am connected via Ethernet.

The problem that I am having is that I am on a Ethernet connection so there is no tun0. The commands that I find on the Internet is for tun0 only or local ip starting with 192.168. 

I tried so many commands to get this to work and had no luck. 

Nothing from [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) works for my needs since my VPN ip address is coming from my router's OpenVPN config and I am connected via Ethernet my preferred connection.

Allow by Specific IP does work, by port either (1194).

Please Help!

---

### Post by linux-lion2 on 2017-08-01
Anyone? Please help!

---

