---
title: "Out-Of-The-Box"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by ts51 on 2006-08-03
Hi! 
 
I know that there is a whole page on supported wireless cards, but I wanted to know if someone had bought a card that worked right out the box. What I mean by this is that they inserted the card into the computer, booted up, typed in their ip, gateway, etc; and had internet. I currently have a Belkin F5D7000 version 2000 and I am getting fed up with trying to get it to work. If any one had a card that worked as I described above let me know exactly what it is called and where I can buy it. 
 
-ts51
 
By The Way: It needs to work on Ubuntu 6.06 and support 802.11g networks. Also if you have the Belkin F5D7000 and got it to work, let me know how you did.

---

### Post by spd106 on 2006-08-04
I have an atheros based DWL-650 Cardbus adapter that works out-of-the-box due to the included madwifi drivers. Though I do get better results and more features with the newer madwifi-ng.

For me Network Manager will make wifi far easier to use, but it still doesn't work with my card yet.

I also have a Belkin F5D7000, I got it to work with the bcm43xx driver using the bcm43xx-firmware package, but it does limit the data rate to 11Mbps and I have to scan for APs before connecting because I set the AP disble essid broadcast. Once this project is improved I think many more people will use it instead of ndiswrapper.

---

### Post by drewsimon on 2006-08-04
I've had such trouble getting wireless to work. I'm probably going to just buy a card that a friend of mine has got working in Ubuntu. 

Are there any wireless cards native to ubuntu? Spd10-- Did I understand you correctly, does ubuntu come with madwifi already set up?

---

### Post by spd106 on 2006-08-05
> Are there any wireless cards native to ubuntu? Spd10-- Did I understand you correctly, does ubuntu come with madwifi already set up?

Yes, ubuntu has the older madwifi drivers included in the kernel restricted modules package, which is usually installed by default. Dapper (and edgy) also seem to have some madwifi-ng modules. But I'm not sure which version they are or how to enable them (/lib/modules/2.6.15-23-386/madwifi-ng).

For a list of compatible cards look in [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) most of these entries were for breezy, but most should still be accurate. Be very careful when choosing a card. If you know someone who already has one working I suggest you get them to help you. A lot of the cards that work best are difficult to obtain now. I got lucky with mine, someone had returned it so I got a 15% discount.:D

---

### Post by reacocard on 2006-08-05
intel 2200 b/g. worked like a charm ootb.

---

