---
title: "looking for a plug and play compatible External Hard drive"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by da protagonist on 2008-12-14
please excuse my extreme noobiness, I don't even know if this is the right place to post this, but I am using Hardy heron and am looking for a good company to buy a 1tb external hard drive that will work out of the box, preferrably under 200$.  I have bought two and had no end of trouble.  Thanks for your time and hope everybody has a great day

---

### Post by The ragman on 2008-12-14
I have used a WD 2tb MyBook, with no problems.

---

### Post by sleepingdragon on 2008-12-14
+1 for Western Digital, I have used a range of WD externals in my time - always Linux friendly.

---

### Post by kansasnoob on 2008-12-14
I've had no trouble with either Seagate or Western Digital.

All of my external drives (most of which are old drives popped into $10 cases) mount great with "pmount" installed.

It's in synaptic or:

```
sudo apt-get install pmount
```

Of course if any drive is formatted as NTFS I also install ntfsprogs (also in synaptic). An alternative is ntfs-config but I prefer ntfsprogs.

---

### Post by Kellemora on 2008-12-14
Hi Da P

Most Externals are pre-formatted for NTFS!

Therefore you need to install ntfs -3g and ntfsprogs I believe it's called, they are in Synaptic.

Externals under 200 gig sold by Western Digital require other software than just the drivers.  Couldn't even get them to work on windows boxes with the drivers until the software to run them was installed.
I've not had one bit of trouble with Maxtor or IOmega on Ubuntu, and not with Western Digitals 200 gig or over.

However, you can pop them out of the case and use them internally with no problems, so go figure, hi hi.........

TTUL
Gary

---

### Post by da protagonist on 2008-12-16
Thanks everyone.  Bought a WD drive and it works great

---

### Post by earthpigg on 2008-12-16
if its formatted to NTFS, you may want to consider formatting to ext2 (just linux compatible) or FAT32 (most compatible with everything, but fragments).

---

