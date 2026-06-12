---
title: "VPN connection failure..."
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by svivian on 2008-04-08
I'm trying to connect to a Windows VPN. On Vista, all I did was enter an IP address, connect, then enter my username/password.

I've set up PPTP on Ubuntu and set up a VPN connection, with the IP address in the Gateway field - is this right? Are there some other settings I need to tweak?

---

### Post by svivian on 2008-04-08
OK seemed like it was a firewall issue.

I can now connect to the VPN but a URL that should be working (and does on Windows) does not work. It's a local address with a port number, i.e. in the format: [http://name:1111/](http://name:1111/)

I can open the page on Windows but not on Linux.

---

### Post by superprash2003 on 2008-04-08
does it work when the firewall is disabled?

---

### Post by svivian on 2008-04-08
No. I need to disable the firewall in order to connect to the VPN. Once connected, the firewall (Firestarter, BTW) turns itself back on. But I can't get to the local server even after turning the firewall off again.

---

