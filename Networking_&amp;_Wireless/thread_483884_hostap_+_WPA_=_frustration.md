---
title: "hostap + WPA = frustration"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Blue Lightning on 2007-06-25
Hi all,

I've been attempting to connect to a WPA-encrypted wireless network using a NetGear MA311 PCI wireless card with the hostap driver under Kubuntu Feisty, but so far I haven't had any luck. KNetworkManager shows the network in the menu, and if I just click on it it brings up the Connect dialog but only allows me to select WEP from the encryption drop-down - WPA Personal is not shown. Hovering over the network in the menu shows that NetworkManager thinks it is a WEP-encrypted network instead of WPA. I also tried connecting directly to the network using the "Connect to Other Wireless Network..." option and manually entering the details, but it just sits at the "Activation Stage: Configuring device" part and then eventually gives up without connecting.

I found some bug reports on Launchpad that looked relevant, one of them suggested stopping NetworkManager and running wpa_supplicant directly. I figured out how to do that, and used wpa_cli to do a scan, but unfortunately it shows up as being WEP in there as well.

Interestingly when I connect to this same network from my laptop which is also running Kubuntu Feisty, it connects perfectly out of the box using KNetworkManager (although it has an Intel Pro Wireless card and uses the ipw2200 driver, so the situation is a bit different).

Any ideas?

EDIT: I just purchased an Edimax EW-7128g card (based on the Ralink RT2561 chip), replaced the MA311 with it and got the exact same results. This would seem to suggest it is not a driver issue (or if it is, both of the drivers have the same problem...)

---

