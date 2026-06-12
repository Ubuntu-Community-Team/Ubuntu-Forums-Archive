---
title: "NFS mountd not running"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by StoneDragon on 2007-07-06
Hello. Does anyone else also have the problem, that upon starting of nfs-kernel-server (reboot or manual restart doesn't matter), the rpc.mountd is not being started? I can't see a cause, the init-script looks o.k. and if I manually start rpc.mountd, my nfs mounts work again flawlessly.

---

### Post by Mr. C. on 2007-07-06
Check your logs to determine if rpc.mountd was unable to start successfully the first time.

MrC

---

### Post by StoneDragon on 2007-07-06
I grepped my /var/log for "mountd" and did not find anything about starting problems, only the normal mount-messages (after I started it manually).
Also no NFS related messages about a problem.
This problem appeared about 5 days ago (+/- 2 days)... I did not see any nfs-related update in the dpkg logs.

---

### Post by Êisdur on 2007-10-01
I have the same problem. There seem to be no instance of nfsd running on my machine. The problem started two days ago and I have no clue about why this happened since it worked fine previously. Other machines I have with similar configuration do not show this problem. I'd appreciate any help on this.

---

