---
title: "Unknown symbol in module in kernel generic"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by jacum on 2007-07-20
Good morning.

I have written a kernel module, really they are 6 modules each of those 

EXPORT_SYMBOLs one for the other.

I always compiled and modprobed the software inside debian and slackware distributions
with VANILLA kernels downloaded from kernel.org.

I recently installed Ubuntu 7.04.

It runs the generic kernel installed by the installation setup.

My modules compile correctly 

make

make install

but when i do a modprobe my_module it gives 

unknown symbol errors 

for the symbols needed by the modules.

I underline that if i rebuild THE SAME kernel, and install the SAME stuff,
it gets correctly inserted.

Is this a solvable issue in your opinion??

How can i successfully install the module in the default kernel, without 
recompiling it?

Thanks a lot

Giacomo S. italy

Giacomo S.
[http://www.giacomos.it](http://www.giacomos.it)

- - - - - - - - - - - - - - - - - - - - - -

IPFIREwall ([http://www.giacomos.it/ipfire](http://www.giacomos.it/ipfire)) viene presentato
all'Universita` degli Studi di Udine, il 28 ottobre, in occasione del
Linux Day 2006:
[http://iglu.cc.uniud.it/linuxday](http://iglu.cc.uniud.it/linuxday)

---

### Post by anubhavrocks on 2007-07-20
have you tried insmod'ing your modules manually and see where it fails

---

