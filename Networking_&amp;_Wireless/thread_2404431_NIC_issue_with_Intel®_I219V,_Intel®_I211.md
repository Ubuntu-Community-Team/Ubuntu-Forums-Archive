---
title: "NIC issue with Intel® I219V, Intel® I211"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by shumway1234 on 2018-10-24
Hello,


I have following problem concerning network interfaces,
and if anyone can suggest what is causing this problem or how to troubleshoot for more.


I have ASUS MB TUF-Z270-MARK1 with two integrated NIC, mostly  I am using eth0 interface.
After reboot or when I turn on PC, eth0 is not working, Ethernet link is in up state 
but traffic is not forwarding (TX/RX packets are not increasing), If I reboot pc several times 
it may start working again. executing  script "/etc/init.d/networking restart"  does not helps.


Lately I checked that when eth0 interface is not working, at same moment eth1 is working, 
and If I remove e1000e module  and run "/etc/init.d/networking restart"  eth0 starts working  without a problem. 


I did not had this problem when installed this os, problem appeared after some time, I want to use eth1 and do not 
konw how to fix this issue, for now I have blacklisted e1000e module and after that eth0 is working without a problem. 


OS: Ubuntu 16
Kernel: 4.19.0 


eth1 (using driver module e1000e) Intel® I219V, 1 x Gigabit LAN Controller(s)
eth0 (using driver module igb)  Intel® I211, 1 x Gigabit LAN


lspci 
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V
    Kernel driver in use: e1000e
    Kernel modules: e1000e


03:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
    Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection
    Kernel driver in use: igb
    Kernel modules: igb




modinfo igb
filename:       /lib/modules/4.19.0/updates/drivers/net/ethernet/intel/igb/igb.ko
version:        5.3.5.20
license:        GPL
description:    Intel(R) Gigabit Ethernet Linux Driver




 modinfo  e1000e
filename:       /lib/modules/4.19.0/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        3.2.6-k
license:        GPL
description:    Intel(R) PRO/1000 Network Driver

---

