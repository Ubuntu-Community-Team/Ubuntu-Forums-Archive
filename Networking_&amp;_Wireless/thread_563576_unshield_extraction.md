---
title: "unshield extraction"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by svenkatesan on 2007-09-30
Hi
I am trying to install windows driver for my USB wireless disk in Ubuntu 7.04 (2.6.20).
Despite the installation disk comes with  linux driver,its not able to install.
I would like make this disk working with ndiswrapper but now I struck with this driver installation.
From the cd I extract the data1,data1.hdr and data2.cab file.(with cabextract)
Since all these are under nstallshield compression,I could extract only with unsheild.
I install unshield and try to extract with foll. command
[COLOR="Red"]**unshield -d /tmp/x data1 or data2.cab**[/COLOR]
nothing happens.No error at all.
Pl  help.
Anyother way to go around?
Thanks.
I m using this adapter GW-US54GXS- using chipset 1211.

---

### Post by TheBenny on 2007-10-15
you have a syntax error, I was just having the same problem.
unshield -d /tmp/ x data1.cab

---

