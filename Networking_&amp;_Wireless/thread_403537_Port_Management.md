---
title: "Port Management"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by tamird on 2007-04-07
Hi everyone

I'm new to Ubuntu, and have been having trouble using aMule on it. I'm getting random lowIDs, Kad reports that i'm always firewalled, etc.

I've followed the various guides that ask me to run:
sudo iptables -A INPUT -p tcp --dport <port #> -j ACCEPT

but still no success :(

my question, then, is two-fold:
1) does anyone have experience with similar problems and/or ways of fixing them?
2) is there a way for me to view the list of port block/allow policies so that i can review any changes i've made?

Thanks!

p.s. aMule problems not caused by router -- i'm sitting on DMZ.

---

### Post by zero-Q on 2007-04-08
&#304; had the same problem. and at last I could finish it. I had forwards my udp and tcp ports in NAT before solving. and when i removed kad-udp port from NAT, Kad status appeared "Kad:Ok". but while i m using Emule in Windows, I forwards the kad-upp port and there is no problem. why does Amule make kad-udp port forwarding as a problem?? is this a bug???

---

