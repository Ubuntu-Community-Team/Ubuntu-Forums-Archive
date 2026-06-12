---
title: "Setting up an ethernet bridge"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by bieber on 2007-06-26
I just made a crossover cable, and connected the spare NIC card on my desktop to the ethernet port on my laptop.  Now, neither adapter has lit up, I'm assuming because I haven't bridged the connections yet (hopefully, that or I screwed up the cable).  So, I've installed bridge-utils, how do I set up a bridge between the two ethernet connections, so the laptop can connect to my LAN transparently, and my desktop can still get access, too?  I haven't been able to find a decent guide, it seems, on the commands involved.

---

### Post by t4thfavor on 2007-06-26
Buy a hub, and a router. It will be alot better, and easier. 

to bridge a connection use.
 ```
sudo brctl addbr NameOfBridge
            sudo brctl addif NameOfBridge 1stInterface
            sudo brctl addif NameOfBridge 2ndInterface
            sudo brctl NAmeOfBridge stp on
```

---

