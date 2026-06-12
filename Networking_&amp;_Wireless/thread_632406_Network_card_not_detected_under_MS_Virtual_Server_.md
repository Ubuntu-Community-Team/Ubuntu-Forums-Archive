---
title: "Network card not detected under MS Virtual Server 2005"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by jonnytabpni on 2007-12-05
hey guys

Tried installing UBuntu Server 7.10 on virtual server 2005. it won't work as CD drive wasn't detected. So i installed it in MS Virtual PC and imported the hard drive into Virtual Server...

Ok sure it works...but UBuntu won't detect the virtual server 2005 virtual network card.

I have tried the "Connect to HP NIC bla" setting as well as "Internet Network" to no avail.

Your help would be appreciated.

Many Thanks

---

### Post by Maxtorm on 2007-12-12
I'm having the same kind of problem using an Ubuntu 6.06 vm under VMware Server 2.0 running on an Ubuntu 7.10 box. If you figure it out, please post here. I will do the same.

---

### Post by Maxtorm on 2007-12-12
Problem solved though I'm not sure how the solution will apply to Virtual Server. I did two things and I'm not sure which actually fixed the issue:
[LIST=1]
[*]Installed VMware tools onto the vm. This contained instructions for removing the automatically installed driver for the AMD virtual NIC and install the vmxnet driver for the VMware NIC.
[*]Commented out all lines in /etc/iftab as it did not contain a valid MAC address for the virtual NIC.[/LIST]

---

