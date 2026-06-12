---
title: "Speedtouch 330 USB not working after upgrade"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Akke on 2006-09-19
My Alcatel Speedtouch 330 was working fine until I upgraded to the new kernel 2.6.15-27-386 this morning.
I now get messages saying speedtch_test_sequence fails.
Anyone knows what's going on?

---

### Post by Akke on 2006-09-20
Solved.

I seemed to have an old version of the speedtouch drivers speedtch-1.bin and speedtch-2.bin. Up to kernel 2.6.15-26-386 that didn't cause any trouble. Renewed them and the problem is gone.

---

