---
title: "Network manager driving me crazy"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by timmay on 2007-02-17
Firstly I will start by saying that the ability to change networks several times per day between WEP encrypted, WPA encrypted and open networks is essential for me. It is also essential to be able to connect to networks that aren't give out DHCP.

Now network-manager is good for connecting to open, WEP and WPA networks and makes switching networks very easy. However it is not possible to connect to a network that is not giving out DHCP with network-manager! This is a big problem when fault finding networks and I was very annoyed that to keep things simple I needed to restart and boot Windows as that in this situation is better.

Network manager has also started having a mind of it's own. Annoyingly if I've had to manually configure the wireless interface I can't switch back to configuring that interface with network-manager without a reboot. Network-manager just keeps saying "no interfaces found" even with the interface un-configured and enabled in system > administration > networking.

Maybe this isn't the right place to be saying this ... I don't know. Is there a development forum for network-manager where I could discuss this problem.

---

### Post by nachotronics on 2007-03-02
Hi, you may try using wifi radar also, it ca configure different ip settings for different networks, but you'll still need nm, because wifiradar can't connect to protected networks itself

Hope this helps.

---

