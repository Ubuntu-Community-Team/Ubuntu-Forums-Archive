---
title: "configure nfs client"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by th1bill on 2008-04-22
I just installed DHCP3 by using the Synaptic Manager so that I can finally configure my client machine and I cannot out how to even start it.  There is no launcher and I have no commands.

---

### Post by brownknight on 2008-04-22
Are you trying to setup an NFS server and client? All you need to install for the client is portmap and nfs-common.

sudo aptitude install portmap nfs-common

---

