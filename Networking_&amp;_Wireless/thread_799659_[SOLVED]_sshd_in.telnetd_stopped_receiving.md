---
title: "[SOLVED] sshd in.telnetd stopped receiving"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-05-19
sshd and in.telnetd were working well on 7.10 KUbuntu on my Thinkpad T61p

Then I took my Thinkpad T61p to a WEP-encrypted network.

I tried adding the pptp components; I could not get them to work at all. 

I brought the system back to my wired network.

in.telnetd is not running but is enabled in /etc/inetd.conf.

I added sshd using adept.

It will not respond either.

The logs do not give me anything obvious. 

What am I missing? What would be the obvious place to look to see why neither sshd nor in.telnet will respond?

Somehow, an additional auto lo crept into my /etc/network/interfaces file. Once removed, all was well.

---

