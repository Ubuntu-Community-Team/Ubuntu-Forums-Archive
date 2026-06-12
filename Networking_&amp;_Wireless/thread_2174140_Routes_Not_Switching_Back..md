---
title: "Routes Not Switching Back."
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by sandeepdas on 2013-09-13
Hi Friends,

I am facing one problem. I have two sites and both are connected via MPLS link. I have ubuntu based asterisk servers on both sites and they are connected over MPLS link. Now for fallback purpose we have create secure tunnel between two sited via internet link. If our MPLS links goes down, traffic of my ubuntu server is automatically shifts to the backup tunnel but the problem is if my primary links (MPLS) comes up, ubuntu is not switching it back and i have to do it manually. Is there any way to automate this process.

My Ubuntu details are as follows. 

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise

Any help in this is much appreciated.

Regards,
Sandeep

---

### Post by sandeepdas on 2013-09-14
Guys Please help...!

---

### Post by s-bodet on 2013-09-14
Hi,

until we don't know more on how you configured the routing stuff, it's not easy to help...

How do you trigger the backup ?

Steve

---

### Post by Praveen_Raiker on 2013-09-16
Hi Steve,

I am working with Sandeep. we are using IP SLA on router to check the link status and trigger the failover. router IP address is configure as gateway on Ubuntu system.
Router, VPN device and Ubuntu system on same network. once the failover take place and traffic going through backup device. when the primary link comes up. system did not change its routing table. because all the devices reside in same subnet.

Praveen

---

