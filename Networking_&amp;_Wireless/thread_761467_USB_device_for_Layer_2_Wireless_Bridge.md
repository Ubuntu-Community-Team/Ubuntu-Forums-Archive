---
title: "USB device for Layer 2 Wireless Bridge"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by pmorch on 2008-04-21
I realize that this may sound as a FAQ; but I haven't found an answer yet: I want to purchase a USB wireless interface, and use it to create **a layer 2 bridge with my ethernet**. 

Bridging with wireless apparently [is not trivial with linux]("http://www.linux-foundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21"). "Many wireless cards don't allow spoofing of the source address" 

With ethernet I know it is a trivial matter of some brctl, ifconfig magic and so please don't point me to brctl or standard bridging info - it doesn't work with wireless without carefully selected hard- & software which is what I'm asking about here!!!

And yes, I can use iptables / masquarading, but that is not a layer 2 bridge! I can also use parprouted for proxy arp, but that is also not a layer 2 bridge although it comes closer. While those approaches have their uses, I want a real layer 2 bridge: a single subnet, broadcast and everything

I'm thoroughly confused: This is a limitation in the wireless driver, because it needs to support "WDS" right? Which drivers support this? Do any of these drivers support an USB wireless device?

Or is there a better place / forum to ask?

Basically, I just want a USB wireless device, that works for Gutsy out of the box, supports WEP, WPA, bridging and that won't give me any hassles. I'm prepared to pay for it too, if need be! :D Or does no such thing exist?

Peter

P.S.: I've found several compatibility lists e.g. [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), but I don't understand how to determine whether I can create a layer 2 bridge with the supported hardware.

---

