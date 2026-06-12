---
title: "open a port on gusty"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by kamasabi on 2007-11-12
after searching the forums and looking around online for about an hour and a half, I still can't get this figured out. -_-

All I want to do is open up port 443 on my file server.  It has already been forwarded on my router, but I need it opened on this computer.  Reason for doing this is I use a vpn software hamachi go access my computers from elsewhere, and it uses that port specifically.  I've tried the following commands, to no avail:

sudo iptables -A FORWARD -p udp -m -udp --dport 443 -j ACCEPT
sudo iptables -A FORWARD -p tcp -m -tcp --dport 443 -j ACCEPT

after doing this, it still doesn't want to open up.  

Any and all suggestions are much appreciated!!!!!!!!

Kama

---

