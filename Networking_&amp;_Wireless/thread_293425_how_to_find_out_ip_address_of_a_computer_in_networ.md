---
title: "how to find out ip address of a computer in network"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by afx on 2006-11-05
my computer is connected to a big local area network and i was wondering how to find out ip address of some computer with shares on the windows network...

hope u help me! tnx

---

### Post by spd106 on 2006-11-05
You could use **smbtree** from a terminal to find the hostnames and maybe install winbind to allow netbios name resolution. There are are other threads on doing this with winbind around the forum.

Or as a fall back you could try a scanning tool such as nmap to find hosts with the ports open for the services you want, but you will need clearance from the network admin to do this. Sometimes you can ping the network broadcast address, though this can cause a storm on a large network.

---

### Post by spd106 on 2006-11-05
Oh yeah, I forgot to mention that if you know the hostnames you might be able to use **net lookup hostname** to find the ip address and **arp** will show the ip addresses of local network hosts you have recently connected to

---

### Post by afx on 2006-11-05
**net lookup hostname** solved the problem.
i owe you one man! thanks a lot! cheers!

---

