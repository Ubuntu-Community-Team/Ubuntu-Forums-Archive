---
title: "Any PCIe or USB wireless adapter that works with 802.11ac networks?"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by negora on 2015-07-22
Hello:

It has passed some years since the first 802.11ac adapters came up in the market. But Linux still lacks drivers that support networks of type 802.11ac. After checking these sources:

[LIST]
[*][List of 802.11ac Hardware](https://wikidevi.com/wiki/List_of_802.11ac_Hardware)
[*][Comparison of open-source wireless drivers](https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers)
[*][About ath10k](https://wireless.wiki.kernel.org/en/users/Drivers/ath10k)
[*][About iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)
[/LIST]

I've came to the conclusion that only some Qualcomm Atheros and Intel chipsets are able to work with them, using the "ath10k" and "iwlwifi" drivers respectively. But with several issues. I've also tried to find PCIe or USB devices that contain these chipsets, but they all belong to internal parts of laptops; I want a single device for my desktop computer.

So Am I right? Is the support of 802.11ac networks still so poor?

Thank you!

---

### Post by TheFu on 2015-07-22
>  Is the support of 802.11ac networks still so poor?

Ask the manufacturers!  They write drivers for other OSes, but not for Linux.  THAT is the issue. The vendor.

---

### Post by negora on 2015-07-22
Calm down ;) . I'm not blaming Linux. I've been using it for ~10 years and I support FOSS. I know who to blame for the lack of drivers.

I'm just asking if you know about devices that are on sale, are Linux compatible, and are capable of communicating with 802.11ac networks.

---

### Post by negora on 2015-08-03
I have been checking again the available 802.11ac devices, and I've seen that some Intel devices for laptops seem to be well supported by the driver "iwlwifi", being able to connect to AC networks. Has anyone tried to use a card such as the Intel Dual Band Wireless-AC 7260 in a desktop computer (using a Mini-PCIe to PCIe converter)? I'm considering this possibility. Because the most of the AC adapters for desktop rely on the Broadcom 4360 chipset, which has very poor support in Linux.

---

### Post by negora on 2015-08-07
Well, finally I decided to try several devices by myself. First of all, and because I didn't want to discard other alternatives to WiFi, I purchased a kit of 2 PLC devices. It was the TP-LINK TL-PA8030P. My Internet connection is 300 Mbps. With this kit I achieved a speed of ~180 Mbps. at most. The ping was ~2.15 ms. approximately. In my opinion, a very good result. However, it was a little far from my 300 Mbps.

So I started to look for 802.11ac cards again, to choose if I kept the PLCs or returned them. I wanted to get the ASUS PCE-AC68 card, but because some users in this and other forums had had serious problems with the Broadcom chipset, I decided to go after network cards with the Intel and Qualcomm chipsets. First, I looked for cards with 2 spatial streams (2×2:2), with the Qualcomm Atheros chip. But it was impossible to find a reliable brand. Or at least one that I knew well enough.

Then I passed to search cards with Intel chipsets. Also with 2 streams. As in the previous case, all them were Mini PCIe. So definitively I needed an adapter to PCIe. But I found the Intel Dual Band Wireless-AC 7260 + Bluetooth for Desktop, which was just what I needed: a Mini PCIe card with an adaptor to PCIe and an external antenna for the desktop. But it was really expensive in my country. Fortunately, thanks to Amazon, I found a Gigabyte GC-WB867D-I, which had exactly the same chip. So I ordered it, together with an ASUS RT-AC68U router.

But just one day later, after reading about the possibilities of combining the RT-AC68U router with the PCE-AC69U card, my urge for this card came back, he he he. So I cancelled the order for the Gigabyte GC-WB867D-I (I was in time yet), risked a little more, and ordered the PCE-AC69U. After all, this situation wasn't new for me. Because I suffered from the same problems when I bought some of the first 802.11n devices in the market, ones from D-Link. There weren't good drivers for Linux back then.

So the router and the card have arrived today. I've tested both them a few minutes ago. And... I can't be happier with this decision!!! I was afraid of having to struggle with the native driver or ndiswrapper. But the version 6.30.223.248+bdcom-0ubuntu0.1 of the native driver works flawless :) . I've obtained a speed of ~250 Mbps! And the ping has been ~0.93! I guess that the driver has matured significantly since it was launched and there were so many complaints in the forums. I expected worse results, sincerely.

PD: now I've to decide if I return the PLCs o keep them for other purposes. But this is another story ;) .

---

### Post by Retro_Trinity on 2015-08-07
For what it's worth, you should be able to get speeds like that from 802.11n devices.  

The Realtek rtl8812ae seems to provide 300 mbps reliably in 802.11n mode (2.4 GHz) using the default kernel driver and connected to a Netgear 6300v2 router.  Getting it to work in 5 GHz mode is difficult/impossible since it seems to want to time out making that kind of connection.  In Windows 10, 650 mbps is attainable using the included driver in 802.11ac mode (5 GHz).  

As you have noted, the simplest course of action appears to be: buy cheap minipcie-to-PCIe adapter, buy cheap laptop card, buy external antenna + heatsink for card (maybe).  That's what Rosewill did.  They repackaged it under the name ac1200pce and sell it for around $40 in the US.  There's no telling what underlying chipset you're going to get, though.  Some of them are ath10k, some are rtl8812ae.

For Linux, the ath10k seems to be the best bet for 802.11ac.

---

### Post by negora on 2015-08-08
I've tested both the router and the PCIe card using the 802.11n protocol in the 2.4 GHz band, but the best speed that I've gotten has been ~100 Mbps. I guess that's thanks to their 3×3:3 spatial streams, because when I used my old 802.11n devices, a D-Link DSL-2740B router and D-Link DWA-140 USB, which were 1×1:1, the best that I achieved was ~40 Mbps. Then and now I've had to use a bandwidth of 20 MHz, because the 2.4 GHz band is so saturated here that using a bandwidth of 40 MHz the speed decreases a lot.

So my need really was to move to the 5 GHz band. But having to expend money I preferred to expend a little more and get good 802.11ac devices. I must admit that at the beginning I considered getting cheaper 802.11n devices... But then I changed my mind. Anyway, I still have to test 802.11n devices in the 5 GHz band, just because of curiosity. 

By the way, I didn't know about the Rosewill brand. I'll search for more information about them. I don't need that devices right now, but maybe I want something like that for my other computers. I still want to try an Intel or Atheros devices and see how it performs. Thank you ;) .

PD: checking 802.11n devices again, I forgot to comment why I did move to 802.11ac instead of moving to 802.11n devices better than what I had. In many specification sheets of 802.11n devices they indicated the number of antennas, but not of spatial streams. In practice, maybe they're equivalent, but I didn't trust in that. However, in several sheets of 802.11ac devices, I found references to the spatial streams, not only the antennas. That was more reliable for me.

---

### Post by Retro_Trinity on 2015-08-09
Okay, so you're having an issue with the 2.4 GHz band being saturated.  Makes a lot of sense.

---

### Post by Schotty on 2015-10-02
> **negora said:**
> I have been checking again the available 802.11ac devices, and I've seen that some Intel devices for laptops seem to be well supported by the driver "iwlwifi", being able to connect to AC networks. Has anyone tried to use a card such as the Intel Dual Band Wireless-AC 7260 in a desktop computer (using a Mini-PCIe to PCIe converter)? I'm considering this possibility. Because the most of the AC adapters for desktop rely on the Broadcom 4360 chipset, which has very poor support in Linux.

Hate to necro (not really that old, but ...) but whilst googling for a replacement AC card I found this thread and felt morally obligated to chime in.

I am currently running RHEL7.1 and use the Intel 7260.  Works well.  The one nag I have is that it does not support AP mode.  I bought a few and, well, have a few spares :D  My Soekris is still on N, and that was what I had been using to get off of crappy routers that I can't do what I want to do with em.  Eventually I suppose ... I caved in the meantime and picked up a Netgear that works very well and is stable.  But I want my Soekris doing all NAT, Firewalling, DHCP, and IPA work ALONG WITH being an AP.

That said, easily setup and one of the few that "just works" out of the box.  For a general puprose worksation or laptop, I can't rag on the Intel.  Cheap, great build quality, and perfect Linux support.  Since I have been in the "mood" shall we say, the local computer shop has an Intel rep that is amazing, perhaps I can have them bug him for me and see what they have to offer.  Wont hurt to ask.  I have no problem dropping a few bucks where its worth it.  But all the other units I found that "just work" are ath10k units that are wholesale mini-pcie boards.  With one exception:

[http://shop.compex.com.sg/wle900vx.html](http://shop.compex.com.sg/wle900vx.html)

I do have adapters that came with the Intels that "should work".  And the adapters aren't that badly priced.  But overall will put the total price plus shipping to over $100.  Most of the good ones are around $45-60 each, most in the $50 bracket.  But I did find this:

[http://www.hwtools.net/Adapter/MP1.html](http://www.hwtools.net/Adapter/MP1.html)

Any thoughts?  I have gone Intel primarily due to the great support in enterprise grade hardware and their very friendly stance towards us FLOSS folks.  But needs are needs.

And if you haven't heard of Soekris:
[https://soekris.com/](https://soekris.com/)

EDIT:: Got a pm stating my stupidity.  Apparently a while ago (I have had this card roughly since Thanksgiving, so nearly a year) the support for APs has been enabled.  One SSID only, but thats all I need.

---

