---
title: "How to make iptables remember/save stuff?"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Starlight on 2008-04-25
Hi! I don't really know much about iptables, but there's one game (Ragnarok Online) which needs a specific iptables rule to be added to make it connect to its server properly... here's the command I type in the terminal to add it:

sudo iptables -t nat -A OUTPUT -d (some IP address here) -j DNAT --to-destination (another IP address here)

After I do it, the game has no problems connecting with the server. But I need to do that every time after I reboot the computer. Is there some way to make iptables save it, so that it always remebers it?

---

### Post by Monicker on 2008-04-25
iptables-save

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by Starlight on 2008-04-25
Thank you! :)

---

### Post by piousp on 2008-05-06
> **Starlight said:**
> 

sudo iptables -t nat -A OUTPUT -d (some IP address here) -j DNAT --to-destination (another IP address here)

By (some IP address here) you mean your IP add?

and by (another IP address here) you the server IP add?

Anyway, i'm gonna try it out that way to see if it works.

---

