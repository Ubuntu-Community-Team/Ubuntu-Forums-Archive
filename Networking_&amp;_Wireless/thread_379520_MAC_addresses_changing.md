---
title: "MAC addresses changing"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by osx on 2007-03-08
I recently cloned an Ubuntu LAMP install from one Dell PowerEdge 2850 to another using dd over netcat (they were each configured RAID 5 with same space). The machines are not identical in hardware, though. On boot of the cloned system everything seemed fine and worked just as the source machine did; however, I have started having some strange problems.

First (not a problem I don't think), the network cards showed up as eth2, eth3, and eth4 instead of starting at eth0 as the source machine shows. The cloned machine has a fiber card (eth2) while eth3 and eth4 are the same type as what the source had (Dell NICs just with different MAC addresses).

Second, which is a problem, is that on the cloned machine, eth3 and eth4 periodically swap MAC addresses. Don't know why and it doesn't seem to be linked to any event. For instance, it happens while the system is running even, not during boot.

For now I have specified the MAC address for each of these interfaces in the /etc/network/interfaces file. Is this OK? Will this "fix" the problem? Additionally, does anybody have any idea as to what is causing the problem?

It's running Ubuntu 6.06.1 LTS with kernel 2.6.15-28-server. I did a kernel upgrade from 2.6.15-27-server after the clone, but I had the problem before the upgrade.

I've just never heard of anything like this before and am at a total loss.

Thanks for any help.

---

### Post by netztier on 2007-03-08
> **osx said:**
> 
For now I have specified the MAC address for each of these interfaces in the /etc/network/interfaces file. Is this OK? Will this "fix" the problem? 


I think that this will make things even more confusing, because like that you "overwrite" the addresses: Upon loading, a driver module copies and writes a NIC's MAC address to a specific place in memory. Defining a MAC address in /etc/network/interfaces will "manually" overwrite that address in memory. I suspect that this helps a lot to create quite a bit of confusion, up to the case of having two identical MAC addresses in the same system on two different interfaces.

Take a look at  **/etc/iftab** instead:

```
[FONT="Courier New"]marc@blaze:~$ **more /etc/iftab**
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:A0:C9:98:82:0E arp 1
eth1 mac 00:50:8B:07:E9:83 arp 1
marc@blaze:~$[/FONT]
```

In this file, you can nail-down ethX assignment, so there won't be any more confusion. Try **dmesg | grep eth** to see the MAC addresses that are discovered during startup.

best regards

Marc

---

### Post by osx on 2007-03-08
Thanks. I'll give that a try. Any idea why this is happening in the first place? Seems to be pretty consistent in the sense that it happens within two hours of boot. One minute each NIC has the correct MAC, the next minute eth3 and eth4 have switched MACs. Once it is up and running, I pretty much have no interaction with it and it is yet to be in production so there are no users on it which indicates it is not linked to any particular user activity.

---

### Post by Mr. C. on 2007-03-09
First, its a bad idea to take a system clone, that's already been booted and configured to another piece of hardware.  Configuration files are written, that won't jibe with the new system.  Unless you understand the gotchas, don't expect things to work out.

Does your system's BIOS show that the NIC mac addresses are swapping, or do you only see that in Linux after the system is booted?

MrC

---

### Post by osx on 2007-03-14
BIOS shows correct MAC addresses. They seem to randomly change after boot.

---

### Post by Mr. C. on 2007-03-14
Then I suspect this would be a property of the order that PCI devices are setup in the PCI enumeration table.  Very curious.

MrC

---

