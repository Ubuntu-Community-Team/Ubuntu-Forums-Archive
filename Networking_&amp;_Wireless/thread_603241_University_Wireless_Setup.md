---
title: "University Wireless Setup?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by JohnnyTricksta on 2007-11-04
I've read some close threads about this, but still have yet to find a solution. The sticky thread for WPA requires no EAP so I can't use that thread. Here is my school's guide: [http://www.its.ipfw.edu/wireless/linux-config.shtml](http://www.its.ipfw.edu/wireless/linux-config.shtml)

ANy ideas?

Thanks!

---

### Post by raghav_p on 2007-11-05
I fail to see what your question is? Are you having trouble connecting to your university's wireless network? It seems they have provided instructions that should work well. The new NetworkManager in Gutsy added support for various advanced settings. To connect to my university (University of Pennsylvania), the following settings work; perhaps yours are the same?

1) Click on Network Manager
2) Click on "Connect to Other Network"
3) Type in network SSID
4) Change wireless security to "WPA Enterprise"
    --> New options appear
5) Change EAP method to "TTLS"
6) Change key type to "Dynamic WEP"
7) Change Phase 2 to "PAP"
8) Type in Login Credentials (i.e. username/password)
9) Click connect.

---

### Post by JohnnyTricksta on 2007-11-05
Sorry, I forgot to mention that I use Wicd instead of the network manager

---

