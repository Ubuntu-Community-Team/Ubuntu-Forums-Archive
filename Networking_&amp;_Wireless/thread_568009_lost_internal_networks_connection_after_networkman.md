---
title: "lost internal networks connection after networkmanager-pptp successful login"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by revenant_org on 2007-10-05
Today, I've decided to use networkmanager-pptp client instead of my own vpn script and w00t it worked out of the box. However, I have a small problem with routing to my internal networks ( I can't reach local network).

Each time I connect using the vpn connection I need to issue the following command to fix the routing problem:
```
 sudo route add -net 192.168.0.0/16 gw 192.168.64.1
```

Is there a way to do this using networkmanager ?

---

### Post by revenant_org on 2007-10-06
I've solved the problem by creating a script under **/etc/ppp/ip-up.d/ ** directory which adds my routing rules.:guitar:

---

