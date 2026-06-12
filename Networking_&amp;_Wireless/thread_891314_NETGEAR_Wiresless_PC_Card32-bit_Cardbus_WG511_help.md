---
title: "NETGEAR Wiresless PC Card32-bit Cardbus WG511 help"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by xnerdx on 2008-08-15
Hey everyone,
  I have a Toshiba laptop that I bought on sale at Walmart, it has a built in wifi adapter of course being a new laptop and such. Anyways due to the fact that this adapter is in-closed inside the laptop I can not get the signal I SHOULD be getting. I have an express card port on the left hand side of my laptop and I am running Ubuntu 8.04. I "plug" the adapter in and nothing happens at all. Ubuntu doesn't do anything just sits there like I have done nothing and the two lights on the card stay unlit. If anyone can tell me what must be done to get this card to work that would be a great help! I hope that this card will increase my wifi capabilities because I recently lost my home internet connection and have to go outside to pick up networks in the area. Sitting next to my home network and running the airmon-ng command to sniff for networks I get a "pwr" of only 68 or so which is why I am assuming that due to the fact that the Wireless card in in-closed within the laptop that I get such a poor "pwr" in airmon-ng. Thank you anyone who an help me!

---

### Post by xnerdx on 2008-08-16
Can anyone help? Does anyone know if this card would even be of benefit?

---

### Post by lisati on 2008-08-16
The Toshiba laptop I have (one of the A100 satellite range, about two years old) has a WiFi switch on the right, just in front of two of its USB ports. When Wifi is enabled, an LED is lit up orange. Maybe your laptop has a similar switch somewhere.

Your enclosed Wifi card should show up when you type the following at the terminal: ```
lspci | grep 802.11
```

---

### Post by xnerdx on 2008-08-16
Thanks for the tip I do have that switch flipped on, I just get a somewhat of a poor signal. I want to figure out how to install an "antena" of sorts to the in-closed wifi card. I found this page that might be of use to myself and any other users with this problem, but I have not read it yet! Give me feedback and I will be sure to do the same!

```
http://translate.google.com/translate?hl=en&sl=de&u=http://de.gentoo-wiki.com/WG511&sa=X&oi=translate&resnum=10&ct=result&prev=/search%3Fq%3DNETGEAR%2BWireless%2BPC%2BCard%2B32-bit%2BCardbus%2BWG511%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26sa%3DG
```

---

