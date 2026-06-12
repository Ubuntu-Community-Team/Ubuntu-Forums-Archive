---
title: "Re-partitioning"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by eXe. on 2011-08-08
Ok, so I have Ubuntu 11.04 (I love it), and backtrack 5 (not so much). I wanted to re-partition my hard drive so I only had Ubuntu 11.04 and it took up the entire disk. When I go into Disk Utility and select my hard drive I can clearly see Ubuntu 11.04. But on the right there is SWAP space, and all kinds of extra stuff. Do I delete all of these? After this what do I do to re-partition my hard drive?
I want to re-partition without re installing Ubuntu.
Thanks
-eXe

---

### Post by Gryllida on 2011-08-08
Ubuntu uses root and swap partitions for itself.

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

If you want to remove another distro, you don't need to remove Ubuntu's partitions - kill only the partitions used by the other system, and format them as needed.

Please let us know if this resolves the issue.

---

### Post by haqking on 2011-08-10
> **eXe. said:**
> Ok, so I have Ubuntu 11.04 (I love it), and backtrack 5 (not so much). I wanted to re-partition my hard drive so I only had Ubuntu 11.04 and it took up the entire disk. When I go into Disk Utility and select my hard drive I can clearly see Ubuntu 11.04. But on the right there is SWAP space, and all kinds of extra stuff. Do I delete all of these? After this what do I do to re-partition my hard drive?
I want to re-partition without re installing Ubuntu.
Thanks
-eXe
#

post a image of your partitions before deleting anything so we can advise better.

by the way, Backtrack 5 is not a distro designed for general everyday desktop use, it is collection of Pen testing tools for security auditing which is why you probably dont like it.

---

