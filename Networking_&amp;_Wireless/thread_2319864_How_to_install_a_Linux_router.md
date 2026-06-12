---
title: "How to install a Linux router?"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by satimis on 2016-04-08
Hi all,

Connection
FTTH (500mbps) -> ONT (4 ports) -> 2 PCs-Virtual Machine
(Dynamic IP)

ONT-Huawei HG8045

Oracle VirtualBox
Host	     Ubuntu 14.04 desktop
VMs	     Ubuntu 14.04 desktop/server/Windows 10 etc.
(PC-4/8 cores, RAM-8/32G, HDD-SSD 1TB, about 20 VMs running on each Virtual Machine)

ONT assigned IP - 192.168.8.2/3/4/5 etc.

Instead of connecting a hardware router to the network, I'm considering building a Linux router on a VM running Ubuntu 14.04 desktop/server.

Please advise which software shall I use pfsense/Quagga any others?

Thanks

Regards
satimis

---

### Post by lukeiamyourfather on 2016-04-08
pfSense is excellent but it's not Linux nor is it an application, it's an operating system based on FreeBSD. You can do it through Ubuntu but it will be a lot more trouble that it's worth IMHO.

---

### Post by satimis on 2016-04-13
> **lukeiamyourfather said:**
> pfSense is excellent but it's not Linux nor is it an application, it's an operating system based on FreeBSD. You can do it through Ubuntu but it will be a lot more trouble that it's worth IMHO.
Agree, lot of work.

Now all VMs can connect pfSense and browse Internet.  But Host can't connect pfSense nor ping its IP Address 192.168.1.1.  pfSense can ping Host.  Same situation as I did about 2 years ago.  I'm still working to sort out the problem.

satimis

---

