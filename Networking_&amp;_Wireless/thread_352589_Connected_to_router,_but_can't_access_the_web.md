---
title: "Connected to router, but can't access the web"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Max Carey on 2007-02-03
I've been trying to get my Netgear WG311T wireless card working in Edgy (6.10) for a few days now, and I've managed to get a connection to my router (all the info pops up on iwconfig).  But I can't connect to any external addresses...I tried pinging the router's IP, google, and several other addresses but all I got was "connect: Network unreachable".  I added the router's DNS settings to /etc/resolv.conf but still have the same problem.  I'm a linux noob and I have no idea what to do, I'd appreciate any help.  Thanks.

---

### Post by Max Carey on 2007-02-03
Finally solved the problem...I had my network key set as an ASCII instead of hex.

---

### Post by thug4life5599 on 2007-02-10
i have a similar problem please tell me what you did. i am completely new and i have no idea what to do

---

