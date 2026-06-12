---
title: "Hardy x86_64: Large File Copies over the network cause System Freeze"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by garymansell on 2008-05-15
Hi,

I have just re-installed my Dell D630 laptop from Gutsy i686 to Hardy x86_64.

Now I find that copying large files (several GB) causes my system to freeze and become un-responsive. This did not happen in Gutsy i686.

It is a wired network connection (BCM5755M) and the hang occurs when copying the file by nfs v2 & v3 (both udp and tcp), ftp and scp. The files are vm images so vary from 6Gb to 20Gb.

I guess my system becomes un-responsive because my home dir is nfs mounted and once the system freezes, the whole network stack clogs up. If you look at top, the wait state reads 90%+ and vmstat shows several blocked processes.

It is possible sometimes to kill the copy process and the system comes back to OK again. Other times, the process will not die and a power cycle is needed.

There are no problems with generally working off of the nfs mounted home directory and day to day work - it is just the large file copies. It seems to be worse with v3 nfs than v2 - sometimes I can copy a 6Gb file with v2 nfs.

Any ideas as to how to fix or work around this issue much appreciated as it is driving me nuts.

Regards

Gary

---

### Post by arbuntoo on 2010-11-18
I have exactly the same problem and it's driving me crazy too -- during any serious network traffic the whole desktop becomes unresponsive. (Ubuntu 10.04 64-bit, wired ethernet, home directory on NFS)

Is there a bug number I can follow?

---

