---
title: "Compaq Evo N620c  Wireless + Wpa = Freeze"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by gintonic on 2008-04-29
Hi,
i've configured my wireless adapter ( multiport wlan 200 ) as explained at the link

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

The wireless card seems to work correctly with open network or wep encryption. I can see on network manager applet the near wireless network.

My wireless router has hide essid and wpa-psk encryption configured.

When i try to configure ( with network manager, wicd, or manually ) wpa-psk encryption my notebook freeze. The two leds on top left blink and the only way to reset is remove battery.

Now i've upgrade to Hardy (8.04) release but the problem still remain. 

Can you help me?
As anyone the same notebook ?

Sorry for my bad english :)

Thanks in advance
Regards
Luigi

---

### Post by deviantnz on 2008-07-26
I have the same laptop (Evo N620c) and I followed those instructions and my laptop freezes when I try to connect to a wireless network.

It would be great if anyone has a solution.

---

### Post by fluffkitten on 2008-07-26
> **gintonic said:**
> 
My wireless router has hide essid and wpa-psk encryption configured.

When i try to configure ( with network manager, wicd, or manually ) wpa-psk encryption my notebook freeze. The two leds on top left blink and the only way to reset is remove battery.


A part of your problem is likely to be that the W200 doesn't support WPA
(not even in Windows IIRC). Trying WEP might work, does for me on a 7.04
install (N600c) so long as I turn off roaming in network manager. 

fK

---

