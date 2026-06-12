---
title: "Laptop Wireless Network cards that work out of the box"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Heyholetsgogrant on 2006-11-10
Does anyone of any wireless network cards for laptops that work out of the box? meaning I buy it off the shelf and just pop it in and it works? I checked the support website for unbuntu and it says it several cards for net gear work out of the box. I looked a "NETGEAR WG511T 108 Mbps Wireless PC Card, 802.11g" [http://www.compusa.com/products/prod](http://www.compusa.com/products/prod)... eless_PC_Card

it says it works out of the box on the ubuntu support site "https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported," but "Has been reported to work out of the box, but a large number of users have had problems. See this HowTo for further details" If anyone can provide a link to best buy or compusa of a card that works out of the box that would be great!

Thanks,

Grant

---

### Post by plexi50 on 2006-11-10
Not sure of the model #'s since I don't have them with me now, but  my Belkin G card and Airlink SuperG card both worked with Breezy and Dapper out of the box. They also worked with Kubuntu with no issues. In addition, my Intel ipw2200 in my Dell lappy worked with no issues at all.

---

### Post by veruca on 2006-12-26
dynex (best buy brand) dx-wcnbc worked with out any effort at all. just configured the card to dhcp and put in the wep key and i was online. 45 bucks too, can't beat that.

---

### Post by tturrisi on 2006-12-26
That netgear card has an atheros chipset and will work just fine once you enable the multi-universe repositories and install the restricted modules package for your kernel.  Those modules contain the madwifi driver needed for atheros chipsets.  I have 2 atheros cards that work flawlessly.

---

