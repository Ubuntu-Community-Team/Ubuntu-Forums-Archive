---
title: "Installing OpenArena"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by MGN001 on 2009-09-23
I'm installing OpenArena on Ubuntu, at least I'm trying to.  When I start the package installer, it says Status:  Error: Failed to satisfy all dependencies (broken cache).  I took a computer repair course and I saw the Broken Cache message and thought 'well, ****', but my computer works fine otherwise.  The only problem I'm having is installing the damn package.  Please help.

---

### Post by nhasian on 2009-09-23
i think your mixing up your caches.  cache on the CPU or hard disk's circuit board is different than the cache on a filesystem :)

---

### Post by inobe on 2009-09-23
> **MGN001 said:**
> I'm installing OpenArena on Ubuntu, at least I'm trying to.  When I start the package installer, it says Status:  Error: Failed to satisfy all dependencies (broken cache).  I took a computer repair course and I saw the Broken Cache message and thought 'well, ****', but my computer works fine otherwise.  The only problem I'm having is installing the damn package.  Please help.


welcome to the forums

go to synaptic and click fix broken packages

---

### Post by 3rdalbum on 2009-09-23
```
sudo apt-get update
```

Should, I believe, fix the broken package cache.

---

