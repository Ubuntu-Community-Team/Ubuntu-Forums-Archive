---
title: "vmware problem with two bridged network nics and host static ip address"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by suoko on 2008-03-12
Hi,

I'm running an ubuntu gutsy host with vmware installed with a slackware guest.
I have 2 nics on this machine which have been both bridged (vmnet 0 and vmnet 2)

If I set up dhcp on the host network nics I have no problem.
If I set up static address on host nics, I start having problems (even with logginin into the host)

Any guesS?

EDIT: Forgot to say that I do NOT have neither avahi nor networkmanager installed
I also disabled the NAT and HOST virtual interfaces.
I only have 
vmnet0 -> bridged to eth0 
AND 
vmnet2 -> bridged to eth1


I'm also sure this problem (relative to static ip address) does not occur with ONE bridged nic only.

---

