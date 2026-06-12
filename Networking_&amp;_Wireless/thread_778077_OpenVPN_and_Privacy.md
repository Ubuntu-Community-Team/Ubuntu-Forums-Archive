---
title: "OpenVPN and Privacy"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Banter on 2008-05-01
I use openvpn to connect to my work computer. I'm concerned that all my internet traffic may be routing thru my work's network. Is there a way to determine if this is the case? Also, is there a way to verify when I have disconnected an openvpn session?

I don't want to violate my work's computer policy!

---

### Post by superprash2003 on 2008-05-01
in most cases yes your internet traffic would go through your work's network while connected to vpn.

---

### Post by SpaceTeddy on 2008-05-02
check your default gateway. Openvpn has the choices of only routing specific network ranges, or do a full redirect over the VPN server.
check the output of this command
```
route -n
```
if your default gatway (0.0.0.0) is your vpn server, then you are being redirected. 

Another way to check this is to go to a [[COLOR="Blue"]website[/COLOR]]("http://www.whatsmyip.org/") that displays your external ip address. Check it when you are not connected, then connect the vpn, and check it again. If the IP changed, you are being redirected.

Yet Another way of finding out:
If your config for openvpn says "redirect-gateway" or the server says "push redirect-gateway" you are being redirected through your work.

---

### Post by Banter on 2008-05-17
thank you!

After connecting to the vpn, it seems like my IP address remained the same, but multiple destinations for 0.0.0.0 were given when I used route -n.

I'll keep poking around to see what I can find.

---

### Post by Paris Heng on 2008-05-17
Anybody use OpenSwan before? For the VPN?

---

