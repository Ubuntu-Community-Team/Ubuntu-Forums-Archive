---
title: "Partition sizes"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-16
I recently reshuffled the size of my partitions because I was running out of space. Currently I have:

root = 15GB (19% used)
home = 10GB (3% used)

I'm concerned these may be too small, or I didn't allocate enough space in the right place. As I understand it, all apps get installed to the root partition, and therefore that should be the biggest. The home partition is for user settings, personal docs, etc.

Now how can I clean out some space, other than emptying my trash and running apt-get with clean, autoclean and autoremove?

---

### Post by kk0sse54 on 2009-03-16
While all applications are installed to your root partition generally your /home with be larger if you put in on a seperate partition since User data like Music, Videos, Documents etc etc tends to take up a lot more space.

---

