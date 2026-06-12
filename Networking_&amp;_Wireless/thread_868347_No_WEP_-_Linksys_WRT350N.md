---
title: "No WEP - Linksys WRT350N"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by JoneYee on 2008-07-23
Hello all, seems like I am asking a question a day as I continue to spin up on this.

Came home today, and I had an external router problem which required a soft reset of my router and cable modem.

Now I cannot reconnect to the wireless as the wireless router is WEP encrypted and when I go into Network settings, WEP is not an available dropdown for the password type (only WPA and WPA2 are there)

I did a sudo gedit /etc/network/interfaces and left only the following lines and did a reboot:

cat interfaces
```
auto lo
iface lo inet loopback
```

Rebooting left me in the same place.

I know the router is good, as the Server (wired) and the only Windows client (work perk - wireless) are both reaching the external internet.  

SO, why would Network Settings fail to see the WEP, or offer the WEP password type, but see the router?  

I have soft rebooted the router twice, including a sequence where flea power was drained from both the router and modem to ensure a full reset.

---

### Post by JoneYee on 2008-07-23
On the 3rd reboot, I have a wireless signal indicator for the first time in the panel and no idea how it got there and all WEP encryption options were listed.

So I guess the lesson learned for me is that I need to try three times not two before seeking out assistance.

---

