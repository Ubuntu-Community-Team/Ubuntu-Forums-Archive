---
title: "IP help"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by ElevenWarrior on 2008-10-20
hi, I need to be able to open certain ports in Ubuntu, (hardy) and I can't figure out how
I have No firewall installed and I'm just stuck
thanks

---

### Post by sethvath on 2008-10-20
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

To revert it back 

sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

---

