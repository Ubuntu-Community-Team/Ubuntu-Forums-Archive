---
title: "Problem with freeradius and Ubuntu 7.10"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by codeb on 2008-03-16
Hi!

After installation freeradius server 2.0.2 on Ubuntu 7.10 with: 
./configure
./make
./make install
 
I got this message:

codeb@codeb-desktop:~$ radiusd x
radiusd: error while loading shared libraries: libfreeradius-radius-2.0.2.so: cannot open shared object file: No such file or directory
codeb@codeb-desktop:~$ 

how to fix that????????

One more question : which server version is tested and work OK with Ubuntu 7.10

P.S. sorry on bad English

---

### Post by koenn on 2008-03-16
Search for radius or freeradius in Synaptic Package Manager and install it from there, 
probably a lot easier.

---

