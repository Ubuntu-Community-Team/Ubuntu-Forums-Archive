---
title: "Portmap and nfs-kernel-server"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by davidcollins001 on 2007-04-02
Is there some sort of issue with portmap and nfs-kernel-server? When I try to restart nfs-kernel-server I get [ok] printed to the terminal telling me that everything has been restarted ok and all is working as should be, but when I look in /var/log/messages there is an error:

"RPC: failed to contact portmap (errno -5)"

I have checked that portmap is running (rpcinfo -p) and it seems to be up fine. Are there any local tests I can do to make sure it is working properly. I installed it with "sudo apt-get install portmap"

I am running this from a live version of ubuntu edgy.

---

