---
title: "Strange network performance issue"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2015-10-14
Got strange network performance issue
I have a Ubuntu 14 LTS server which has local disk , and runs samba and virtual box.
There are also two NAS devices mounted as CIFS (no NFS support) and Ecryptfs (with or without encryption the performance is not much different)

when the ubuntu server read or writes to the NAS devices i get approx 25 mbs (BITS) VERY SLOW

When a windows 10 client accesses a samba share on the server (from local disk on the server) i get throughput of around 770 mbs
When the same windows 10 client copies a file from the samba on the ubuntu sever to the the NAS devices i get around 300 mbs. 
When the window 10 client  accesses the nas devices directly i get approx 700-800mbs
When a win7 client running in a virtualbox instance on the ubuntu server i get around 250 - 300 mbs

So the network is ok, the ubuntu server can transfer data at a good speed.

It looks like CIFS mounts from ubuntu. Whilst i would expect a performance hit mouning cifs on ubuntu I would not expect to loose over 700mbs.

Any ideas?

---

### Post by Bucky Ball on 2015-10-14
*Thread moved to **Networking & Wireless**.*

You may have better luck here.

---

