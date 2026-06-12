---
title: "how to get online with ubuntu 18.04"
date: 2019-01-22
forum: Networking &amp; Wireless
---

### Post by William_Labbett on 2019-01-22
Hi,
     
I've got an i3-8350 on a Z370 PC Pro motherboard. I've installed ubuntu 18.04 and couldn't get a network connection with things as they were. I tried pilugging in a PCI NIC
but couldn't connect with that either. I'm not sure what to do next.

Does anyone know a simple solution to this?
Are there PCI NIC'S known to work with this setup or drivers for my motherboard?

---

### Post by oldos2er on 2019-01-22
Moved to Networking and Wireless.

---

### Post by TheFu on 2019-01-22
To be fair, most network adaptors "just work", but sometimes new hardware needs extra help and brand new hardware could take a few months before someone can reverse engineer a driver.

Intel NICs are well supported.  Any of the Intel PRO/1000 or I211 Gigabit will work easily. I have 1st-hand knowledge about these. They are also more efficient for moving network data and use less system overhead and fewer interrupts.

Does the networking work from the "Try Ubuntu" choice before doing an install?  

If so, can you please run a command like this?```
$ lspci -nnk | egrep 'Net|Ethe' -A3
```
Or if you like prettier output and can install packages ... 
```
$ inxi -bz |grep Net
Network:   Card: Intel I211 Gigabit Network Connection driver: igb

```
or with the most details and useful output:
```
$ sudo lshw -C network
```

We need to see the specific NIC model, the driver and preferably the driver version.  

Please.

---

### Post by William_Labbett on 2019-01-23
Thanks very much for your reply.
I don't know how, but I've got it working now.

---

### Post by TheFu on 2019-01-23
see "just works" most of the time. ;)

---

