---
title: "Concerns about Upgrading and Wireless"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by DrTaylor on 2008-05-30
I'm running Gutsy Gibbon, which I like fine, but I would really like to upgrade to Hardy someday soon. However, I have an Acer Aspire 5135, which has had notorious problems with the networking. I finally got the wirless working - Ubuntu didn't recognize the card properly and you have to download the Ubuntu driver and then add a patch to that in order to fix it.

My question is, will I have to go through all that again if I upgrade to Hardy? Does anyone know if my wireless driver would just carry over with the patch intact?

Thanks!

---

### Post by Ayuthia on 2008-05-31
> **DrTaylor said:**
> I'm running Gutsy Gibbon, which I like fine, but I would really like to upgrade to Hardy someday soon. However, I have an Acer Aspire 5135, which has had notorious problems with the networking. I finally got the wirless working - Ubuntu didn't recognize the card properly and you have to download the Ubuntu driver and then add a patch to that in order to fix it.

My question is, will I have to go through all that again if I upgrade to Hardy? Does anyone know if my wireless driver would just carry over with the patch intact?

Thanks!
There have been some changes to some wireless drivers in Hardy so there is a chance that you might need to do something.  Can you post your lshw -C network?  It will help determine your wireless card and also what driver it is using.

---

### Post by DrTaylor on 2008-06-02
This is what is shows when I run lshw:

 *-network
                description: Wireless interface
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wifi0
                version: 01
                serial: 00:1f:3a:4b:21:c4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless


But here's the best part. It's actually, I'd have to look it up, but I think its an AR5005EG, not AR5006. Ubuntu doesn't recognize it properly. What i have is the madwifi driver through Synaptic with a patch downloaded from the Atheros site.

My cranky computer and I thank you.

---

