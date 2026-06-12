---
title: "WMP11 no longer works after upgrade"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by Jsteinman on 2007-03-13
Hi,

I am running version 6.10 after updating my system with the &#8220;Update Manager&#8221; my LinkSys WMP11 wireless card no longer works and no longer show up under system->administrator->networking

uname -a
Linux paonia 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

If I look for the card using &#8220;lshw&#8221; it show the card but it is disabled and it configuration is no loner wireless.

Output from lshw

*-network DISABLED
description: Ethernet interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: 6
bus info: pci@00:06.0
logical name: wlan0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=prism2_pci multicast=yes
resources: iomemory:dddff000-dddfffff irq:177

If I boot back to the kernel before the update and the wireless can works fine. If I look for the card using &#8220;lshw&#8221; I see it as enabled and the configuration shows it as wireless.

uname -a
Linux paonia 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Output from lshw

*-network
description: Wireless interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: 6
bus info: pci@00:06.0
logical name: eth0
version: 01
serial: 00:06:25:09:9c:b9
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=orinoco_pci ip=192.168.0.102 multicast=yes wireless=IEEE 802.11b
resources: iomemory:dddff000-dddfffff irq:177

Something has changed between the kernel/module upgrade between 2.6.17.10 and 2.6.17.11 to break the LinkSys WMP11 wireless card.

Has anyone else experienced this problem and is there a solution?

- John

BTW: Also, after the upgrade the wireless card shows up as wired and as wlan0. If I enable it the lshw show it now enabled but not as a wireless. This should not happen when the card was working before the upgrade and still works if I boot off of the old kernel. What has changed?

---

### Post by Jsteinman on 2007-03-14
After some research on the web and poking around on the system I found that both the prism2 and the orinoco drives were being loaded onto my system. This appears to have caused a conflict so I did a "rmmod" of both modules. Than I only loaded the orinoco and orinoco_pci. This appears to have resolved the conflict and now the wireless WMP11 card works again.

I am use to REDHAT and SUSE use of the modprobe.conf file but Ubuntu doesn't seem to have one nor does it have a conf.modprobe or modules.conf or anything that resembles the configuration file i need. Can some explain how ubuntu handles this or point me to the documentation.

Thanks,

John

---

### Post by chili555 on 2007-03-14
Please add the following to /etc/modprobe.d/blacklist:```
#chili sez no to prism2
blacklist prism2
```

You will probably have to reboot to be sure.

---

### Post by Jsteinman on 2007-03-15
Thanks!

I black listed the "prism2_pci" that fixed the problem. Still not sure why that an upgrade would change this but I am happy to be back up and running.

Thanks again, 

John

---

### Post by merhawie on 2007-03-24
Just wanted to say thanks! This worked flawlessly!

---

### Post by mickymouse111 on 2007-09-23
I have just upgraded from 6.10 to 7.04. I also have a WMP11 wireless card

I seem to have the same problem. 
I have tried installing the linux-wlan-ng-firmware and linux-wlan-ng packages

this seemed to work, then i rebooted ubuntu and suddenly my card stoped working again!

I followed the instructions on this page
[https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan)

Now I cant even find my card under the network manager.  Whereas before it was there but it would not connect to anything.

uname -a 
linux max-desktop 2.6.20.-16-generic #2 SMP fri aug 31 00:55:27 UTC 2007 1686 GNU/Linux

This is the output from lshw after I followed the instructions on blacklisting the prism drivers

*-network UNCLAIMED
description: network controller
product: prism 2.5 Wavelan shipset
vendor: Intersil Corporation
phyiscal id: 8
bus info: pci@01:08.0
version: 01
width: 32bits
clock: clock 33MHz
capbilities cap_list
configuration: latency=32
resources: iomemory: feaff000-feafffff irq:20

---

