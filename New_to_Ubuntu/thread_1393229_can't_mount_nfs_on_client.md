---
title: "can't mount nfs on client"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by suhe on 2010-01-29
hello guys..
i wanna ask you something ..why my nfs can't mount on my client,,
but the cnfiguration on the server i thought was correct..
i have configured /etc/exports
i have configured fstab
i have restarted /etc/init.d/nfs-kernel-server

but it's still not working...
please...help me to solve this..
thank you all...
God BLess

---

### Post by overdrank on 2010-01-29
Hi and welcome, Moved to Absolute Beginner Talk

---

### Post by lijcam on 2010-01-29
Try this on the server side.

```
sudo exportfs -rv
```Then try mounting on the client side.

---

