---
title: "[SOLVED] installed firestarter and can't access windows shares...I can't even see the"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by jflaker on 2008-03-24
I had access to windows shares up until I installed firestarter.....now I can't even see any of the other systems on the network.

Any ideas?

---

### Post by LeoSolaris on 2008-03-25
Unless you need specific control over your ports, you don't actually need firestarter. FS is a user front end for iptables, which is running by default. It allows you more control of the firewall that is integrated into the system. At least that is how it has been explained to me. I was a little nervous about not having a firewall at first and had that issue with firestarter, too. I ended up removing firestarter, which returned functionality to my shared folders. I tested the firewall out by using one of the test sites on the web. Iptables worked without the gui front end, at least in my tests.

---

### Post by jflaker on 2008-03-25
I ended up removing firestarter and I did get functionality returned.  

I wanted to allow remote from another PC in the house, but it wasn't working and the result was a loss of other networking functionality.........

Thanks for the input

---

