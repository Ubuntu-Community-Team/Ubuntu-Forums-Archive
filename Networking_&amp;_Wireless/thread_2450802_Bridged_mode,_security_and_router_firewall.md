---
title: "Bridged mode, security and router firewall"
date: 2020-09-21
forum: Networking &amp; Wireless
---

### Post by Sceiron on 2020-09-21
Hi, u just got my ssh server up and running by setting one port on my router to "Bridged Mode".  As described in this post: [https://ubuntuforums.org/showthread.php?t=2450506](https://ubuntuforums.org/showthread.php?t=2450506)

What does "Bridged Mode" actually mean?
Because now i can connect over SSH to my ubuntu server using putty:  ipadress:port without having a "Firewall rule" (Port Forwarding) in my router. 

Does this have any affect on my security?

Tnx :):popcorn:

---

### Post by pcfan1234 on 2020-09-22
What router do you use?
Bridge mode is often used if the routing is disabled at all, but that can't apply here.
You have to differ between IPv6 and IPv4.
IPv4 uses NAT and therefore needs a port forwarding (static NAT table entry) to make a host reachable from the outside.
IPv6 doesn't use NAT. All IPv6 hosts that have a global IPv6 address (show your address to check that) and are therefore reachable from the entire IPv6 internet without port forwarding.

Next thing is a Firewall. It is completely separate from port forwarding and NAT. It can apply to IPv6 and IPv4.
You have to check NAT for IPv4 and the Firewall for IPv6 and IPv4.

EDIT: Now the security aspect:
Only hosts running server services (like FTP/HTTP server) are vulnerable via direct internet access.
If you for example have no Firewall rule for IPv6 and your server has only an FTP server running on port 21, is isn't possible to connect to port 80 if there is no service running.
They will get a message back that says them.

But in the case a hacker has access to the server, it makes sense to only allow the used port incoming in the SPI Firewall.
The hacker can install an HTTP server on port 80, but it isn't accessible from the outside if he doesn't manage to hack into the Firewall as well.

---

