---
title: "Intel 82562EZ e100 &amp; eepro100 Issues"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by gnutech on 2006-08-17
I have a Sony Vaio with an OEM Asus motherboard that has a Intel 82562EZ Nic.

lspci

02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

dmesg|grep e100

e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
e100: Copyright(c) 1999-2005 Intel Corporation
e100: eth0: e100_probe: addr 0xfeaff000, irq 17, MAC addr 00:0C:6E:9D:00:2A

I have tried everything I can think of and cannot get it to work.

By default ubuntu 6.06 loads the e100 driver, but when I try to ifconfig eth0 up it gives the following error "SIOCSIFFLAGS: Resource temporarily unavailable."  It is my understanding that this is an irq conflict error.

I tried disabling other integrated devices (i.e., sound card, etc), but nothing seems to work.  It was suggested that I disable PnP OS in the BIOS, but being that this is an OEM motherboard the BIOS is quite locked down.

If I rmmod e100 and modprobe eepro100 I am then able to ifconfig eth0 up, but it only shows that the interface has an irq and not a base address.

The default route seems to be fine, but when I try to ping the default gateway it cannot reach it.

I have even tried downloading the latest Intel e100 driver and compile it to only find the same results.

I would appreciate any assistance.

Respectfully,


Gary

---

### Post by gnutech on 2006-08-18
Come on you guys.  My company is trying to decide whether we should go with Ubuntu or OpenSuSE.  I told them that Ubuntu would be the way to go simply because of all the great community support and now no one replies to my little driver problem (above).  Please help another company go Ubuntu.

Respectfully,


Gary

---

### Post by zorglab on 2006-08-31
> **gnutech said:**
> Come on you guys.  My company is trying to decide whether we should go with Ubuntu or OpenSuSE.  I told them that Ubuntu would be the way to go simply because of all the great community support and now no one replies to my little driver problem (above).  Please help another company go Ubuntu.

That's the kind of post which makes me hesitate to reply.

Anyway, I had a similar problem. I resolved it by adding pci=routeirq to the kernel boot options. The interface showed then up as eth2 even though dmesg reported eth0.

---

### Post by thaer on 2006-08-31
we sure have a great support , it's just that we need time to answer your problmes

---

