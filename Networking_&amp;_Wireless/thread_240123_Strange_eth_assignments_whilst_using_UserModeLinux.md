---
title: "Strange eth assignments whilst using UserModeLinux"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by Rygel on 2006-08-20
Hi there,

on a (seems so, at least...) correctly configured PC, I get strange results in starting user mode linux instances. Strange not because of an incomplete startup but by the fact that the eth assignments are wrong.

When I start a user mode linux instance with

./vmlinux eth0=tuntap,tap1

the result is, that there is _no_ eth0 in the uml instance, just an eth2 - what would be the logical continuation of the eth0, eth1... row of the host-pc.

I wrote all this to the uml mailing list, but they are quite sure that the problem is somewhere in the ubuntu startup because there are no problems with other distros as FC5, debian sarge etc. 
They speculated on some kind of ifrename - which in my case is not installed on the system.

I'm quite interested in the cause of this because I'ld like to use ubuntu with UML. So, what's the main difference in networkin setup in ubuntu compared with debian or other distros, what could cause the client instance to start the eth count at 2 instead of being unimpressed by the count of eth devices on the host?

Kind regards,
Peter

---

