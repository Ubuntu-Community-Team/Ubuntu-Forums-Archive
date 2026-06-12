---
title: "Missing network interfaces"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by elmo80 on 2007-02-04
Hi everyone.

I have recently installed Ubuntu 6.10 using the Alternate Install CD for AMD64 hardware.

My system is based on an ASUS P5B + Intel Core 2 Duo E6600 processor and it's purpose is to be a Virtual Machine host / server. I have also installed on system several ethernet Network Interfaces cards (3) from different vendors: 3COM, Intel, Realtek. Taking into account the integrated NIC on the motherboard, the system has 4 NICs.

The problem i am facing is that when I removed some of the NICs and replaced them with other cards my network interfaces became named eth2, eth3, eth4 and eth5, but I am missing eth0 and eth1. I would like to have the interfaces named eth0, eth1, eth2 and eth3.

I have no X-Window nor WindowManager installed (its a server installation), so I have to change the configuration by hand. ¿Where should I be looking? I've inspected /etc/network/ with no luck.

If i try to ifconfig eth0 or ifconfig eth1 i get an error message saying the device doesn't exist.

Thanks in advance.

---

### Post by bnuytten on 2007-02-18
Since you did not receive a reply for over a week I'll try to answer your question. If this were a Fedora Core system, you could have a look in /etc/modprobe.conf. There you **could** find something like:
```
alias eth1 3c59x
alias eth2 skge
```

In Ubuntu, I've taken a look in less /etc/modprobe.d/aliases but did not find any ethX stuff. If the kernel does it's hardware scan, it will e.g. find the onboard Intel interface first and load the e1000 driver and names the interfaces eth0, than it find a 3Com 3c590 card and loads the 3c59x card and names the interface eth1. So there is a direct link between these modules and their interface names.

Besides the kernel approach, you may try with the "map" keyword. See "man 5 interfaces". Again, in Red Hat based distro's you can easily supply the MAC address of an interface. So you "force" the kernel to either load the module if the MAC matches or otherwise leave the interface down. In the latter case a message would be printed to /var/log/messages on boot or /etc/init.d/networking restart.

Hope this helps.

---

### Post by esaym on 2007-03-23
edit: wrong thread, sorry

---

