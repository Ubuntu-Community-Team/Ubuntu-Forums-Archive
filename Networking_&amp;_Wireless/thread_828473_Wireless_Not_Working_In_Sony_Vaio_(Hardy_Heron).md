---
title: "Wireless Not Working In Sony Vaio (Hardy Heron)"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by campero on 2008-06-13
I installed Hardy Heron on my Vaio vgn-nr123e and my wireless works just fine whenever I'm running windows but when I reboot and run Ubuntu the wireless turns off and there is no way to turn it on. When I installed Ubuntu it said it was using some private drivers because there were no open source drivers and in the hardware manager it says it is enabled and in use but no luck with the Wireless. 
Any ideas? I'd really appreciate the support I can get.

My windows device manager says I have a:
LAN-Express AS IEEE 802.11g PCI-E Adapter

---

### Post by rlzyoner on 2008-06-14
You could download ndiswrapper (a tool for linux that allows user to use windows wireless drivers), this is available via Synaptics
Once downloaded and extracted etc, point ndiswrapper to the drivers located on your windows partition.
This instructs ndiswrapper to use these drivers.

Once you do this, open a terminal and type in ndiswrapper -l (this will list the installed drivers.) Just ensure that your driver is listed.

Reboot and you should be good to go.

---

### Post by campero on 2008-06-18
Thanks for your advice. I'm no expert in linux, could you be a little bit more specific how to point ndiswrapper to drivers in my window partition. 

Thanks again for the help

---

