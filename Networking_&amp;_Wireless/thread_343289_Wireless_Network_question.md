---
title: "Wireless Network question"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by MiloLinux1221 on 2007-01-21
Does anyone know of a program for ubuntu that can see who else is using my wireless router through my wireless laptop? I'd love to give them the boot. I have a WEP key but still think someone is getting through because my internet performance has been subpar

---

### Post by Paerez on 2007-01-21
The easiest thing to do is to log in to the router and look in the DHCP section. It should list all the MAC addresses of the people connected.

---

### Post by ignorance on 2007-01-21
Well you could use a program for sniffing the network and see if there is anyone else (diffrent ip than yours) sending or recieving on your wifi. But i could have other reasons why you have a bad internet performance.

---

### Post by TheWizzard on 2007-01-21
> **Paerez said:**
> The easiest thing to do is to log in to the router and look in the DHCP section. It should list all the MAC addresses of the people connected.
machines with a static address are not visible in this table.

---

### Post by chili555 on 2007-01-21
Try fping. For example, do sudo fping -g 192.168.1.2 192.168.1.50.

If you do not have it, of course, sudo apt-get install fping.

Most routers also allow you to limit access to specific MAC addresses. Add your own, enable and then no one but you gets in.

---

### Post by Paerez on 2007-01-21
> **TheWizzard said:**
> machines with a static address are not visible in this table.

Machines with a static address will be in the static address table. Though I don't know if an intruder could give themself a static address and be able to use the network.

I think Kismet will do what you want.

---

### Post by TheWizzard on 2007-01-22
> **Paerez said:**
> Machines with a static address will be in the static address table. Though I don't know if an intruder could give themself a static address and be able to use the network.


i can't possibly find the static addresses table. and my fileserver is connected to the router with a static ip. :confused:

---

### Post by Paerez on 2007-01-22
I use MAC filtering to give my server a permanent address, so my static IPs are in the MAC filtering table. Then everything else is in DHCP. I actually run an insecure network and just rely on MAC filters.

---

