---
title: "cryptsetup on multiple partitions"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by pteri498 on 2009-01-02
I'm trying to encrypt my root and home partitions, and I've found a good tutorial on it using cryptsetup, but I can't find something that does more than a single partition.

I fear it would make more than one key for each parition to do it separately on each partition, and I'd really rather do a password just once to load both partitions. Is this possible?

---

### Post by hyper_ch on 2009-01-02
each encrypted device will have it's on password. However you could store the key to unlock other passwords on your root one...

You're trying to encrypt upon installation?

---

### Post by pteri498 on 2009-01-02
Not during installation. I have an 8.04 installation all done, with my boot, root, and home partitions separated. I'm  not sure how to do encryption upon install on this system, since I'm using an EEE PC with Ubuntu-EEE, and between it, the basic 8.04, and the basic 8.10 installations, ubuntu-eee 8.04 is the only one that works for me.

---

### Post by hyper_ch on 2009-01-03
doing a full encryption on an already installed system is not so easy.

---

