---
title: "[SOLVED] please help, six weeks without wireless (post upgrade)"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by irishbreakfast on 2008-10-16
Please, someone help me.

I did the following update

linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41 
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41 
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41

and now can't use the wireless.


I have done lots of reading on this forum but have only tried:
1) Restarted with -16, -17 and -18
and 
2) sudo apt-get install linux-backports-modules-hardy-generic

Neither made any difference whatsoever.

I have not tried any other ideas as they are for other hardware or too confusing.

This is not a hardware problem, I dual boot with Vista and wireless is fine there. I am using a wired connection with Ubuntu now.

I use Intel(R) PRO/Wireless 3945ABG/BG. Dell Inspiron 1525 (not purchased in/from US)

******
Commit Log for Tue Aug 26 12:07:30 2008

---

### Post by dmizer on 2008-10-16
Please post the output of:
```
lshw -C network
```

---

### Post by irishbreakfast on 2008-10-16
thank you very much dmizer.

lshw -C network

  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:48:62:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.0.4 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:54:17:1f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

---

### Post by sh_son on 2008-10-16
> **irishbreakfast said:**
> 
I use Intel(R) PRO/Wireless 3945ABG/BG.

If you are using 3945ABG/BG it should work without any problems with default driver module that loads when you install the OS, iwl3945. Or wasn't it working before or you tried to use for other purposes like to get support of rfmon, packet injection etc?

---

### Post by irishbreakfast on 2008-10-16
It was working just fine until I did that upgrade.  

I have no idea what you are referring to with "get support of rfmon, packet injection?"

---

### Post by irishbreakfast on 2008-10-19
bump

Please Please Please help......

---

### Post by dmizer on 2008-10-19
Take a look here: [http://ubuntuforums.org/showthread.php?t=892920](http://ubuntuforums.org/showthread.php?t=892920)

Do you have a wireless on/off switch? There may be a bios setting for it as well.

---

### Post by irishbreakfast on 2008-10-19
Thank you. 

that pushed me over the edge to finally install wicd. It works fine now.

I can also now see a working version of ifconfig output, which I can try to duplicate later via terminal.

But I still need to check rebooting to Vista and back to Ubuntu as Rocklee suggested he had problems.

You wouldn't happen to know where I can learn how an upgrade can cause network-manager to not work and and what parts it broke. I would have preferred to use commands and a wee script to fix this.


Thanks for your support

I would thank you and mark this as solved but I can't figure out how to do that.

---

### Post by dmizer on 2008-10-19
> **irishbreakfast said:**
> You wouldn't happen to know where I can learn how an upgrade can cause network-manager to not work and and what parts it broke. I would have preferred to use commands and a wee script to fix this.

Just experience tells me not to trust network-manager. My experience has been that network-manager has been a problem ever since they started making it a part of the gnome desktop.

Actually, if you only connect to one or two wireless networks, you could ditch both network-manager and wicd, and just configure your wireless in: system > administration > networking

The manual configure file for networking is located at /etc/network/interfaces you can learn about all the details by reading the man page with this command:
```
man interfaces
```
There is a sticky at the top of this forum labeled "How To: Manual Network Configuration without the need for Network Manager" which is another extremely helpful reference: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If you have problems understanding what's written in the manual, or need help with the howto, please feel free to ask questions. Glad we got you working though.

For future reference, all I did to find your fix was search in google with the following parameters:
> hardy 3945ABG site:ubuntuforums.org

Within those results are several mentions of network-manager.

---

