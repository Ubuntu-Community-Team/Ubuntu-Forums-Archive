---
title: "Ubuntu Focal - How to persist &quot;ip link set ens224 up&quot;"
date: 2021-06-24
forum: Networking &amp; Wireless
---

### Post by amercer on 2021-06-24
20.04.2 LTS (Focal Fossa)

I just added a second wired ethernet to a Ubuntu 20 VM.  The adapter is ens224.  The adapter shows DOWN by default.  I can run a "ip link set ent224 up" and the adapter comes up perfectly.  I can not find a way to persist this setting besides using a startup script.

Thanks,
Allen

---

### Post by TheFu on 2021-06-26
netplan config file?

---

