---
title: "does removing some partition from hard drive affects partition maming?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-04
Hi
Thank you for reading my post.
Can some one please let me know whether removing sda2 will cause the sda3 name to change?
for example when I remove sda1 and sda2, will it cause the sda3 to become sda1?

Thanks.

---

### Post by evilkastel on 2008-12-04
As far as i know it won't. I have partitioned my disk several times and the names remain unchanged. at ine time I had sda1 and sda6 only. So, i think it's a no.

---

### Post by vanadium on 2008-12-04
I think it is generally a yes. With current hardware, device names might even change between different boots. This is the reason why UUIDs are used today. UUIDs uniquely identify a partition unlike device names, which are assigned at boot time.

---

### Post by timcredible on 2008-12-04
depends on what you mean by 'remove'.  if you left that space on the drive, then no.  if you put the space that used to be sda2 into sda3, then yes.  however, if what you're really looking to do is make sure the partitions mount in the same place all the time, just label each partition, then they'll always mount in the same place no matter what.

---

