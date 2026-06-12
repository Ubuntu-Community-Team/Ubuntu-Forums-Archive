---
title: "[SOLVED] Reroute Port"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by gali98 on 2008-11-15
Hey all!

Okay so I am pretty sure this is possible. So I have an ssh server running on a computer(192.168.0.100) behind a router. The router forwards port 8000 on the outside to my computer on the inside). Isn't there a way to set on the Ubuntu machine for it to forward 8000 to 22 (ssh).
My guess would be to use iptables, but I have no experience and no idea how it works. Basically I need the incoming port on the computer (8000) to be routed in the computer to port 22.
If any of you net gurus could give me a hand, I would appreciate it!
Thanks,
Kory

Note: And yes, I know I could just set the ssh server to run on 8000, but I would rather do it this way, plus I want to learn to use iptables. :)
tx2

---

### Post by gali98 on 2008-11-17
Hey all...
So I figured out how to do and want to share so anyone else who needs it can know how.
 ```
sudo iptables -t nat -A PREROUTING -p tcp --dport [incoming port] -i [device] -j REDIRECT --to-port [port]
```
Note: you don't need the brackets..
Where incoming port is the one that you want to reroute and port the port that you want it routed to. Device is just that. So an example would be;
```
 sudo iptables -t nat -A PREROUTING -p tcp --dport 60000 -i eth1 -j REDIRECT --to-port 22
```
This would route port 60000 to port 22 on eth1...
Hope this helps!
Kory

---

