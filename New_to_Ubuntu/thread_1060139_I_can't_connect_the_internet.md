---
title: "I can't connect the internet"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Amani.S on 2009-02-04
Hello ,
I've just installed Ubuntu now 
I have a problem , That I can't connect the internet
I also have Windows Vista , and the internet is very good there
What should I do ??

---

### Post by NewJack on 2009-02-04
Let's start with a couple of questions:

1- Is it wired or wireless that you are having a problem with?
2- Are you on a laptop or a desktop?
2- What version of Ubuntu are you using?

P.S.- I recommend being a bit more descriptive in your future posts.  It will help the Community help you.

---

### Post by davidwaine on 2009-02-04
Can you say what steps you have already taken and what computer you are using please? Also which version of Ubuntu? Are you using wireless?

---

### Post by Amani.S on 2009-02-04
1- Is it wired or wireless that you are having a problem with?
**both** 
2- Are you on a laptop or a desktop?
**laptop**
2- What version of Ubuntu are you using?
**Ubuntu 8.10 i368**

P.S.- I recommend being a bit more descriptive in your future posts. It will help the Community help you.
**Thank U , I'll try to **:)

---

### Post by Amani.S on 2009-02-04
My laptop is MSI : MS-163C

---

### Post by davidwaine on 2009-02-04
Does anything happen when you plug in the cable at all?

---

### Post by Amani.S on 2009-02-04
No , nothing at all 
I was told that I have to configure my Internet Card by writing something in the terminal 
but till now I don't know what to write

---

### Post by newbee70 on 2009-02-04
> **Amani.S said:**
> Hello ,
I've just installed Ubuntu now 
I have a problem , That I can't connect the internet
I also have Windows Vista , and the internet is very good there
What should I do ??

open terminal and enter:

```
 lshw -C network 
```

and post the output here.

---

### Post by Amani.S on 2009-02-04
The output is :

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:21:85:48:1a:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:f6:36:aa:65:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

