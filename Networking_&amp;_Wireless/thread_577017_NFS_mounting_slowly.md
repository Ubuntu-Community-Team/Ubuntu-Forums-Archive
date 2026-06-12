---
title: "NFS mounting slowly"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by brenth on 2007-10-15
Hey all, I have duped a 7.04 drive and moved it identical machine. I have reset all the network settings, etc. But I am having an issue where my NFS servers are mounting really slowly. I looked on the forums and I have tried a number of fixes ( such as installing portmap and nfs-common). To no avail. It seems there is an issue with portmap, as when I try and restart it, it hangs for some time . I tried dpkg-reconfigure portmap with no luck.

Oct 15 15:38:04 ws-035 kernel: [ 2308.182341] portmap: server localhost not responding, timed out
Oct 15 15:38:04 ws-035 kernel: [ 2308.182363] RPC: failed to contact portmap (errno -5).

Anyone have any idea what the deal?

---

### Post by jinx099 on 2007-10-15
make sure you have portmap installed.

---

### Post by brenth on 2007-10-15
I have installed portmap and uninstalled portmap and dpkg-reconfigure portmap'ed to no avail

---

