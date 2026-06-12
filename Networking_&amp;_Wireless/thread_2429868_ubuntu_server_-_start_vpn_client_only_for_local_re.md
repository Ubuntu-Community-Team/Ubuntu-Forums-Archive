---
title: "ubuntu server - start vpn client only for local resources"
date: 2019-10-24
forum: Networking &amp; Wireless
---

### Post by mauro_ita on 2019-10-24
Good morning everybody,

I've a small home intranet with a local router with ZEROSHELL. I've set up a VPN server with ZS and my idea is to use it only to connect remotely and to reach the local PCs but not to be used as default gateway.

In the ubuntu 18.04 desktop, I can set up a VPN client selecting the "Use this connection only for the resources of its network". Perfect and done!

How do I achieve the same on an ubuntu 18.04 server?

In other terms:
I need to set up a VPN client on a web server ubuntu 18.04 which is used only for the resources of the intranet

At the moment when I connect the web server with vpn, the connection is fine but the web server uses it as default gateway...

Cheers

---

### Post by Skaperen on 2019-10-25
if the VPN is not to be the default, are you intent on using it for just select address ranges?

---

