---
title: "Wireless broken in linux 2.6.29-7"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Ambush Commander on 2008-11-28
Hello all,

I am seeing a curious problem on by Dell Vostro 1400 with a Broadcom Corporation BCM4312 802.11b/g wireless card. Namely, when I boot Ubuntu using the newly minted 2.6.27-9 kernel, my wireless does not work; however, when I boot with the older 2.6.24-21 kernel, my wireless works normally (2.6.27-7 kernel panics far too often to be useful).

Is there anything I can do to fix this now, or do I just have to wait until a new Linux kernel is released?

---

### Post by asgard_command on 2008-11-29
I just update from 2.6.29-7 to 2.6.29-9 and broke my wireless had to boot with the older kernel so also interested to hear if others had this problem.

---

### Post by Ambush Commander on 2008-11-29
So, it looks like they released a new Linux Kernel. With any luck this issue will be fixed. Installing now!

---

### Post by lswb on 2008-11-29
The 2.6.24.xx kernels are used in hardy, 2.6.27.xx in intrepid. If you try to install the 2.6.27 kernels in hardy you will also need all the modules and some probably some other componenets for the matching kernel. What version and kernel are you actually running?

---

### Post by Ambush Commander on 2008-11-29
I'm running Intrepid Ibex, huh. My archive.canonical.com repos is still pointing to hardy, but all of my other software sources are intrepid. I suppose this means I should reboot with the new Linux kernel, and use an ethernet cable to update by software packages?

---

### Post by Ambush Commander on 2008-11-29
It looks like the recent updates to the kernel fixed the problem. Now lets hope it doesn't kernel panic like the previous version did. :-)

---

