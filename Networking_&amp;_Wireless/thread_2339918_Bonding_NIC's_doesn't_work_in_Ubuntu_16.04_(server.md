---
title: "Bonding NIC's doesn't work in Ubuntu 16.04 (server)"
date: 2016-10-14
forum: Networking &amp; Wireless
---

### Post by alberlinux on 2016-10-14
Hello people. This is my first post here.

I would like to say, sorry for my English. Forgive me if I commit any grammar mistake, because my native language is Spanish.

I have several problems trying to bond two network cards in Ubuntu 16.04, server edition.

The NIC's are the same brand, Realtek, but, I don't know why, the bonding process ends unsuccessfully.

I followed various tutorials of bonding NIC's, but all of them are for Ubuntu 14.04 or 12.04. I do not know if the steps are different in both versions.

Here, some tutorials I followed:

[https://www.unixmen.com/linux-basics-create-network-bonding-on-ubuntu-14-10/](https://www.unixmen.com/linux-basics-create-network-bonding-on-ubuntu-14-10/)
[https://paulmellorsblog.wordpress.com/2014/07/17/ubuntu-server-14-04-lts-nic-bonding/](https://paulmellorsblog.wordpress.com/2014/07/17/ubuntu-server-14-04-lts-nic-bonding/)
[http://www.miguelvallejo.com/nic-bonding-in-ubuntu-12-0412-04-2/]("https://paulmellorsblog.wordpress.com/2014/07/17/ubuntu-server-14-04-lts-nic-bonding/")

Basically, I can set up bond0, but when I do a ping to google, for example, the host is unreacheable. The IP, netmask and gateway are correctly set.

I activate the "bonding" module in /etc/modules.

When the computer boots, I notice what the kernel module 'bonding' doesn't start.

The nomenclature of interfaces, is a problem? I mean, change the name of "enp4s4" to "eth0" causes problems?

If any of you need the interfaces conf file, ask me for it.

---

