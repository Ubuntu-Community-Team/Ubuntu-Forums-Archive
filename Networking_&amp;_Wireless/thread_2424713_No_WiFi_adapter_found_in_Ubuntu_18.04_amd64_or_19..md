---
title: "No WiFi adapter found in Ubuntu 18.04 amd64 or 19.04 amd64"
date: 2019-08-13
forum: Networking &amp; Wireless
---

### Post by aydanaydan on 2019-08-13
I've been trying every possible way in the last two days to somehow enable/install the wifi adapter, without any success. I'm pretty new into Linux, so I would like to have clear instructions on the commands I need to put in the terminal please. 

[https://paste.ubuntu.com/p/CzdxnGvHY5/](https://paste.ubuntu.com/p/CzdxnGvHY5/)

---

### Post by chili555 on 2019-08-13
Is this a virtual machine?

---

### Post by aydanaydan on 2019-08-13
> **chili555 said:**
> Is this a virtual machine?

yes, indeed

---

### Post by chili555 on 2019-08-13
Please see: [https://www.quora.com/How-do-I-enable-a-wireless-adapter-on-VirtualBox](https://www.quora.com/How-do-I-enable-a-wireless-adapter-on-VirtualBox)

> “VirtualBox or any virtualization application abstract the hardware of its host machine, and creates the virtual or hypervisor layer between the host machine’s hardware and virtual or hypervisor application”

Pretty simple huh? In layman terms it means that to use host pc hardware virtualisation software builds a virtual layer between the hardware on host pc and virtual application due to which we are unable to access wifi adapter.Next, see: [https://communities.vmware.com/thread/576192](https://communities.vmware.com/thread/576192)> 
A virtual machine will ALWAYS see the network interface as wired. 
You probably can use a USB wireless, however.

---

### Post by aydanaydan on 2019-08-16
> **chili555 said:**
> Please see: [https://www.quora.com/How-do-I-enable-a-wireless-adapter-on-VirtualBox](https://www.quora.com/How-do-I-enable-a-wireless-adapter-on-VirtualBox)

Next, see: [https://communities.vmware.com/thread/576192](https://communities.vmware.com/thread/576192)You probably can use a USB wireless, however.


Thank you chili, came across the same thread yesterday..

---

