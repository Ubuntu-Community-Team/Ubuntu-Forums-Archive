---
title: "How to open port"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by razvan7 on 2015-06-16
Hello . I have a torrent tracker and i need to open port 5500 for seeders ... How i can do this ? 
And after how i can check if is open ?

---

### Post by TheFu on 2015-06-16
a) the router needs to allow the connections - [http://portforward.com/english/routers/port_forwarding](http://portforward.com/english/routers/port_forwarding)
b) the computer needs to have a static IP on the LAN, so the router can forward ports to a known IP/port pair.
c) the computer needs to have a listener on the port (probably whatever tracker software you are running)
d) the firewall on the computer needs to NOT block the port - by default, Ubuntu doesn't block any ports.

So - which ever interface to the firewall you use will have a way to get a list of rules. gufw, ufw, iptables, whatever ... follow the directions for that software to see any firewall rules.

Clear as mud?

---

### Post by razvan7 on 2015-06-16
i have an VDS server... yes it has a static ip .... and now ?

---

### Post by TheFu on 2015-06-17
> **razvan7 said:**
> i have an VDS server... yes it has a static ip .... and now ?

Reread "d" and the last paragraph. Only you can determine the answer.

---

