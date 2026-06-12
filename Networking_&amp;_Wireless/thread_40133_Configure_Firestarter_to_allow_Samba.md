---
title: "Configure Firestarter to allow Samba?"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by Seti on 2005-06-07
I have a small home LAN; my desktop and my girlfriend's Toshiba Satellite A10 that also runs Hoary. We use Samba to share folders back and forth, and usually it runs really smoothe, aside from the occasional hiccup. Anyway...
We are behind a D-Link wireless hub and router, I connect via LAN cable, and she connects wirelessly. The access point is secure; 128-bin WEP, MAC address filtering, password, no open ports for services. So from that standpoint, we are pretty safe behind it. I'd also like for both of our machines to run Firestarter firewall, just for the extra layer of protection, but so far any attempts on my part to set it up blocks samba. Does anyone use Firestarter and Samba, and could you give me some hints how to configure it so the firewall is on while we still share folders?

Thanks!

---

### Post by dataw0lf on 2005-06-08
Open up ports 138-139, and 445.

---

### Post by Seti on 2005-06-08
Thanks, I'll try it.

---

