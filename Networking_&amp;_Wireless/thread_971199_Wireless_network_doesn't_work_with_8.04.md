---
title: "Wireless network doesn't work with 8.04"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by maxhoward on 2008-11-04
My wife's PC is running Ubuntu 8.04.  Ubuntu seems to be running OK but I can't get it to connect to the internet via wireless to the router on my PC.

I tried sudo -lshw -C network
 
and it listed Product:  bcm4306 802.11b/g LAN controller
              Vendor:   Broadcom Corp.

So I assume that the pc can recognize the wireless card.

Next I did a search for files containing "bcm43" and found 5 files containing bcm43xx, one of which was in the directory: kernel/drivers/net/wireless.

So now I assume that 8.04 loaded the drivers needed for this wireless card.

I've played around with the networking configuration but can't get it to work.  Any help would be greatly appreciated.

Thanks,

---

### Post by maxhoward on 2008-11-18
I discovered that the wireless adapter I was using (Buffalo WL12-PCI-G54S) would never work with Linux.  So a bought a new wireless adapter (D-Link WDA 2320), installed it, made a few adjustments in the System > Admin > Network settings and everything worked just fine.  Ubuntu recognized the adapter and nothing more was needed.

Problem solved.  :)

---

