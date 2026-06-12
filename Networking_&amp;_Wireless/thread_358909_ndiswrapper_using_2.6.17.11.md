---
title: "ndiswrapper using 2.6.17.11"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-02-11
I've been using ndiswrapper to configure my wireless network card with no problems for a couple of months, under kernal 2.6.17.10 (generic). On the last two boots, I've noticed I now have another kernal - 2.6.17.11 which is first in boot list. When this boots, I get a string of error messages along line of "error inserting ndiswrapper .......", and when system eventually boots, I have no wireless network connection - its just not there at all.
Rebooting with 2.6.17.10 works fine. Has anyone else seen this problem, and where did 2.6.17.11 come from - did I  get it via an upgrade??

---

### Post by spd106 on 2007-02-11
Yes, it's a new security update.

I suggest that you find whatever guide you used to set it up and go through it again. Chances are you will need to re-install a package, or upgrade to newer version. If you built ndiswrapper from source then you will need to rebuild it. The driver should not need to be changed.

---

### Post by glendavee on 2007-02-20
Thanks. Problem fixed. I downloaded latest version of ndiswrapper (1.37), then uninstalled the existing one and installed 1.37. Seems to have fixed the problem

---

