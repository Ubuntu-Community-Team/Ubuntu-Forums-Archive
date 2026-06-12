---
title: "[SOLVED] Problem  with YPBINDPROC_DOMAIN:Domain not bound"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by quimico69 on 2008-11-12
Hello everybody,

As the title says I have a problem with an annoying message 
YPBINDPROC_DOMAIN: Domain not bound
that appears very often in the command line.

The background is this, I have a small cluster (4 machines, Hardy on all of them) that was setup using NFS and NIS (1 fileserver node for user files, so users can login to any node in the cluster and see their files).  Previously, networking was through DHCP (I know, NIS over DHCP is a huge security risk, but so far nothing bad happened, phew).  So, the powers that be decided to get rid of DHCP and go with static IP addresses.  My machines could not find each other any more.  I got new IP addresses and added the new IPs to get NFS and NIS  working again.  I followed all the indications on the NFS and NIS ubuntu howto (except for the IPSec stuff) and there is one machine that reports all the time:
YPBINDPROC_DOMAIN: Domain not bound
whenever I use a sudo <command>, it reports three or four times the message and then finally asks for the password.  

In addition, it boots reasonably fast, but X takes forever to start, reports a "failed to initialize HAL" and some problem with the trash applet.

Any ideas?

---

### Post by quimico69 on 2008-11-12
Sorry, after yet another check, it turned out that I had an incorrect address for the ypserver in yp.conf

Now it is working fine.

---

