---
title: "Internet access is gone"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by zoltanzylox on 2008-08-27
Hey,
        I did my system update this morning and after it installed a new kernel and a bunch of apps, the internet is no longer working. Deluge the bittorent program still works, but Firefox and Pan are completely hung up. I now seem to have eth1 instead of eth0 when I do ifconfig. It seems there are others having this problem. Don't the system update people test this stuff out before they launch it on us? Help!

---

### Post by puppywhacker on 2008-08-27
yes the update people test the packages, but strangely enough they refuse to come to your house to test specifically your system.

The problem is that interface names like eth1 are assigned at startup by the kernel. The order is chosen based on hardware position (io/irq).

You can define the device name somehow by spefifying the module name for your device and it's alias in /etc/modprobe.d/aliases

easier is to just accept reconfigure the changed device again to match your network. click "system" "administration" "network" or update the file /etc/network/interfaces

goodluck

---

### Post by zoltanzylox on 2008-08-27
>yes the update people test the packages, but strangely enough they refuse to come to your house to test specifically your system.
Well, since this seems to be a kernel update issue, maybe it's not specific to my machine, which again leads me to wonder if indeed anyone checked this out. You must be aware that the "Networking and Wireless" pages are full of this problem.
>The problem is that interface names like eth1 are assigned at startup by >the kernel.

 The order is chosen based on hardware position (io/irq).

>You can define the device name somehow by spefifying the module name for your device and it's alias in /etc/modprobe.d/aliases

>easier is to just accept reconfigure the changed device again to match your network. click "system" "administration" "network" or update the file /etc/network/interfaces

The problem is that once eth1 has been assigned, neither Firefox nor Pan nor any other browser see it. I also get a message saying "eth0 does not exist." This is a ******* mess, and all I did was innocently run system update. Thanks for your input, I appreciate it, but does anyone have some step by step instructions as to how I can get my net access back?

---

### Post by Sloma on 2008-08-27
> **puppywhacker said:**
> (...) easier is to just accept reconfigure the changed device again to match your network. click "system" "administration" "network" (...)

goodluck

Ok, this method works but after restart I have to do it again :(

---

