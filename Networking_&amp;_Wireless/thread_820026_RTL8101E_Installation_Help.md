---
title: "RTL8101E Installation Help"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by WeEatVista on 2008-06-05
Alright, now I know what wireless card I have. I have a realtek RTL8101E. After searching the web, I can't find out how to actually make it work. I downloaded the Linux driver, but I can't figure out how to install it. Any help?

Thanks in advance,

We Eat Vista

P.S. I'm new to Linux and lovin it, except for wireless :(

---

### Post by chili555 on 2008-06-05
Are you certain your wireless is 8101E? I thought that was a wired ethernet card. Please post, from a terminal:```
sudo lshw -C network
```We'll take a closer look.

---

### Post by WeEatVista on 2008-06-05
My output of that code is 

 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:89:05:1a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair


I'm not sure if this is even a wireless card, I don't think ubuntu 8.04 recognizes my card. I didn't think that RTL8101E sounded right either from my previous experience using windows (i think windows detected it as another card)

Thanks for your help so far, I hope I can get wireless going.

EDIT: While researching online, I found that my laptop (Toshiba Satellite A215-S742[eight]) comes with the Realtek RTL8187B wireless card (which doesn't work well with ubuntu at all)

---

### Post by chili555 on 2008-06-06
It seems certain that your 8101E is an ethernet device:> description: Ethernet interface
product: RTL8101E PCI Express Fast Ethernet controllerAs for your 8187B, here is a link that may help:[http://ubuntuforums.org/showthread.php?t=782299&page=2&highlight=jadams](http://ubuntuforums.org/showthread.php?t=782299&page=2&highlight=jadams) see post #12. The file referred to is here: [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

Read these posts carefully and we'll be glad to help.

---

