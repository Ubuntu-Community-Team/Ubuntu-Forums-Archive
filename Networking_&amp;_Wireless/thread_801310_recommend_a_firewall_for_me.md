---
title: "recommend a firewall for me"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by codamNO on 2008-05-20
Hi,

I am in need of a firewall solution to go between a standard ADSL router and a wireless access point. The only traffic required outgoing from the network under the access point is http and ftp. I also require the ability to completely block traffic to certain defined hosts. If anyone has good experiences with a configuration tool for firewall on 8.02, give me some tips.

---

### Post by tamoneya on 2008-05-20
ubuntu already has a firewall built in call IPtables and it is very good.  All that you actually need is a way to configure it.  A nice GUI for this is firestarter:```
sudo apt-get install firestarter
```

---

### Post by jimv on 2008-05-20
Doesn't your router/gateway have a firewall built in?

---

