---
title: "Can you recommend me a good USB 5 GHz wifi adapter for Ubuntu?"
date: 2023-01-12
forum: Networking &amp; Wireless
---

### Post by SpaceManJack on 2023-01-12
Thanks. I'm using a PC and it was built in 2015 so it only accepts 2.4 GHz wifi signals.

---

### Post by TheFu on 2023-01-12
I'm confused by the "USB" in your search for a router?  That really doesn't make any sense.  Do you actually want a router or just a wifi dongle for an existing computer and existing network?

I'm going to assume "wifi router" is really what you mean and ignore the USB part.

Not much information or planned use has been provided.  Location matters greatly.  We tend to put wifi routers in a corner, not central to the place we want full coverage.  Will there be 1 client device or 10 or 50?  That all matters.  Home routers will struggle with lots of wifi devices.  Ubiquiti APs can handle many more.
I suspect you don't want 802.11a wifi device, though technically, it is 5.8Ghz. That's from the 802.11b timeframe where 22Mbps was the fastest possible.

I also think you probably want an AX (wifi-6) device to get the speeds and security it claims. Wifi-5 devices will be cheaper, if that is an overriding consideration.

Are you a home user or small business?
Is a guest network necessary?
Do you need multiple wifi networks to keep IoT and kids game consoles separate from adult laptops, tablets, and phones?
Do you care at all about security, just a little, or are you paranoid (with reason)?

There are many different opinions about the best routers and how to set them up.

I keep routing separate from wifi.  Routers can last 10+ yrs, if you leave off the wifi and use a separate AP-only device just for wifi.  Along that line, it means that small business vendors tend to be best at support for more than 2-3 yrs.  That puts you into a low-power x86-64 platform, say an APU2-based system where you load pfSense or OPNSense or openWRT yourself for the routing, then get a quality AP from someone like Ubiquiti.

Mikrotik makes all-in-one small business routers and is known to provide timely patches for issues.
Ubiquiti tends to sell wired routers and wifi-APs separate.  This usually means you'll replace the AP 2-3x more often than the router to have the newest speed and security enhancements that newer wifi protocols promise (but seldom actually deliver). Both Mikrotik and 

If you aren't interested in the added features, capacity, and better security that OPNSense, Mikrotik and Ubuquiti offer, then I suspect you just want a cheap, home router, that has long support periods.  If that is the situation, thanks to the FTC in the USA, Asus was caught doing really poor security in their routers around 2014 and part of the settlement was that they would implement world-class support after the sale.  Effectively, Asus routers have much longer firmware support periods - usually 2x longer than others due to that legal agreement with the FTC.  We all win because of this.  No need to buy their $300 wifi-router either.  For an average small home, even the cheap $70 Asus wifi-routers are well supported.  They can even be used as an AP-only, if you want a better router, but still need wifi.  The cheap Asus wifi router in AP mode is about 40% less cost than a much more capable Ubiquiti AP-only device.  Ubiquiti handles many more concurrent clients, but in a home, that probably doesn't matter.

Since I'm not in the market for a router or AP now, I don't have an exact model for any of these options, but it is my short-list of vendors to look over. Beware that there are lots of cheaper and more expensive router/wifi vendors. That doesn't relate to their firmware support.  Looked for Asus wifi routers on Amazon.  Found a wifi-6 version, RT-AX1800S, for $70.  For $80, a compatible USB dongle is included.  The RT-AX55 is also interesting for the price.

If you have an existing wifi router and it hasn't gotten any firmware updates in the last 2 months, it is time to get new hardware with better support.  I see patches for my OPNSense router every 2 weeks, as an example.  No router should go more than 3 months between firmware updates. Security issues arise all the time and need to be addressed. Updated firmware is required, just like we need to patch our computer OSes weekly.

---

### Post by chili555 on 2023-01-12
> I'm going to assume "wifi router" is really what you mean and ignore the USB part.By chance, does OP want a wireless router with a USB port to which s/he may connect a storage device, for example?

---

### Post by TheFu on 2023-01-12
> **chili555 said:**
> By chance, does OP want a wireless router with a USB port to which s/he may connect a storage device, for example?

I hope not.  Pretty much every router that supports storage has a history of security failures which leaked the data on that storage over the internet. Some vendors patched that code 5 times, as new bugs were found.  At this point, best not to even consider that as an option, IMHO.   

Unless the goal is to share all the information world-wide, then USB storage connected to a router is a great idea!

---

### Post by SpaceManJack on 2023-01-12
I edited the title sorry for the confusion. Yes I meant USB Wi-Fi adapter for 5 gigahertz.

---

### Post by SpaceManJack on 2023-01-12
I edited the title sorry about the confusion.

---

### Post by morrownr on 2023-01-12
> **scott130 said:**
> Thanks. I'm using a PC and it was built in 2015 so it only accepts 2.4 GHz wifi signals.

Chili555 has a link in the top sticky but I'll post it again:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Menu item 1 gives a lot of info so that you understand the background.

Menu item 2 gives info and links to a lot of good usb wifi adapters that work with in-kernel drivers.

Knowing exactly what you want would help as there are a lot of adapters. Do you need long range?

Nick

---

### Post by chili555 on 2023-01-12
> I hope not. Pretty much every router that supports storage has a history of security failures which leaked the data on that storage over the internet. Some vendors patched that code 5 times, as new bugs were found. At this point, best not to even consider that as an option, IMHO.

Unless the goal is to share all the information world-wide, then USB storage connected to a router is a great idea!Thanks. That's exactly the answer I hoped OP and subsequent searchers would gather.

Can you do it? Yes. It it safe to do it? Nooooo!!!

---

### Post by SpaceManJack on 2023-01-12
USB WiFi adapters aren't safe to use? 

I have a PC that was built in 2015 but it only accepts 2.4 GHz Wi-Fi signals, which means I need a USB wireless so I can get the 5 GHz signal.

I was hoping someone would just provide me with an Amazon link to a good USB wireless that works with Linux?

---

### Post by chili555 on 2023-01-12
> **scott130 said:**
> USB WiFi adapters aren't safe to use? Sorry if we were misunderstood. We meant to say that wireless routers...not wifi adapters...with a USB port for storage; i.e. an attached USB drive, are unsafe to use.

@morrownr's site is about as good as it gets: [https://github.com/morrownr/USB-WiFi/blob/main/home/The_Short_List.md](https://github.com/morrownr/USB-WiFi/blob/main/home/The_Short_List.md)

---

### Post by morrownr on 2023-01-12
> **scott130 said:**
> 

I was hoping someone would just provide me with an Amazon link to a good USB wireless that works with Linux?

[https://www.amazon.com/Panda-Wireless-AC1200-Adapter-Antennas/dp/B0B2QD6RPX](https://www.amazon.com/Panda-Wireless-AC1200-Adapter-Antennas/dp/B0B2QD6RPX)

The link I sent you to provided many links, many of which are to Amazon but if you want one link, see above.

---

### Post by TheFu on 2023-01-13
> **scott130 said:**
>  I was hoping someone would just provide me with an Amazon link to a good USB wireless that works with Linux?

"good" is subjective.  There are trade-offs.
* size (tiny, a 6inch antenna, antler antenna)
* coverage distance (same room, hotel wing, 500m through walls)
* environment (brick/foil-backed insulation)
* future support (history of the vendor updating the kernel software to resolve issues)
* cost ($10, $20, $50, %100+)
* Wifi standards to be supported?  Wifi-6, wifi-5, 802.11ac, 802.11N.  Others?

We all would like a tiny USB dongle that can barely be seen that has 500m distance with strong, fast, signals, that will get firmware updates for 25 yrs that costs $10.  Sadly, that doesn't exist.

What are your priorities?

---

### Post by mIk3_08 on 2023-01-13
> **scott130 said:**
> 
I was hoping someone would just provide me with an Amazon link to a good USB wireless that works with Linux?
Try this out. [Click Here]("https://www.amazon.com/usb-wifi-adapter-linux/s?k=usb+wifi+adapter+linux")

---

### Post by morrownr on 2023-01-14
> **mIk3_08 said:**
> Try this out. [Click Here]("https://www.amazon.com/usb-wifi-adapter-linux/s?k=usb+wifi+adapter+linux")

I strongly recommend against using this approach. The best way to make a usb wifi adapter purchase for Linux is to first learn because you cannot depend on the vast majority of sellers or ads to tell anything close to the truth. "Linux support" in an ad means NOTHING.

Recommend the following site as it will increase your knowledge and provide direct links to adapters that are known to work well with Ubuntu:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Menu item 1 gives background information. Menu item 2 provides information and links for 75+ adapters that are known to work well with in-kernel drivers.

Regards,

Nick

---

