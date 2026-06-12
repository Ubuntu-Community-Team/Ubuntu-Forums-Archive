---
title: "NC100 doesn't run in Heron"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by fester225 on 2008-08-19
I'm running an old Gateway on 8.04, but it doesn't connect to the local Ethernet through its ADMtek NC100 network card, which used to work under Windoze.

I have a 1.44 floppy with instructions for Linux, and a TULIP.C file, which apparently result in the creation of a network driver. Of course, the instructions don't work.

How do I load an appropriate driver into my Gateway so it will connect with my Ethernet?

---

### Post by ariebs on 2008-08-21
The Tulip driver has been around for about an epoch and a half, so I'd be suspicious of any solution that isn't "Use what the distro provides."

What are the symptoms that you're seeing?

The output from the following may be helpful to debug this:

$ lspci
$ sudo lshw -C network
$ /sbin/ifconfig
$ sudo cat /etc/network/interfaces

/andy

---

