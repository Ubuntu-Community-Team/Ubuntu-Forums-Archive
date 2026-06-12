---
title: "What settings in Firestarter will allow a QEMU bridged network?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by andrewkk on 2008-11-07
I have set up a virtual machine with bridged networking [as described on the wiki]("https://help.ubuntu.com/community/KVM#Networking"). When Firestarter is running, the virtual machine guest cannot connect to the internet via the bridge and cannot ping the host. When I *sudo firestarter --stop*, the virtual machine guest is assigned an IP via DHCP, can connect to the internet, and can ping the host.

I would rather not have to stop Firestarter completely; what "holes" should I punch in the firewall to allow the virtual machine guest network access over the bridge?

---

