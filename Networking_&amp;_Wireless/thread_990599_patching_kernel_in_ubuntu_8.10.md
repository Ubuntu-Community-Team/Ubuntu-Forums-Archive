---
title: "patching kernel in ubuntu 8.10 ?????"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by sanosuke86 on 2008-11-22
anybody help me????

root@dheen-desktop:/usr/src/linux# ls
arch CREDITS drivers init kernel MAINTAINERS net scripts usr
block crypto fs ipc lib Makefile README security
COPYING Documentation include Kbuild linux-2.6.16.62 mm REPORTING-BUGS sound
root@dheen-desktop:/usr/src/linux# patch -p1 < /usr/src/KERNEL_2.4.19_MPLS172.patch
(Stripping trailing CRs from patch.)
patching file drivers/net/ppp_generic.c
Hunk #1 FAILED at 57.
Hunk #2 FAILED at 282.
Hunk #3 FAILED at 296.
Hunk #4 FAILED at 314.
Hunk #5 FAILED at 328.
5 out of 5 hunks FAILED -- saving rejects to file drivers/net/ppp_generic.c.rej
(Stripping trailing CRs from patch.)
patching file include/linux/if_arp.h
Hunk #1 FAILED at 83.
1 out of 1 hunk FAILED -- saving rejects to file include/linux/if_arp.h.rej
(Stripping trailing CRs from patch.)
patching file include/linux/if_ether.h
Hunk #1 succeeded at 65 with fuzz 1 (offset 4 lines).
(Stripping trailing CRs from patch.)
patching file include/linux/mpls.h
(Stripping trailing CRs from patch.)
patching file include/linux/netdevice.h
Hunk #1 FAILED at 329.
1 out of 1 hunk FAILED -- saving rejects to file include/linux/netdevice.h.rej
The next patch would create the file include/linux/netfilter_ipv4/ipt_MPLS.h,
which already exists! Assume -R? [n] y
(Stripping trailing CRs from patch.)
patching file include/linux/netfilter_ipv4/ipt_MPLS.h
(Stripping trailing CRs from patch.)
patching file include/linux/ppp_defs.h
Hunk #1 FAILED at 74.
1 out of 1 hunk FAILED -- saving rejects to file include/linux/ppp_defs.h.rej
(Stripping trailing CRs from patch.)
patching file include/linux/rtnetlink.h
Reversed (or previously applied) patch detected! Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 FAILED at 253.
Hunk #2 FAILED at 283.
2 out of 2 hunks FAILED -- saving rejects to file include/linux/rtnetlink.h.rej
(Stripping trailing CRs from patch.)
patching file include/net/dst.h
Hunk #1 FAILED at 10.
Hunk #2 FAILED at 65.
2 out of 2 hunks FAILED -- saving rejects to file include/net/dst.h.rej
(Stripping trailing CRs from patch.)
patching file include/net/ip.h
Hunk #1 FAILED at 162.
1 out of 1 hunk FAILED -- saving rejects to file include/net/ip.h.rej
(Stripping trailing CRs from patch.)
patching file include/net/ip_fib.h
Reversed (or previously applied) patch detected! Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 FAILED at 29.
Hunk #2 FAILED at 53.
Hunk #3 FAILED at 82.
Hunk #4 FAILED at 119.
4 out of 4 hunks FAILED -- saving rejects to file include/net/ip_fib.h.rej
(Stripping trailing CRs from patch.)
patching file include/net/mpls.h
(Stripping trailing CRs from patch.)
can't find file to patch at input line 838
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr linux-kernel/net/Config.in mpls-kernel-fixes/net/Config.in
|--- linux-kernel/net/Config.in Sat Aug 24 00:22:21 2002
|+++ mpls-kernel-fixes/net/Config.in Tue Nov 12 20:00:45 2002
--------------------------
File to patch: /usr/src/KERNEL_2.4.19_MPLS172.patch
patching file /usr/src/KERNEL_2.4.19_MPLS172.patch
Hunk #1 FAILED at 81.
1 out of 1 hunk FAILED -- saving rejects to file /usr/src/KERNEL_2.4.19_MPLS172.patch.rej
(Stripping trailing CRs from patch.)
patching file net/Makefile
Hunk #1 FAILED at 19.
1 out of 1 hunk FAILED -- saving rejects to file net/Makefile.rej
(Stripping trailing CRs from patch.)
patching file net/core/dst.c
Reversed (or previously applied) patch detected! Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 succeeded at 23 with fuzz 2 (offset 4 lines).
Hunk #2 FAILED at 166.
1 out of 2 hunks FAILED -- saving rejects to file net/core/dst.c.rej
(Stripping trailing CRs from patch.)
patching file net/core/neighbour.c
Hunk #1 FAILED at 952.
1 out of 1 hunk FAILED -- saving rejects to file net/core/neighbour.c.rej
(Stripping trailing CRs from patch.)
patching file net/ipv4/af_inet.c
Hunk #1 FAILED at 116.
Hunk #2 FAILED at 936.
2 out of 2 hunks FAILED -- saving rejects to file net/ipv4/af_inet.c.rej
(Stripping trailing CRs from patch.)
patching file net/ipv4/fib_semantics.c
Reversed (or previously applied) patch detected! Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 succeeded at 193 with fuzz 2 (offset 43 lines).
Hunk #2 FAILED at 282.
Hunk #3 FAILED at 527.
Hunk #4 FAILED at 544.
Hunk #5 FAILED at 731.
Hunk #6 FAILED at 751.
5 out of 6 hunks FAILED -- saving rejects to file net/ipv4/fib_semantics.c.rej
(Stripping trailing CRs from patch.)
patching file net/ipv4/ip_output.c
Hunk #1 FAILED at 113.
1 out of 1 hunk FAILED -- saving rejects to file net/ipv4/ip_output.c.rej
(Stripping trailing CRs from patch.)
can't find file to patch at input line 999
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -uNr linux-kernel/net/ipv4/netfilter/Config.in mpls-kernel-fixes/net/ipv4/netfilter/Config.in
|--- linux-kernel/net/ipv4/netfilter/Config.in Sat Aug 24 00:22:28 2002
|+++ mpls-kernel-fixes/net/ipv4/netfilter/Config.in Tue Nov 12 20:00:46 2002
--------------------------
File to patch: /usr/src
patch: **** File /usr/src is not a regular file -- can't patch
root@dheen-desktop:/usr/src/linux# patch -p1 < /usr/src/DSMPLS+IP.patch
missing header for unified diff at line 3 of patch
(Stripping trailing CRs from patch.)
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- net/sched/sch_dsmark.c Fri Dec 21 18:42:06 2001
|+++ sch_dsmark.c Tue Jul 16 17:52:15 2002
--------------------------
File to patch: /usr/src/DSMPLS+IP.patch
patching file /usr/src/DSMPLS+IP.patch
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 195.
2 out of 2 hunks FAILED -- saving rejects to file /usr/src/DSMPLS+IP.patch.rej
root@dheen-desktop:/usr/src/linux#

---

