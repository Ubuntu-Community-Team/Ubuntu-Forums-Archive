---
title: "[SOLVED] [SOLVED] A8V-VM SE VIA Rhine wired adapter onboard NIC in ubuntu 8.04"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by linuxvacuum on 2008-06-27
I had major problems with my wired network adapter with this A8V-VM SE motherboard such as : lost connectivity, no ip, intermittent internet access.

But thanks to this fix from [https://lists.ubuntu.com/archives/ubuntu-users/2004-October/004844.html](https://lists.ubuntu.com/archives/ubuntu-users/2004-October/004844.html) it works! :guitar:

Add this to the end of the kernel line in your GRUB
> pci=noacpi noapic

I don't know why it works, how is power management related to the NIC getting an IP lol?, but it does!

---

