---
title: "Having issue communicating from Ubuntu 18.04 Virtual Server"
date: 2021-01-09
forum: Networking &amp; Wireless
---

### Post by donchido on 2021-01-09
Hello All,
Please i have the following cases on my Ubuntu 18.04 servers
1. I attached a **secondary NIC** to VM running Ubuntu, edited the **yaml file** and did **netplan apply **successfully, new NIC was visible when i did **ifconfig -a **but NIC unable to communicate out (to other servers on same VLAN) 
2. I attached a **secondary NIC** to another VM running Ubuntu, edited **yaml **and did **netplan apply** , no error message. **Ifconfig -a **doesnt display newly configured IP address edited on **yaml file** and thus unable to communicate out. Please is there any other step i'm missing here. i'm still trying to get the hang of how Ubuntu works (thus not an expert). please any recommendation is highly appreciated

Regards,
Donchido

---

### Post by TheFu on 2021-01-09
On the vm-host, you need to setup a bridge for the VMs to connect.  
Or use iommu to pass the pci card into a VM for exclusive use.  There are kernel settings at boot for that.
[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)

The hypervisor used will matter too. Which one is being used?

---

