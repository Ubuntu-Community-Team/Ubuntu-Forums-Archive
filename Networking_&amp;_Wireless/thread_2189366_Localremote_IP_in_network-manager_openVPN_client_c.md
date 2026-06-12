---
title: "Local/remote IP in network-manager openVPN client config"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by HittingSmoke on 2013-11-21
I'm setting up a VPN connection to a router running an OpenVPN server. It's a pre-shared key setup and I can get the server to respond but I know don't what I'm supposed to put in the fields labeled "Local IP" and "Remote IP". I don't know if this is referring to the external IP of the local machine and the router, internal network IPs, or what? The server will not connect when they're left blank. Using external IPs gives me an error about local/remote IPs not allowed to be the same as ifconfig IPs.
What IPs am I supposed to enter into these fields?

---

### Post by bashiergui on 2013-11-24
[http://openvpn.net/index.php/access-server/docs/quick-start-guide.html](http://openvpn.net/index.php/access-server/docs/quick-start-guide.html)

---

### Post by HittingSmoke on 2013-11-24
> **bashiergui said:**
> [http://openvpn.net/index.php/access-server/docs/quick-start-guide.html](http://openvpn.net/index.php/access-server/docs/quick-start-guide.html)

I don't see any information at that link which answers my question.

---

### Post by bashiergui on 2013-11-27
Local IP would be your machine's IP. The remote IP would be the IP of the VPN server.

If you use DHCP on your local machine then you will need to reserve an IP on your router.

---

