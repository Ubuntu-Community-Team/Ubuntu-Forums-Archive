---
title: "PC not seen on  network"
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by boz_1812 on 2016-05-03
Hi,
Still very much a newbie, so not sure where to start with this problem.
I have 3 PCs on a lan all via ethernet, say PCs A, B and C

A is Ubuntu 14.04 LTS
B is also Ubuntu 14.04 LTS
C is Ubuntu 16.04 and acts as my file server.

Both A  and C appear on the network when they are booted, but B does not appear when it is booted.  
If I ping B from A or C it comes back as an unconnected host. 
Now, if I ping A from B, then B suddenly appears on the network if checked from A, but still not seen from C.  
If I then ping C from B, then all three machines are happy and appear on the network.  I can copy files, login with ssh, etc.  
In summary, B doesn't become available on the network until I do an outbound ping from it.
Thanks.

---

### Post by boz_1812 on 2016-05-14
Events have overtaken this problem.  Since I posted, the PC (B) that was not appearing on the network has developed further network problems.  Networking spontaneously disabled and I have not been able to turn it back on.  
Rather than waste more time, I've done a clean install of 16.04 LTS.  See how that goes.

---

