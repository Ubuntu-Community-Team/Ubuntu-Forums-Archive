---
title: "Wireless driver constantly disabling itself."
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Yenool on 2008-11-08
First and foremost, hello all.  This is my first time posting on this forum!

Getting down to business, the problem that I'm having has to do my wireless network card.  It isn't really the end of the world, I can enable my wireless card in "Hardware Drivers" where the card is called "Broadcom STA wireless driver" and it works fine.  I have had some trouble with it, but I got it working eventually.  Where my problem lies is that every time I restart my computer "Hardware Drivers" still has a tick in the "Enabled" box but it say "Not is use" in the status column.  So I can get it working again by disabling and re enabling it, but it's just a pain to do that every time I want to use it.

My wireless card according to lshw is:
               description: Network controller
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0

I know it says it's not installed but that's because I haven't disabled and re enabled the card this boot up.

What I have tried to fix it is uninstalling and reinstalling it with restarts mixed in, in every order I can think of; tried using ndiswrapper instead; and using the BCM firmware extractor that can be found in the package manager (epic fail) and this problem still soldiers on.

If it makes any difference, I'm using a dell studio 1535, Ubuntu Hardy Heron 8.04.1 amd64.

Any ideas you guys can come up is greatly appreciated.

---

