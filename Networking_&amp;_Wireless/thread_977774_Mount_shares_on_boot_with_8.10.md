---
title: "Mount shares on boot with 8.10?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by agerrius on 2008-11-10
Hi,

Since upgrading to Ubuntu 8.10 I have a problem with the shares that I have in the fstab file. Before I installed the upgrade they were automatically mounted when I booted the PC, but now that does not happen anymore. If I use

```
sudo mount -a
```

everything is fine again, but it is a bit annoying to do that manually all the time. Another difference I notice is that after I login I see a message that my wired network has been established. So it looks like the network is not up before (that might be why the mount fails?).

Do other users have the same experience or does somebody has a tip on how to solve this? Thanks,

Arno

---

