---
title: "Slow network connection wired and wireless"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2015-01-09
Hi, I'm using an Intel NUC as an HTPC with xbmcbuntu on it.  However both my wired and wireless connections are a third of the speed of a windows laptop using the same wifi in the house.

I had expected the wired connection to be faster. This is causing me streaming issues as the broadband isn't fast to start with.  

Please let me know if there is any more information I can provide to help diagnose the problem.

Cheers

---

### Post by SnoopFogg on 2015-01-09
Ok, so this fixed the wireless connection:

sudo apt-get update
sudo apt-get dist-upgrade

The wired is still poor but wireless is now fast enough to stream.

---

### Post by GhettoPastrami on 2015-01-10
This seemed to work for me. Thanks!

---

