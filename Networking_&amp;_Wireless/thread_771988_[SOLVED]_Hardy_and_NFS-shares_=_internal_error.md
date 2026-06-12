---
title: "[SOLVED] Hardy and NFS-shares = internal error"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Archmage on 2008-04-28
When I'm trying to mount my (in Gusty working NFS-share) in Hardy I'll get this error message:

mount.nfs: internal error

On the same time my five Gusty-machines (with the same settings) connecting flawless to this share.

Does this now need an other package or could this be a firewall-problem? I have blocked all unnessacary ports on my server. Maybe in Hardy the machine wants to connect on an other port?


Here is a bug-report from someone else that seems to have the same problem:

[https://bugs.launchpad.net/ubuntu/+bug/213444](https://bugs.launchpad.net/ubuntu/+bug/213444)

---

### Post by gareth_005 on 2008-04-28
I just setup my nfs mounts in hardy, also got an error but then I selected nfs-common in synaptic, accepted the dependencies and installed.

After that I ran mount again and all is well.

---

### Post by Archmage on 2008-04-29
Solved it. Restarting the services didn't help, but after I did restart my server it works now.

---

