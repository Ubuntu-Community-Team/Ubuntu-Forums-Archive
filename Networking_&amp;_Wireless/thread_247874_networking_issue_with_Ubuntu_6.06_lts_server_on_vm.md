---
title: "networking issue with Ubuntu 6.06 lts server on vmware"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by bdanford on 2006-08-31
I have a Ubuntu installation I was buiding on a test VMWare Server 1.0.1 box. I had 2 network cards installed, one on a internal network behind a firewall, and another on a DMZ behind a filewall. Im building a spam filter that will relay mail to my main mail server. Everything was working fine, so I moved the VM to my production VMware server, same version and everything, nics on vmware configured the same, vnet0 briged to internal network, and vnet1 briged to dmz network. Bring back up the vm on the production server. No network interfaces? just the loop back. When I do a /etc/init.d/networking start, I get this:

SIOCSIFADDR: no such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: no such device
SIOCSIFBRDADDR: no such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

Same thing for eth1.

I installed the VMware tools, but when I did, I didnt have a build environment installed, so I didnt have it build the modules for the vmware tools. Now, I cant do it becuase I dont have the kernal sources installed, and with no network interfaces, I cant really (easily) get the kernel sources to build the modules.

Any ideas, I really hate to rebuild this machine.

Thanks!

Brian D. Danford
[email]brian@mytsi.org[/email]

---

