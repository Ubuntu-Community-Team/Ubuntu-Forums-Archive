---
title: "Atheros Wireless Not Showing up... Help Required"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Faithman on 2008-09-19
Ok, so I am sure that you all have read about 1000 of these posts, but mine is somewhat special, or I am straight up mentally disabled haha. So I have been working on getting my AR242x Atheros Card working on my Toshiba Satellite A215-S4757 for, no joke, 4 FULL days now and I've gotten no where. I have searched the forums repeatedly and I've used everyones methods here but still not having any luck whatsoever. If anyone could please help, let me know if you need more information on my system and what not and I would be more than obliged to give it. :)

Thank you

Update: *-network DISABLED
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wlan0
                version: 01
                serial: 00:1b:9e:36:86:aa
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

This is what I am getting now, advise on what I should do?

---

### Post by hooflung64 on 2008-09-19
> **Faithman said:**
> Ok, so I am sure that you all have read about 1000 of these posts, but mine is somewhat special, or I am straight up mentally disabled haha. So I have been working on getting my AR242x Atheros Card working on my Toshiba Satellite A215-S4757 for, no joke, 4 FULL days now and I've gotten no where. I have searched the forums repeatedly and I've used everyones methods here but still not having any luck whatsoever. If anyone could please help, let me know if you need more information on my system and what not and I would be more than obliged to give it. :)

Thank you

I just installed 8.04 through the system update over wireless on my P205-S6237 which has an AR242x Atheros card as well. Worked fine on 7.10 but after booting into 8.04 there is no wireless support now. I can see it in Device manager but cannot see anything related to it when I lsmod.

We might have to install the mad drivers by hand =/

---

### Post by Faithman on 2008-09-19
Oh geeze, I've been reading around, and with a few people, when they updated, it knocked it all offline. Thats probably the biggest part that scares me, is if/when I finally do get it working, and theres an update, I may end up in the same boat again... Paddless :(

---

### Post by Cuba71 on 2009-08-17
I have a Toshiba laptop A135-S4527 w/ an Atheros AR242x, and it works fine with Ubuntu 8.10, 9.04 and 9.10 alpha-4.
It uses the ath5k driver. 
Have you tried under Windows?

---

