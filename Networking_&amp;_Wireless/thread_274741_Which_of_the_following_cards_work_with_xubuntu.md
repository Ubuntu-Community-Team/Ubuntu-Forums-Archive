---
title: "Which of the following cards work with xubuntu?"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by nhelke on 2006-10-10
Hi!

I need to equip my xubuntu machine with 802.11b/WiFi capabilities..

This machine is going to be donated to my school so I do not want to spend a lot of money.

I have seen mixed messages on the internet. Different people reporting success and failures with ubuntu and these cards.

I wish once and for all to collect confirmed information about these cards along with instructions for their use.

Here is a list of potential cheap WiFi cards available at my local PC hardware store, in ascending order of price:

[LIST]
[*]ZyXEL G-302_V3 (ZYX-2414)
[*]MSI PC54G3 Wireless
[*]ROLINE RWA-54
[*]TRENDNET TEW-423PI
[*]D-Link DWL-G510
[*]US Robotics USR805418
[*]NETGEAR WG311IS
[/LIST]

If any one has positive or negative experiences (with contextual information) with any of these cards  I would be most grateful for the insight.

---

### Post by x64Jimbo on 2006-10-10
Your best bet is to look at chipsets rather than model numbers. The chipset is what determines its compatibility. 
As far as getting a card in your local store, you'd save a lot of money if you shopped online. Ralink chipsets are pretty well supported under Linux and those cards can be had for less than $20 online
Example:
[http://3btech.net/ch5480wipcne.html](http://3btech.net/ch5480wipcne.html)
Driver pages:
Manufacturer: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)
Open Source: [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

---

### Post by gvgerman on 2006-10-10
I found this helpful: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by huygens on 2006-11-19
I have the MSI PC54G3 and it works fine under Ubuntu 6.10 (Edgy Eft) using the open source driver, however because of a [bug in the default Edgy driver]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117") installation, I had to follow an [how-to]("http://ubuntuforums.org/showthread.php?t=296822") before I could use it. But it was easy and it works like a charm.

However, it [might not work with NetworkManager]("http://live.gnome.org/NetworkManagerHardware") (I don't use it as my computer is a desktop, would be usefull only if it was a laptop).

Huygens

---

### Post by x64Jimbo on 2006-11-21
I use NetworkManager on my desktop. Why wouldn't you find it useful?

---

### Post by FrodoB on 2006-11-21
Find something with an Atheros chipset like this:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0)

If it is Atheros it should work out of the box.

---

### Post by x64Jimbo on 2006-11-22
I agree. Atheros chipset cards have been my choice for several years now. They're great for packet injection ;)

---

### Post by FrodoB on 2006-11-22
I should add for the record that Atheros devices that are USB do not work with madwifi and would therefore require ndiswrapper. I do not recommend that. Zydas zd1211b or Ralink rt73 devices would be better for USB.

---

