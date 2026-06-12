---
title: "network card not detected - Ubuntu desktop 6.06"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by ramo223 on 2007-04-20
Hi,

After Ubuntu desktop installation, my network card is not recognized by the system. I tried to compile the drivers for Asus P5L-VM e1000 driver but unsuccessful.
Can somebody tell me whether I should reinstall Ubuntu on a higher version (7.04)?

I'm a total newby here so please be nice with the instructions. :) 

Cheers

---

### Post by tripolitan on 2007-04-20
Depending on what you need out of your ubuntu distribution, 7.04 is pretty new. If you want stability, stick with 6.06 and install a supported NIC. or you could try your luck with 7.04.

---

### Post by phreaky- on 2007-04-21
I have the same problem does anyone give me a working solution. This is what I have done so far.

Installed 6.06 server and found out that the e1000 was not detected. So I downloaded the driver from the Intel site. To load is as a module And the README sais go into the /src/ dir from driver and do make install.

Then I get: Makefile:71: *** Linux kernel source not found.  Stop.

I did a search on it and found out that you had to download the kernel-source-version trough apt-get. Well there is nog kernel-source package :S Next I found another page ([http://ubuntuforums.org/showthread.php?t=70905](http://ubuntuforums.org/showthread.php?t=70905))
which stated i should apt-get install linux-tree. Guess what can't find that package either.

Then I tried to compile a new kernel 2.6.20 (which has support for e1000) using a few tutorials but can't find a tutorial which works for me? Is there a good tutorial on this forum? 

Then I found out 7.04 has a new kernel so I installed that and it works.

But I wanted to install a program and it won't compile anymore because of it seems not compatible with 7.04 :S

I'm really getting frustrated, every step I take leeds to a dead end! So back to 6.06.

Can anyone tell me how to fix it the PROPER way.

---

### Post by phreaky- on 2007-04-22
Ok I did  the following. 

Downloaded the e1000 driver from the intel support site.

When I do make install from source it sais I need the kernel source. So I installed it with:

**apt-get install linux-source-2.6.15**

I did a make install again and now I get an error from  the driver :S

*cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode*

Any idea on that?

In the mean time I will compile a new kernel. I found something that seems to work :D

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Ramo try that or install the 7.04 it has support for the intel driver. But for me glftpd did not work on 7.04

---

