---
title: "cannot connect to network, nor internet"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Atica on 2008-07-24
Current network configuration: ethernet card Intel PRO/100 VE on a Dell Dimension 4550
connected to a Ethernet Broad band D-link router (dhcp), from thence to a cable modem to the internet. This configuration is working and stable on my current home LAN under XP and Vista.  Want to migrate to Linux, thus tried Ubuntu 8.04.1 LiveCD (Checksum iso and CD - OK).
Cannot get a working network connection !  Does not find my ethernet card !  Is the problem with the liveCD version of Ubuntu?  If I dont get a connection, I dont expect to be able to do an install since I would not be able to get internet access.
A solution anyone ?  Thank you

---

### Post by flamethrower on 2008-07-24
> **Atica said:**
> Current network configuration: ethernet card Intel PRO/100 VE on a Dell Dimension 4550
connected to a Ethernet Broad band D-link router (dhcp), from thence to a cable modem to the internet. This configuration is working and stable on my current home LAN under XP and Vista.  Want to migrate to Linux, thus tried Ubuntu 8.04.1 LiveCD (Checksum iso and CD - OK).
Cannot get a working network connection !  Does not find my ethernet card !  Is the problem with the liveCD version of Ubuntu?  If I dont get a connection, I dont expect to be able to do an install since I would not be able to get internet access.
A solution anyone ?  Thank you

yeah, "a solution anyone". i'm pulling one out of my *** right now -.-

is your nic supported directly by the kernel and just needs a firmware? if so, did you download and install the firmware?
are there official linux drivers from intel for your nic? of so, did you download and install these?

---

### Post by Atica on 2008-07-24
> **flamethrower said:**
> yeah, "a solution anyone". i'm pulling one out of my *** right now -.-

is your nic supported directly by the kernel and just needs a firmware? if so, did you download and install the firmware?
are there official linux drivers from intel for your nic? of so, did you download and install these?
This is the question - I dont know if my NIC is directly supported on the Ubuntu 8.04.1 distributed liveCD !  I know that drivers exist for the Intel PRO/100 VE under the Linux kernel 2.6.24 of that Ubuntu version (see intel download site).  However, I dont know enough about Linux, to start an installation and then be stuck with getting s/w from the internet without a connexion directly under linux and having to go through the process in a different way.
I recently installed Debian 4.0r.3 on an old Compaq laptop 1260 with PCMCIA ethernet card - started installation with boot/root/drivers diskets and from there, everything went smoothly, with installation directly from the internet until completed.  Impressive !  but... is Ubuntu restrictive?

---

### Post by flamethrower on 2008-07-24
> **Atica said:**
> This is the question - I dont know if my NIC is directly supported on the Ubuntu 8.04.1 distributed liveCD !  I know that drivers exist for the Intel PRO/100 VE under the Linux kernel 2.6.24 of that Ubuntu version (see intel download site).  However, I dont know enough about Linux, to start an installation and then be stuck with getting s/w from the internet without a connexion directly under linux and having to go through the process in a different way.
I recently installed Debian 4.0r.3 on an old Compaq laptop 1260 with PCMCIA ethernet card - started installation with boot/root/drivers diskets and from there, everything went smoothly, with installation directly from the internet until completed.  Impressive !  but... is Ubuntu restrictive?

i dont know bout the ubuntu live cd, but the knoppix live cd simulates a writable root filesystem (by merging the cd with a ramdisk), so you can install drivers there. i suggest you try installing the drivers in a knoppix session. if you can get it to work there, it will probably work in any distro.
also, why dont u stay with debian, since you've had experience with the installation process anyway. if you want more up-to-date software than etch (4.0) has to offer, go for the testing branch. this is more unstable but still at least as good as a ubuntu install.

---

