---
title: "Ubuntu Distributed Process Cluster"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by rick_1010 on 2006-10-14
From what I can gather Ubuntu only has package support through Synaptic manager for server type clusters which do not deal with distributing processes and are of use only for a web server environment with redundancy on each machine.. I have hopes to somehow make a distributed process cluster on Ubuntu so that 1 machine can be the head and run software that would then be distributed throughout the machines for better performance. Anyways, if you know of anything like this for Ubuntu please post (I am aware of openmosix but it is very out of date and not suited for newer distros).

Thanks

---

### Post by AmericanAqualung on 2007-03-11
At Haverford College, we're working on putting together such a distributed cluster with Ubuntu and Open Source software.  The basic gist of the setup is to setup password-less ssh, distributed shell, ntp, nfs, open mpi, and then use the open source resource manager and scheduler - Torque/Maui from clusterresource.com .  We've been putting together some explination guides as we go and should have the final system up and running in a few weeks.  If you'd like more information send me an e-mail at [email]aohara@haverford.edu[/email]

-Andy O'Hara
Haverford College '09

---

