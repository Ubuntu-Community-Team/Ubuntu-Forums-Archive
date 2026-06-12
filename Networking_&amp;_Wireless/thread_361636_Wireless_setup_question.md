---
title: "Wireless setup question"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by bazar on 2007-02-14
I found an easy to read walkthrough for a g122/b adapter
setup for Dapper, it probably works for Edgy too I would 
think. 

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29)


I have a different brand adapter (buffalo) that has the same
chipset ralink2570.  I am assuming that I can use this 
walkthrough as well, am I incorrect in assuming so?


This walkthrough says "Please make sure you have the 
appropriate Kernel-Headers and GCC in place." but the
information on kernel setup the article links to is a broken
link.  After I install v. 6.10 would I have to do any further
setup to the kernel?

---

### Post by bnuytten on 2007-02-15
> **bazar said:**
> 
I have a different brand adapter (buffalo) that has the same
chipset ralink2570.  I am assuming that I can use this 
walkthrough as well, am I incorrect in assuming so?

No. You can use that walktrough as well. The chipset is the same, so you will use the same module(s). Doesn't matter much if it is made by one brand or another. Altough not in this aspect.

> **bazar said:**
> 
This walkthrough says "Please make sure you have the 
appropriate Kernel-Headers and GCC in place." but the
information on kernel setup the article links to is a broken
link.  After I install v. 6.10 would I have to do any further
setup to the kernel?
If they are not install, you can install these with "apt-get install gcc linux-headers-2.6.17-11-generic" depending on your current kernel of course. Use uname -r to find out.

---

### Post by bazar on 2007-02-17
> **bnuytten said:**
> No. You can use that walktrough as well. The chipset is the same, so you will use the same module(s). Doesn't matter much if it is made by one brand or another. Altough not in this aspect.


If they are not install, you can install these with "apt-get install gcc linux-headers-2.6.17-11-generic" depending on your current kernel of course. Use uname -r to find out.


Much thanks

---

