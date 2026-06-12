---
title: "networking"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by nnamdi on 2009-06-25
pls i need a good ip tunneling application for ubuntu

---

### Post by antikristian on 2009-06-26
depends on what you want

VPN tunnels:
NetworkManager-pptp - supports pptp through Network manager
NetworkManager-openvpn - supports the openvpn standard
NetworkManager-vpnz - supports cisco vpns, ipsec (i belive) ++

SSH-port-tunneling
Just use openssh to create a port tunnel, use the -L for a normal tunnel, or -R -L for reverse tunnel. Howtos [here]("http://lmgtfy.com/?q=ssh+tunnel");-D or [here]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html")

If it's an actual IP Tunnel you want, [This]("http://blog.kovyrin.net/2006/03/17/how-to-create-ip-ip-tunnel-between-freebsd-and-linux/") might work

---

