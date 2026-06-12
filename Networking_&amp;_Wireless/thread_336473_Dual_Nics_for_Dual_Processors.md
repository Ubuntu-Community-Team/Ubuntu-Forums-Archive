---
title: "Dual Nics for Dual Processors"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by AmericanAqualung on 2007-01-11
Hi,
I'm not sure if this is the right forum or not, but since it has to do with network setup on a cluster, I'm going to ask here anyway.
Recently, I have been working on using Ubuntu to set up an HPC linux cluster (using passwordless ssh, dsh, ntp, nfs, torque, maui, and open mpi).  Everything has been going very smoothly and I love the way Ubuntu works.  My question actually refers to a, quite common, setup seen in many rackable and blade servers.
Many of these machines are dual processor machines and contain dual nics.  I know that with torque/openpbs how to configure a machine with dual processors, but how should I use the nics for cluster communications?  Is there a way to assign data/communications needed for a processor to one of the nics an the other processor to the other nic?

Thanks a lot,
Andy O'Hara

---

