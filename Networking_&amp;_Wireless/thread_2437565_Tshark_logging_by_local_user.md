---
title: "Tshark logging by local user"
date: 2020-02-25
forum: Networking &amp; Wireless
---

### Post by dyous87 on 2020-02-25
I'm running an Ubuntu server on a corporate network in which users log into either via RDP or SSH with x-forwarding. I want to use TShark to log all network traffic but I'd like to know if there is anyway I can have the Linux username added to the packet capture. In another words if 'user_a' and 'user_b' are both logged into the server I'd like their respective internet traffic to log there usernames. Is this at all possible with TShark? I've read that iptables can "tag" traffic but I'm not sure exactly how it works and if it would accomplish what I'm trying to do.

---

