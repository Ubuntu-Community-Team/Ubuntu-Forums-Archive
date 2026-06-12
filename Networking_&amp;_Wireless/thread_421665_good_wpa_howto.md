---
title: "good wpa howto?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by patrickfromspain on 2007-04-24
Hi there!

I'm deciding if I want to migrate my network from wep to wpa (in my case, I don't have any neighbours that will hack into my net, and will never have). However.. I'd like at least to try wpa. At worst, I won't use it but I'll know how to configure it, which can't be bad

I don't want to use network manager, thats the first thing. I have 2 pcs, one with an INPROCOMM IPN2220 (using ndiswrapper, the card supports wpa) and another using a pci card based on ralink's rt2500 chipset.

In my router I must select WPA-pre shared key, and then TKIP or AES, right? TKIP or AES, why?

Any good guides around? I've seen a few.. but all seem to be different. I'd like you to share how you made wpa work or which guide you used.

Thanks a lot :)

---

### Post by spd106 on 2007-04-25
Wikipedia has a decent entry about WPA and the difference between TKIP and AES. Well worth a read, though it boils down to TKIP for greater compatibility and AES/CCMP for the best security. 

Depending how advanced you want to get I suggest you just use Network Manager for the simple case and use the EAP/WPA sticky (wpa_supplicant) for more complex cases.

---

