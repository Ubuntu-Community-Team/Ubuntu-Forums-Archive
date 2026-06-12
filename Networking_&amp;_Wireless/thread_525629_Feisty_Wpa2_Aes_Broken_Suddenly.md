---
title: "Feisty Wpa2 Aes Broken Suddenly"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by LoPHat on 2007-08-14
Hello from a relative noob,

I recently upgraded to feisty fawn (clean install) and really like it. I installed the current MadWIFI drivers and use Keyring Manager 2.18.0. I successfully connect and authenticate to Open, WEP 64/128, WPA1/2. Was working for months without problems. I am current with all updates for all mods. At some point - i can't say just when but it was in the last 3 months - WPA2 broke. Other windoze machines had no problems so i knew it wasn't the AP. Until today i just thought it was just my computer that wouldn't talk to it. I did some troubleshooting today and discovered that it's just WPA2 that doesn't work. Toggling settings one at a time revealed the following results:

MAC Filtering enabled - OK
WEP 128 enabled - OK
WPA TKIP 63 CHAR - OK
WPA2 AES 63 CHAR - BROKEN
BROADCAST SSID disabled - BROKEN - can't even see the AP

NOW, up until recently all of the BROKEN things werre OK. 

Any ideas?

Hardware:
AP = Netgear WG602v3     V1.2.5 firmware(current)
WC = Netgear WG511T w/most current firmware

---

