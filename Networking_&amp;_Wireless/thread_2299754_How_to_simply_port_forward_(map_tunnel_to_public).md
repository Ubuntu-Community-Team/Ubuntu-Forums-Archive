---
title: "How to simply port forward (map tunnel to public)?"
date: 2015-10-21
forum: Networking &amp; Wireless
---

### Post by andrew102 on 2015-10-21
Hello,

How may I simply enable a port on the tun0 to be NAT'd to the public IP ?

i.e. If I have a server with public IP (eth1) 100.100.100.100 and tun0 IP 10.0.0.1. Then I want, say, port 80 at IP 10.0.0.2 (a different device) accessible from this devices public IP 100.100.100.100 ?

I have UFW installed and enabled.

---

### Post by michi1983 on 2015-10-21
Hi,

which IP has your Ubuntu machine?
Which device has the 10.0.0.2?
Which device establishes the internet connection of your ISP? A Router?

---

