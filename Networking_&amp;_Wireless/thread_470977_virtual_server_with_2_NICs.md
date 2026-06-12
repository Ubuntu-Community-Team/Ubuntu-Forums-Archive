---
title: "virtual server with 2 NICs"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by theaaronm on 2007-06-11
Hi,

I have Ubuntu 6.10 Server with 2 network cards installed.  I have routing working perfectly on the operating system itself, but I am having problems using VMWare's Virtual Server and an Ubuntu appliance.  I cannot figure out how to direct the virtual appliance which NIC to use.  No matter what I try to do, it seems that the virtual appliance always bridges to the host's eth0.  I've tried setting vlans, but don't much much experience in this arena.

I have run vmware-config-network.pl and it says that vmnet0 is bridged to eth0 and vmnet2 is bridged to eth1.  When I config the appliance through vmware server console to use vmnet2 as eth1 doesn't seem to work.  It continues to use vmnet0.

Does anyone have some guides or pointers for me to troubleshoot what is going on here?  Does the linux version of Virtual Server have anything like the Virtual Network Editor on Windows?

---

