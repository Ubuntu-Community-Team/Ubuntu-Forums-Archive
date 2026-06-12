---
title: "What are the advantages of transferring from WUBI to normal dual boot?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by suitedaces on 2009-03-03
And do they outweigh the difficulties that a partition-phobe like myself would have?

---

### Post by philinux on 2009-03-03
According to the faq's


> What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate.

[edit] what's the phobia like?

---

### Post by stchman on 2009-03-03
> **suitedaces said:**
> And do they outweigh the difficulties that a partition-phobe like myself would have?

A WUBI install is left prone to Windows viruses (when running Windows) and NTFS file fragmentation.  Go with a traditional dual boot and use EXT3.

---

### Post by philinux on 2009-03-03
stchman is dead right. Although the wubi install cant run a windows virus, if your windows gets infected you could loose you wubi too as it's part of the file system.

Wubi is really meant to test the water with the os. As a live cd can be sluggish wubi gives you a better feel as to how it would run.

---

