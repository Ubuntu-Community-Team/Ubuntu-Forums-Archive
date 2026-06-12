---
title: "knetworkmanager ipn2220 ndiswrapper"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by j00z76 on 2008-09-09
My laptop has an IPN-2220 WiFi card. It works through ndiswrapper. My problem is with knetworkmanager. As I switch my computer on, knetworkmanager doesn't show any available networks (it should show a few). If I check available networks with ```
sudo iwlist wlan0 scan
```, I get ```
None found
```. ndiswrapper is loaded and works.

In order to get my wifi card to work, I need to manually assign it an ESSID (say using iwconfig). As that happens, knetworkmanager reacts, and starts connecting! I can scan with iwlist and the card works as expected

What's going on here? Do I need to manually iwconfig my card so that it has an ESSID by default? What's going on!


Thanks!

---

### Post by j00z76 on 2008-09-11
> In order to get my wifi card to work, I need to manually assign it an ESSID (say using iwconfig). As that happens, knetworkmanager reacts, and starts connecting! I can scan with iwlist and the card works as expected

I solved this by having an iwcofing wlan0 essid SomeSuch in my /etc/rc.local file. This seems to "switch" the card on, and knetworkmanager and friends seem to work.

---

### Post by Kevbert on 2008-09-11
The other way to get wireless working is to install the network manager for gnome with
```
sudo apt-get install network-manager-gnome
```
in Konsole and then reboot.  This method seems to work fine in Intrepid.

---

