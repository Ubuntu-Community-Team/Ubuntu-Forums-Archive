---
title: "Ubuntu 20.04 Ethernet not working"
date: 2020-04-19
forum: Networking &amp; Wireless
---

### Post by vasi7899 on 2020-04-19
I am using ubuntu 20.04, till now there is no problem but suddenly my ethernet stopped working when I type 
```
`sudo lshw -C network`



```I posted the same in focal bug section, but they advised me to post it here. So I am reposting it the same.
This is the result 


    ```
*-network UNCLAIMED       
           description: Ethernet controller
           product: RTL810xE PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:02:00.0
           version: 07
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd cap_list
           configuration: latency=0
           resources: ioport:3000(size=256) memory:a2200000-a2200fff memory:a2000000-a2003fff



```But I am able to connect to WiFi.

My kernel version is [B]5.4.0-24-generic


[/B]

---

### Post by guiverc on 2020-04-19
Possibly useful - [https://github.com/ghostrider-reborn/realtek-r8101-linux-driver](https://github.com/ghostrider-reborn/realtek-r8101-linux-driver)

---

### Post by vasi7899 on 2020-04-19
It worked. Thanks

---

### Post by mörgæs on 2020-04-19
Good, please mark the thread solved.

---

