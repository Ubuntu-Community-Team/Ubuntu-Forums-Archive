---
title: "T-Mobile Hotspot using 802.1X authentication"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by dataminer on 2008-01-16
I wanted to post this information for those who are interested in utilizing T-Mobile Hotspot's 802.1X authentication. This may be useful for those who recently received an XO laptop and received the complimentary year of T-Mobile Hotspot. If you go to T-Mobile's support website, they claim that if you wish to use 802.1X, you need to download their Connection Manager software for Windows. This is not necessary. Below is the nessesary configuration info for connecting using Gnome NetworkManager 0.6.5 or higher:

Network Name: tmobile1x    
  (Note: this SSID is not broadcast)
Wireless Security: WPA Enterprise
EAP Method: TTLS
Key Type: TKIP
Phase2 Type: PAP
Identity: (your T-Mobile username)
Password: (your T-Mobile password)

And that's it! I'm not really sure why T-Mobile would discourage users of alternate operating systems from using their service. After setting this up, you will no longer have  to use the web login each time. Also, all wireless traffic between your laptop and the access point will be authenticated and encrypted. I hope this information helps!

---

