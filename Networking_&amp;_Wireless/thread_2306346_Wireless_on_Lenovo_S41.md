---
title: "Wireless on Lenovo S41"
date: 2015-12-14
forum: Networking &amp; Wireless
---

### Post by auduns on 2015-12-14
Hello.

I have installed Ubuntu 15.10 on a brand new Lenovo S41, but there is no wireless.

lspci:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Broadcom Corporation Device 43ae (rev 02)
```

lshw:

```
  *-network
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:44 memory:f0c00000-f0c07fff memory:f0800000-f0bfffff
```

I have tried to install bcmwl-kernel-source, but no luck. I really have no idea where to look next.
Googling "43ae" just gives me a few other threads with the same problem.

Can I get this wireless card to work on Ubuntu, somehow?

Thank you :)

---

### Post by sandyd on 2015-12-14
Moved to *Networking & Wireless*

---

### Post by Hadaka on 2015-12-14
Hi, please open a terminal then COPY and paste.
one line at a time.
```
lspci -n | awk '/0280/{print$3}'
rfkill list all
```
post the output
thanks.

---

### Post by auduns on 2015-12-15
Thank you for answering.

Output:

> root@stinelenovo:~# lspci -n | awk '/0280/{print$3}'
14e4:43ae
root@stinelenovo:~# rfkill list all
root@stinelenovo:~# 


---

### Post by Hadaka on 2015-12-15
Hi,your broadcom card is not yet supported,there is no linux dirver
for it at this time.
this thread,also a Lenovo,solved the problem by replacing the card
[http://ubuntuforums.org/showthread.php?t=2296434](http://ubuntuforums.org/showthread.php?t=2296434)
page #3
Note that this card has 2 antenna posts.
this thread solved his issue of weak signal ...here
[http://ubuntuforums.org/showthread.php?t=2304607&page=2](http://ubuntuforums.org/showthread.php?t=2304607&page=2)
Post #19
*Or purchase a USB wifi device.
good luck

---

### Post by auduns on 2015-12-15
Allright, thank you for the update.

It is a brand new computer, so I don't think I will try to replace the card. I just have to settle with a USB wireless for the time beeing :)
Maybe there will be a driver available later :)

---

