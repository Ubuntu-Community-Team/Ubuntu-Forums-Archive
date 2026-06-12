---
title: "Cannot SSH when connected Wirelessly"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by daxumaming on 2008-02-07
I have a problem here with SSH on Gutsy. It seems that I can ssh To and From my laptop if it's connected via ethernet. But when I go wireless, my SSH drops and I keep on getting **No route to host** errors.

I don't have a firewall installed, except iptables - which I haven't configured. I've also disabled any wireless security settings I have on the router. But i still can't connect via SSH when using a wireless connection.

I'm attaching my sshd_config.

Any insights on this matter is highly appreciated... Thanks!

---

### Post by daxumaming on 2008-02-08
Ok, now I know what's causing the problem, my eth0 still up. That's why I can't ssh through wireless. To be able to ssh, I have to disable eth0.

---

