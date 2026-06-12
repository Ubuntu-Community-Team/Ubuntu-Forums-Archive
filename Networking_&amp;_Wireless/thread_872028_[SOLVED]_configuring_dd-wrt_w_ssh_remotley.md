---
title: "[SOLVED] configuring dd-wrt w/ ssh remotley"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2008-07-27
on my WRT54GL v1.1 router with v24 std dd-wrt flashed I have enabled sshd and am using a rsa key to access my router. I can access the router from abroad by typing: ```
ssh -p routers-chosen-sshd-port root@routers-external-ipadress
```

I am using a rsa key- everything works fine except what I get is a cli for the router. I would like to edit port forwarding options to allow me to access a server on the other side of the router. I don't want to leave this port open normally due to security but I want to be able to open it from the outside. Is there a file I can edit in my router somewhere to port forward a certain port to a certain internal ip adress and then enable/disable it?

---

### Post by bcn17 on 2008-07-29
I figured it out - If you are wondering use the iptables command. It has numerous ways to edit port forwarding.

---

