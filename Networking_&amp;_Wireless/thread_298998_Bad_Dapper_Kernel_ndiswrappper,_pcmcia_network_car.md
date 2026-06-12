---
title: "Bad Dapper Kernel? ndiswrappper, pcmcia network card, toshiba, etc drops connections."
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by sekim27n2 on 2006-11-13
I was experiencing tons of dropped ssh, sftp, samba, gaim, etc, connections.  At first I thought it would be my router, wireless card, NP100 card, etc.

First thing I did was buy a new router, instead of using my friends.  That didn't solve the issue.

The next thing I did was remove WPA-SPK encryption.  That didn't solve the issue.

I tried changing between my two NP100 cards, which actually there are two different versions.  Version 2 is not autodetected, while version one is autodetected.  Version 1 uses pcnet_cs, while with version 2, pcnet_cs is attempted to be used.  This fails, and pcnet_cs must be disabled, and axnet_cs must be used instead.  However, this isn't a perfect solution.  I believe there may be some issues running version 2 with axnet_cs.  Anyways, I thought I would throw that in there for whomever needed that.

At any rate, my LAN connection still dropped connections, randomly.

I tried several different kernels, of which I mostly forget, the last one I tried was 2.6.15-27-686.  I also tried the kernel that came with Dapper Drake 6.06 Server CD, and the kernel that was downloaded with the apt-get upgrade.  My desktop that has the same kernel doesn't have an issues with dropped connections.](*,) 

I then thought that ndiswrapper must be the source of all my troubles.  So I removed that, but my NP100 still dropped connections.  I downloaded and installed the latest version of ndiswrapper, and my wireless lan still dropped connections.

I finally figured that the problem could be with the kernel.  So I downloaded linux-source-2.6.5 from apt-get and proceeded to compile a kernel and install it, which I have little to no experience doing.  Afterwards however, my connections were no longer dropped.  All my networking problems vanished.  So is it just me, or is there some type of bug in the kernel.

My Hardware:

ZyXel G-102 v2
NP100 V1
NP100 V2
96 MB Ram
Toshiba 2715X/DVD Laptop

I wonder if anyone else compiles there own kernel if it will solve the dropped connections, if anyone is experiencing this.


Note: The connection is dropped after allowing 12 hours more or less to pass, or trying to transfer 100 MB + files.  Also resolving DNS information would randomly stop working and start working again.

---

