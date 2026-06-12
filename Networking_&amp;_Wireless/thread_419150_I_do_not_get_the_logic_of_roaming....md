---
title: "I do not get the logic of roaming..."
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by mac.ryan on 2007-04-22
Feisty64 here.

I have troubles in understanding the logic of the roaming mode: I live in a place where my WiFi is encrypted, but I get the signal of open networks from neighbours. I configured Feisty for my own network, but if I am in roaming mode, Feisty insists to connect me to one of the latter ones, no matter what.

Two questions then:
[LIST=1]
[*]what is the logic here? I would expect that Feisty would first attempt with secure networks, and only afterwards would try for open ones (to me: security and privacy should come first when you speak about the Internet). Evidently Feisty has another criteria, does anybody know which one?
[*]Is there a tweak to configure that? (i.e. a way to explain the roaming bit that it should try networks in a given order, according for example to: a custom list, or the power of the signal, or the b/g/n protocol, or...[/LIST]many thanks in advance...

---

### Post by spd106 on 2007-04-23
AFAIK it automatically reconnects to the network it was last connected to. The settings are in gconf. See this FAQ for more details [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

### Post by mac.ryan on 2007-04-24
Thanks. That link is being very useful! :)

---

