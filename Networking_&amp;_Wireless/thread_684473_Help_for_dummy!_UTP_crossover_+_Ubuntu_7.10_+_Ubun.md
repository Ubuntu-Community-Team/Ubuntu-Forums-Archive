---
title: "Help for dummy! UTP crossover + Ubuntu 7.10 + Ubuntu 7.10"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by arms on 2008-02-01
Guys, I don't have so much time so I hope for help here.

I need from one Ubuntu 7.10 PC (the 1st computer) copy files to another Ubuntu 7.10 PC (the second computer). Data in the first computer are on two separate partitions with file system NTFS.  Those machines are connected via UTP crossover cable. I managed to setup remote desktop (so connection is ok), however I did not find a solution with shared folders. I have only basic knowledge of networking and Linux, so step-by-step and non-command line instructions would be appreciated.. I think it's a very easy task for a professionals :)

---

### Post by hahahan on 2008-02-01
Use synaptic packetmanager to install openssh-client and openssh-server on both machines.
Then you can browse both machine's with nautilus by entering ssh://user@Ipaddress as location.

Regards.

---

