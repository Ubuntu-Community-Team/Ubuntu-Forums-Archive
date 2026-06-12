---
title: "How to block outgoing UDP packets?"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by c4242504 on 2014-01-12
Long story shot, I want to stop UDP packets sent from my machine to the internet.
How do I do that?
 Thanks in advance.

---

### Post by The Cog on 2014-01-12
You need to know a port number to block, as you really do not want to block all UDP. Blocking all UDP would kill your ablilty to perform DNS lookups.

If something is trying to make outgoing connections, it may use a randon source port, but the destination port will be fixed, so it is probably the destination port you want to block. This command will block outgoing UDP to port 1234:
```
sudo iptables -I OUTPUT -p udp --dport 1234 -j DROP
```

But why not track down and stop the process that's sending them in the first place? Fix the cause, not the symptom.

---

