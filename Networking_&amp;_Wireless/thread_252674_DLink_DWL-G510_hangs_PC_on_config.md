---
title: "DLink DWL-G510 hangs PC on config"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by andyhem on 2006-09-07
Hi,
  Am just playing with Ubuntu for the first time and am booting off a freshly downloaded CD. My PC is an old(ish) gateway pentium 3 700mhz...
Am trying to get it to talk to my home network using a D-Link DWL-G510 card. The OS seems to see the card okay (it appears in the list of n/w devices), and the card recognised the SSID of my network but everytime I set up my WEP key and hit connect, the whole system locks up.
Any clues?

---

### Post by rijnoutgankema on 2006-09-07
Andyhem,
Check if you have the HEX or ASCII codes right. I never got it to work from the Ubuntu Networking GUI. I ended up entering the HEX code of the WEP in etc/network/interfaces.
That went o.k.
Rijnout

---

