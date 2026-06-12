---
title: "Slow Local Network Transfer Speeds"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by wiredadex on 2008-08-18
Hi! As a foreword, if you need me to get you any more information about my issue, let me know how to get it for you please. 

I am attempting to dump a few large files onto a network share via a wired connection. The files are coming from my Ubuntu Machine to a local computer. The transfer speeds are abysmal. Currently waiting on a 33 hour transfer of roughly 2GB. I made the cable, and I thought that was causing the problem, but ping and trace route work just fine, with no dramatically slow speeds. 

I will be checking back on this tomorrow, thank you for your time.

---

### Post by wiredadex on 2008-08-19
I haven't made any progress as to determining why the transfer speeds are so slow. On the bright side, there's only 22 hours left on the transfer. Any ideas?

---

### Post by ModelM on 2008-08-19
In a terminal type:

ifconfig

and check the number of errors, overruns, collisions on the interface (probably eth0). A number greater than zero for any of these may be a big clue.

---

