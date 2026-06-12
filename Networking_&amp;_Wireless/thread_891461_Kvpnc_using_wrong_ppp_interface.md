---
title: "Kvpnc using wrong ppp interface"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by syd2o2 on 2008-08-16
I'm using Kvpnc to connect to a vpn network using pptp. The first time I started it, and configured a connection, it used ppp0 interface and I was successfully connected to my vpn network. 
Unfortunately, since then, kvpnc started trying to use ppp1 interface for connections. And since my internet connection is on ppp0, it can't connect.
If I go into profile-network-general I can see that network device is set to ppp1, but the option is greyed out and I can't change it.
Can anybody help me? I need to set/force kvpnc to use ppp0 interface for connections.

---

