---
title: "Ubuntu 14.04, Intel AC-8265 m.2 network connection is &quot;UNCLAIMED&quot;"
date: 2017-02-24
forum: Networking &amp; Wireless
---

### Post by markef on 2017-02-24
Hi all,

Been struggling with this all day so last resort really. Struggling to find the drivers for this card for 14.04 anywhere. I tried installing Windows Wireless Installer and Wine an a shabby attempt to "hack" the drivers on but to no avail.

sudo lshw -C network gives me this: 


```
*-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:df200000-df201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: eth0
       version: 12
       serial: 80:fa:5b:3b:5e:23
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       ....
       ....
       ....
```

Worth noting that the Ethernet adapter is working fine. 
Any help?

---

### Post by ajgreeny on 2017-02-24
You probably need to install Ubuntu version 16.10 for that wifi adapter to work according to [https://ubuntuforums.org/showthread.php?t=2340679](https://ubuntuforums.org/showthread.php?t=2340679)

I believe you will not be successful with 14.04, nor probably with a normal kernel in 16.04, though there may be some hope with 16.04 if you update the kernel according to [https://ubuntuforums.org/showthread.php?t=2351610](https://ubuntuforums.org/showthread.php?t=2351610)

---

### Post by chili555 on 2017-02-24
> You probably need to install Ubuntu version 16.10 for that wifi adapter to work Yes, please.

[http://askubuntu.com/questions/854858/new-hp-spectre-x360-wifi-not-working-using-intel-8265-card](http://askubuntu.com/questions/854858/new-hp-spectre-x360-wifi-not-working-using-intel-8265-card) Please note the comment:> Thanks, upgrading to 16.10 solved it.

---

