---
title: "Problems with Remote Desktop/Interfaces"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by jolindsey on 2011-01-07
Currently running Ubuntu 10.04 LTS.
Currently have 4 interfaces lo, eth0, eth5 and eth6.

Trying to get Remote Desktop to run on eth0. When we select System>Remote Desktop, sometimes it tells us that the interface that will be used is localhost and other times it says the address for eth6.

Are we missing something in the interfaces?

Any help would be greatly appreciated.

Thanks

---

### Post by Old_Grey_Wolf on 2011-01-07
If I enable remote desktop, it will give me the IP address of the computer or it will give me the DNS resolved name for the computer. 

You may want to look at the DNS lookup for the computer. The "localhost" suggests that here is no DNS setup or the computer is not connected to the network.

---

