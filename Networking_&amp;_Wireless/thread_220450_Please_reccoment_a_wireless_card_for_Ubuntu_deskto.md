---
title: "Please reccoment a wireless card for Ubuntu desktop"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by blastoff on 2006-07-21
I have 5.10 "breezy badger" on a dual boot with windows (maybe soon to ubuntu only) desktop.  

I want to purchase a wireless card (b/g) for the system.  

-It must have good reception (doesn't ahve to be best, just better than your average notebook internal card.  Use a dell truemobile 1300 for reference if possible)
-I want something that is preferably supported by ubuntu and very easy to configure.
-Obviously cheaper is better, but it must meet the above two requirements.

I don't care if it's PCI or USB, whatever works best and is easiest to set up.

Please reccomend me a card to use!  Thanks in advance to all.

---

### Post by tturrisi on 2006-07-21
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=706706&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=706706&CatId=367)

---

### Post by blastoff on 2006-07-22
is this for a desktop or laptop?

---

### Post by psycosmyth on 2006-07-22
Crazy me started a thread for this again. I've tried many and well, D-link seems to be recognized in the Ubuntu world. I can't get Knoppix or Feather to detect it but the kernal build for Dapper picks it up, for Breezy? I don't know.

---

### Post by orb9220 on 2006-07-22
Just be wary with D-Link or any other for that matter for playing musical chipset.

Example: friend has a D-Link G510 which uses a different chipset then the G510 ver B1 that I have which is based on the aethros chipset. His requires config with ndiswrapper mine works out of the box,

---

### Post by tturrisi on 2006-07-22
> **blastoff said:**
> is this for a desktop or laptop?
for a notebook.
> Just be wary with D-Link or any other for that matter for playing musical chipset.
All manufacturers evolve their products. The dwl630 & dwl650 (made in the past couple years to present) use an atheros chipset and work out of the box with mad-wifi drivers which get installed when one installs the linux-restricted-modules package for the kernel being used.

---

### Post by blastoff on 2006-07-22
can anyone reccomend a card for a DESKTOP (or usb is fine, so both)?

what about [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211)

---

### Post by psycosmyth on 2006-07-23
what I've noticed is the good cards with "speed boost" or whatever gimmik they use to up the price tend to conflict with most kernel builds. I can't verify this but I went through several before I got the WNA-1330. It helped that the clerk was aware of Linux issues and let me return the ones that failed.
I havent tried any for my desktop yet, it's still in XPrison.

---

### Post by JSVH on 2006-07-24
I would also looking for a wireless card for a Ubuntu Desktop. Any help would be welcomed. I am looking for similar things: work out of the box, good signal, lower cost.

-John

---

### Post by fragmented_user on 2006-07-26
I've got a WG311 NETGEAR card on my box. its got 54mbps Wireless G and worked almost immediately (one minor adjustment needed).

---

### Post by ubercat on 2006-07-26
If you can live with an older 11.b card (WEP), find yourself an old Cisco aironet 350 on ebay or on the net. They work out of the box, even on Dapper! I dumped my Belkin F5D6020; the card borked after update on Breezy (drops connection unless I use a keep-alive beacon), and it's really broken under Dapper. I've found differences on older laptops as well. Some Dell notebooks, circa 2002, can act up when initializing the hotplug system with the pcmcia card plugged in unless they're patched -- it involves the integrated sound/video chipsets in some of these units.

As far as 11.g WPA cards, search the forums here: there are many ongoing discussions on the subject.

good luck!

---

### Post by sidlinux on 2006-07-26
If you have a desktop or laptop with USB, I recommend you get the Linksys WUSB11 Ver 2.6.  This is a USB device running at 11Mbps.  You may need to get it from eBay unless you can find it at some stores.

If you have a laptop with a pcmcia slot available, another card you may consider is the Dell TrueMobile 1150.

These are the only cards that worked out for me out of the box (with Dapper Drake) without configuring anything.  I encourage you to switch over to Ubuntu 6.06 if you haven't.  You won't be disappointed.

Sidney

---

