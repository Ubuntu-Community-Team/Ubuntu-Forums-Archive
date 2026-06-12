---
title: "belkin f5d7010"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by ljonesj on 2007-06-28
belkin f5d7010 this link [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=578281&CatId=2698](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=578281&CatId=2698)
will this work out of the box with ubuntu 6.06 lts and up and if it does will kismet work

---

### Post by t4thfavor on 2007-06-28
Looks like you will be using ndiswrapper for that device. Which in my opinion is not a good solution.

If you want a decent card with linux support grap a Cisco, or Netgear card. Make sure the Netgear card has an atheros chipset. Also if you have an internal minipci slot Intel cards work quite well.

EDIT: Ndiswrapper uses the windows drivers which do not allow for monitor mode, which is what Kismet uses.

---

### Post by ljonesj on 2007-06-28
i know i have a laptop with a broadcom internal card which i hate so how do i tell if it has the atheros chip

---

### Post by ljonesj on 2007-06-28
what about d-link is that a bust which cards are my best bet for the atheros chip

---

### Post by t4thfavor on 2007-06-28
I dont think any of the dlink cards are atheros. Cisco cards are atheros, and most of the 108mbps netgear cards. Just do a google search on the model number of the card and you can usually find it.

What kind of laptop do you have? If its not an HP or IBM you can just remove the old broadcom card, and install the new atheros, or intel card where it was.

You can pick up an atheros minipci card for < 50USD, and an intel card for < 20USD.

I would recommend that you go the minipci route since it will give you better antennas and not stick out of the laptop.

I am sure if you go look at some cards in your price range, then google them you can find out if they will work.
have a look here
[http://cgi.ebay.com/New-ATHEROS-108Mbps-Mini-PCI-WiFi-Wireless-MiniPCI-card_W0QQitemZ230145472061QQihZ013QQcategoryZ45001QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/New-ATHEROS-108Mbps-Mini-PCI-WiFi-Wireless-MiniPCI-card_W0QQitemZ230145472061QQihZ013QQcategoryZ45001QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[http://cgi.ebay.com/Atheros-AR5006XS-SUPER-AG-wireless-miniPCI-card-108Mbps_W0QQitemZ290132299206QQihZ019QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Atheros-AR5006XS-SUPER-AG-wireless-miniPCI-card-108Mbps_W0QQitemZ290132299206QQihZ019QQcategoryZ45000QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by ljonesj on 2007-06-28
its a compaq laptop so its hp so most of the netgear cards that are 108mps are what about wg511 v2

---

