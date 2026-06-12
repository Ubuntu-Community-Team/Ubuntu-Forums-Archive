---
title: "Routing 255.255.255.255 to other subnets?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by thomas79 on 2007-05-15
Hi

I have set up a Ubuntu machine as a router between two private subnets, 192.168.1.0 and 192.168.2.0 (with subnet mask 255.255.255.0). However, the application that I wish to run on top of the network uses broadcast to 255.255.255.255. It seems that such broadcast only reaches the subnet from which it is sent.

Does anybody know how to configure the router such that broadcast is routed to the other subnet?

Any help would be greatly appreciated!

PS - Setting up the machine as a mac bridge instead of a router would also do it for me, since I can then avoid subnetting. However, one of the networks is wireless and the other is an ethernet, and that doesn't seem to work either. I have posted this problem in another thread, where somebody had a similar problem ([http://ubuntuforums.org/showthread.php?t=434369]("http://ubuntuforums.org/showthread.php?t=434369")).

---

### Post by Synflux on 2007-05-15
Hi,

Different subnets are by definition different broadcast domains :confused: 

I'm not sure if you can do that?

Thanks,

Dave

---

