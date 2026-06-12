---
title: "ping works in only one direction"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by gjb1002 on 2008-09-09
Hi,

I have set up two machines running Kubuntu 8.04. One is a physical machine and the other a virtual VMware machine.

I'm trying to persuade them to talk to each other so I can set up NFS.

So I found their IP addresses via ifconfig and added them to each other's /etc/hosts file. Now if I ping the physical machine from the virtual machine (or mount directories via NFS), it works fine, but if I do it the other way round I get no response.

Am I doing the right things here? Most of the guides to NFS I've read seem to assume your machines can already talk to each other...

Thanks for the help.

Regards,
Geoff Bache

---

