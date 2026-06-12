---
title: "Networking on Client vs Server"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by billtric on 2007-09-09
I have successfully installed Ubuntu 7.04 Desktop and Server in two different Parallels Virtual Machine running on my XP box.

Now, I am having networking issues.  The Desktop network does work, but only after I right click on the network icon and select "Wired Network".

The file /etc/network/interfaces looks good on desktop and server.

Running ifconfig on the desktop gives me the **eth0** and **lo**, but server only gives me **lo**.

How can I get eth0 on my server?

Thanks,
Bill

---

### Post by billtric on 2007-09-10
I was able to figure this one out.

When I installed the server in Parallels, i did it this way: **install acpi=off noacpi nolacpi pci=noacpi**
I wiped it and re-installed this way:** install acpi=off**

I guess all that acpi stuff was causing the installer to ignore the NIC.

Thanks..

---

