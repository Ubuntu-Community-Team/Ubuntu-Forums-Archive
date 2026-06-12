---
title: "Ndiswrapper problem with Belkin54g Card"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by gorgeous on 2006-09-21
Hello,

I installed Ubuntu Lamp Server in my computer few months ago. I am trying to setup the wireless connection to a wireless router.

I installed ndiswrapper to install the drivers of the network card, and the results are OK, the driver is installed and the hardware present, but then when I type modprobe ndiswrapper it tells me the module ndiswrapper is not found.

The next term was, following the instructions of some users, download the source of ndiswrapper to compile it and make it again, but I obtain more errors when I type make and...

"Can't find kernel sources in /lib/modules/..../build/"

I try to create a symbologic link with this command: "ln -s /usr/src/`uname -r` /lib/modules/`uname -r`/build"

but I can't find the source of the kernel on my file system.

I will try to compile another kernel but I think this is not necessary. Or I need that?

Thanks a lot to everybody.

Gorgeous George.

---

### Post by gorgeous on 2006-09-22
Hello! I fixed my problem installing the linux headers, but now....the driver is running but I cant get the wlan01 interface when I type iwconfig..

---

