---
title: "[SOLVED] Samba Performance tweaking to a Macbook vs. Windows through DLink DIR-655"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by whatever69 on 2008-10-05
Hi Everyone,

I've been happy with my setup the last 2 years, and I just bought a new router - D-Link DIR-655.

I was connecting wireless and wired and noticed the following before tweaking:

Wired 100 Mbps
==============
Macbook to Ubuntu: 56 Mbps
Windows to Ubuntu: 72 Mbps

Wireless N (Connected at 130 Mbps ... Apple's fault)
====================================================
Macbook to Ubuntu:  20 Mbps
Macbook to Windows: 44 Mbps

That a significant change.

So I changed the following line in Samba's smb.conf file:

socket options = TCP_NODELAY SO_KEEPALIVE IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

to

socket options = TCP_NODELAY SO_KEEPALIVE IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

After this, I noticed the following:

Wireless:
=========

Macbook to Ubuntu: 44 Mbps, with peaks up to 48 Mbps.  

That's nearly double the performance!!  Wireless is basically what I was unhappy about.

Does anybody have any SO_SNDBUF and SO_RCVBUF values that they care to share that they have used in order to improve network performance?  Btw, removing those values gives close to the same result.

Oh, and all the above were using Samba shares.  Just for kicks, I tested the following over SFTP using FileZilla:

Macbook to Ubuntu: 60 Mbps  <---- MY GOAL!

I'm hoping to achieve the above speed with the necessary tweaks.  So I need 16 Mbps!  Please note that I did all the above tests using files larger than 1 GB to get a sustainable speed. I also did tests using 1MB files and performance was similar.

Thanks guys!  Any help is appreciated.

---

### Post by whatever69 on 2008-10-06
Hi Guys,

1.  Removing SO_SNDBUF and SO_RCVBUF from your smb.conf is the best solution.  Let the linux kernel do its job.

2.  I was able to hit speeds of 56 Mbps using NFS.  Basically, if you are running OS X and want to mount a share, use NFS, and not Samba.  But obviously, you still need Samba if you have Windows computers.  So both NFS and Samba servers are now running on my Ubuntu computer.

Hope that helps people out there.

EDIT:  I can now get speeds of up to 70 Mbps over NFS wirelessly (even though I connect at 130 Mbps and not 300 Mbps).

---

