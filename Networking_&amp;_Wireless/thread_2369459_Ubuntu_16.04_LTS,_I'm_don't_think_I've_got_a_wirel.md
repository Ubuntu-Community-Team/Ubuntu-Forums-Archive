---
title: "Ubuntu 16.04 LTS, I'm don't think I've got a wireless card and would like one"
date: 2017-08-23
forum: Networking &amp; Wireless
---

### Post by naomibrown on 2017-08-23
Hi,

I've read the sticky post, and I'm getting a bit confused! I have this pastebin [http://paste.ubuntu.com/25375919/ ]("http://paste.ubuntu.com/25375919/"). 

I don't think I've got a wireless card from reading it, but I'd like to get one. I've looked at the [wireless cards supported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), but the link for desktop computers at the top of the page for Passys about PCI cards says "The requested page could not be found."

Can I just choose any one of the PCI cards that works out of the box from the list, or is it more complicated than that? I read this a [wiki]("http://www.wikihow.com/Install-a-PCI-Card") on it and it seemed relatively straightforward to do. Any other/alternative advice? Do I need to check if I have a free slot first? If so, how do I do that?

Thanks - this may be a really stupid question or completely the wrong one!!!
Naomi

---

### Post by BenginM on 2017-08-25
Hiya Naomi , So you have a Dell XPS 8300 with no wireless card , looking at the specs in 

[http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_setup%20guide_en-us.pdf](http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_setup%20guide_en-us.pdf)
[http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_service%20manual_en-us.pdf](http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_service%20manual_en-us.pdf)

And according to [Jesse L from Dell]("http://en.community.dell.com/support-forums/network-internet-wireless/f/3324/t/19391424") , you'll need a Half Height Mini PCIe card for the slot on the XPS 8300 ..

[https://www.thinkpenguin.com/gnu-linux/mini-pci-mini-pci-e-mini-pci-e-half-height-guide-laptop-wifi-cards](https://www.thinkpenguin.com/gnu-linux/mini-pci-mini-pci-e-mini-pci-e-half-height-guide-laptop-wifi-cards)

I would get an Intel AC card ..
[https://www.intel.com/content/www/us/en/products/wireless/wireless-products/dual-band-wireless-ac-7260.html](https://www.intel.com/content/www/us/en/products/wireless/wireless-products/dual-band-wireless-ac-7260.html)

[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)


[https://wikidevi.com/wiki/Main_Page](https://wikidevi.com/wiki/Main_Page)
[https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux](https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux)

## Do not get a USB Wireless adapter. Terrible value, and extremely  spotty. a PCI-E card is wildly more  stable.

---

### Post by naomibrown on 2017-08-25
Thanks a lot for all the info! I've learnt loads :)

Can I just check that this one [on amazon]("https://www.amazon.co.uk/Intel-Wireless-N-Bluetooth-Internal-300Mbit/dp/B00N7474CS/ref=sr_1_1?ie=UTF8&qid=1503652839&sr=8-1&keywords=intel+dual+band+wireless+ac+7260") and this one [on ebay]("http://www.ebay.co.uk/itm/3160HMW-Wifi-Bluetooth-4-0-Dual-Band-Wireless-AC-7260-For-Intel-Dual-7260-SWTG-/331849612974?hash=item4d43c73eae:g:TdMAAOSwt7pXLK5i") are the same as the one you refer to? 

Also, I took off the case of my machine to have a look at it, so I would know what I'm doing. Is all I'm doing slipping the card into the part at the bottom left hand corner of the photo, next to where it is labelled? i.e. it would be facing flat down towards the floor?

[ATTACH=CONFIG]276507[/ATTACH]

Thanks,
Naomi

---

### Post by Bucky Ball on 2017-08-25
Yep, bottom left corner. Is there a slot under that red thing (presume that's a video card)? You are looking for a regular PCI slot. They are common and your computer should have a few of them down in the bottom left.

I strongly disagree with the 'don't get a wireless USB dongle' stance. In my experience with them, and I have used many over the years, if you do a bit of research and grab one that's compatible with your distro, it will work faultlessly. 99.9% of mine have. Using one right now (as the internal wireless card in my laptop has died!). I have only ever used one with my desktop since I built it a year and a half ago. 

Cheap, and if you live near a computer shop, easily obtainable. If not, there's always online.

A dodgy wireless chip is just that, whether on a PCI card or in a USB dongle. It's the make and model of the wireless chip being used by the device that counts, USB or PCI, not really even the manufacturer of the PCI card or dongle, if you follow me.

---

### Post by chili555 on 2017-08-25
> Yep, bottom left corner. Is there a slot under that red thing (presume that's a video card)? You are looking for a regular PCI slot.I respectfully disagree. Please see page 34 here: [http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_service%20manual_en-us.pdf](http://downloads.dell.com/manuals/all-products/esuprt_desktop/esuprt_xps_desktop/xps-8300_service%20manual_en-us.pdf)

I believe that the mini wireless card goes in what appears to be a grey connector just below and to the left of the fan. Then you connect the black and white antenna wires that we can see in your attachment.

By the way, BenginM asserts that you have an XPS 8300 but I see no confirmation in your original post. If it IS an XPS 8300, read the service manual page I mentioned and look inside the computer and I think it will all make sense.

I believe the card you linked at Amazon is correct.

[ATTACH=CONFIG]276510[/ATTACH]

---

### Post by chili555 on 2017-08-25
This is probably the location.

[ATTACH=CONFIG]276511[/ATTACH]

---

### Post by BenginM on 2017-08-26
The one you linked from amazon is the Wireless-N  version of 7260 which is fine , But the Wireless-AC is 3x faster if  your main router is AC and its a common standard nowdays. I suggest you  read about Wireless N Vs AC .. 

##
 [http://www.makeuseof.com/tag/everything-need-know-ac-routers/](http://www.makeuseof.com/tag/everything-need-know-ac-routers/)
[URL="https://www.forbes.com/sites/gordonkelly/2014/12/30/802-11ac-vs-802-11n-wifi-whats-the-difference/#3ed9adf23957"]https://www.forbes.com/sites/gordonkelly/2014/12/30/802-11ac-vs-802-11n-wifi-whats-the-difference/#3ed9adf23957
https://www.youtube.com/watch?v=7Xy31O1Twkc[/URL]

So even if your current main router is N only it will be compatible with a wireless-AC card and it will work at reduced speeds.
 
The one you linked from ebay appears to be the the Intel's [Wireless-AC 3160]("http://www.ebay.co.uk/itm/Intel-3160HMW-Wireless-802-11ac-Dual-Band-Mini-PCI-E-Wifi-Card-Replacement-/252174161216?epid=1048693788&hash=item3ab6c05540:g:HmgAAOSwXeJYCGAr")  from the picture which is fine too , am not sure why it's labeled in  the title as "Wireless-AC 7260" .. and this is why i don't trust amazon  or ebay! , i only trust the official site of a brand.

[This]("http://www.ebay.co.uk/itm/Intel-Dual-Band-Wireless-AC7260-7260HMW-Bluetooth4-0-Half-Mini-PCI-E-Wlan-Card-/192024852524?hash=item2cb592b82c:g:c9YAAOSwbsBXmaqg") appears to be the correct model .

I suggested the Intel Dual Band Wireless-AC 7260 for  the BT+ feature it has and the fact that the iwlwifi kernel driver will be  used for it which gets much love & support from the community . 

as well as the other newest Intel cards:
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)

Do  i see two usable PCIe x1 slots covered by that gpu!  you could most  likely fit a full-sized PCIe x1 or PCI (depending on which slot is  there) card 
                      below the GPU..

according to the XPS 8300 service manual which i linked earlier the mobo has 3 PCI Express x1 card slots ,and 1 Mini-Card slot.

so  your options seems to be a PCIe x1 wifi card, the Intel Wireless AC  8265 would be a good choose for that .  but a half-size mini PCIe card would be the cheapest  option. Get whichever card that fits your budget with the features you want :)

---

### Post by BenginM on 2017-08-26
chili, i spotted the Dell XPS 8300 from

```

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: tg3
```

in [http://paste.ubuntu.com/25375919/](http://paste.ubuntu.com/25375919/)

---

### Post by chili555 on 2017-08-26
> **BenginM said:**
> chili, i spotted the Dell XPS 8300 from

```

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
	Subsystem: Dell XPS 8300 [1028:04aa]
	Kernel driver in use: tg3
```

in [http://paste.ubuntu.com/25375919/](http://paste.ubuntu.com/25375919/)Ahhh! I see.

I'll be back to the forum as soon as I wipe off a few layers of grime from my thick glasses...

Thanks.

---

### Post by naomibrown on 2017-08-26
Right, I think I know where it should go now! :) 

Again, learning loads from the links :)

I'm going to have a look at my router later and work out whether it's AC or N!

Thanks,
Naomi

---

### Post by naomibrown on 2017-09-09
I think my router is an N. It's an ASUS one: [https://www.asus.com/Networking/DSLN14U/ ]("https://www.asus.com/Networking/DSLN14U/"). 

Even in that case is it sensible to buy the [AC card]("http://www.ebay.co.uk/itm/Intel-Dual-Band-Wireless-AC7260-7260HMW-Bluetooth4-0-Half-Mini-PCI-E-Wlan-Card-/192024852524?hash=item2cb592b82c:g:c9YAAOSwbsBXmaqg") so that if I get a faster router I'll not need to mess about changing it?

Thanks,
Naomi

---

### Post by chili555 on 2017-09-09
I'd buy the AC card. The difference in cost is likely to be just a few dollars. If it does not now, when your ISP offers fast speeds that take advantage of AC speeds and when you get a newer router, you'll be all set.

---

