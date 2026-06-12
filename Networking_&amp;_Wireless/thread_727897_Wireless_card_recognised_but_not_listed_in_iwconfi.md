---
title: "Wireless card recognised but not listed in iwconfig"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Giacecco on 2008-03-18
Dear all,
I have just bought an **HP G6000 **laptop, apparently quite a good compromise between price, specifications and performance. I am trying to run **Ubuntu 7.10 ** 64-bit on it, and I have been successful until now but for the wireless configuration.

The G6000 mounts an **Atheros AR5006EG**, that I expected to be recognised by Ubuntu without any issues, once the "restricted drivers" are enabled. In fact it comes out correctly in the **lspci **list:

14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

**BUT ** it does not in **iwconfig**:

lo        no wireless extensions.
eth0      no wireless extensions.

**I have read the docs** at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) but the instructions take for granted that once lspci is fine, iwconfig shall be, too.

Was I lucky enough to buy the only laptop whose wifi chipset is not yet supported by Madwifi? (see [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679))

The card is enabled in the BIOS and I used it without any issues using the pre-installed Vista that I promptly removed off my sight. 

What's your advice?

Giacecco

---

### Post by dca on 2008-03-18
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
 
I think I have one as well in my Acer...  If you look in 'System -> Preferences -> Hardware Information' on the menu does it reference it as OEM Vendor:  AMBIT Systems???

---

### Post by dca on 2008-03-18
If your criteria matches mine, I used this post to get it working...
 
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

