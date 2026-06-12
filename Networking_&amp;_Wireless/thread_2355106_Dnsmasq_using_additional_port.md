---
title: "Dnsmasq using additional port"
date: 2017-03-09
forum: Networking &amp; Wireless
---

### Post by tera23 on 2017-03-09
Hi.

I'm new to linux - so be gentle or provide instructions please.
I want to ask a question about dnsmasq - used with network-manager.

I've noticed the dnsmasq started using a high port "UDP *:51560". I've beed using this instalation for about a month and before only port 53 was used. It occured after a night of torrent-downloading. Whats going on, why is this happening? the port never changes and doesn't go away. I can't find any configuration files for dnsmasq - it seems there aren't any. Everything should be on its default settings.

dnsmasq 1919 nobody 4u IPv4 26562 0t0 UDP nexxus:53
dnsmasq 1919 nobody 5u IPv4 26563 0t0 TCP nexxus:53 (LISTEN)
dnsmasq 1919 nobody 11u IPv4 21045 0t0 UDP *:51560

Can anyone explain or help me resolve this issue?

Ubuntu 16.04.2 LTS

Thank you.

---

### Post by tera23 on 2017-03-10
Ok, I've read somewhere that this is normal behaviour, and I have noticed that the port does actually change upon restart.
Can someone explain why is this additional port necessary and why does dnsmasq sometimes use more than one such port?

---

### Post by ristosu on 2017-03-20
That port is used for forwarded outgoing requests. Earlier versions picked a random port for every request.

Why this behaviour has changed, I don't know. But I don't like it.

Risto

---

