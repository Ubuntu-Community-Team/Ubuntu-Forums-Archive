---
title: "Zyxel G-260 USB adapter with NDISwrapper drops connection in Ubu &amp; Sabayon but not XP"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by AstarothCY on 2007-10-01
I have installed the 7.2.2.42 driver using ndiswrapper, the adapter then seems to work fine, it establishes a connection with the router and I can connect to the internet, but after a few seconds it drops the connection. If I disable and re-enable the connection, it re-establishes and works for a few seconds, then drops again.

The interesting thing here is that the same problem happens on the Gutsy Beta live cd, as well as the Sabayon 3.4f live dvd. The adapter has absolutely no problems on WinXP so it's not the network and it's not the adapter, it sounds like an ndiswrapper compatibility issue. If it helps, I am connecting to a Buffalo AirStation router and the network is protected with WEP 64bit hex. 

Any ideas? Let me know if you need me to post any output.

---

### Post by AstarothCY on 2007-10-04
:(

---

### Post by AstarothCY on 2007-10-07
help?

---

### Post by AstarothCY on 2007-10-08
bump

---

### Post by Lambert on 2007-10-08
After going through this cycle, open a terminal and type this.

dmesg | grep ndis

post output here to see if any errors are listed.

---

### Post by AstarothCY on 2007-10-08
Well this is slightly embarassing, I just tried it again and it hasn't dropped the connection for a while now. Maybe there's been a relevant update in the past few days? Anyway, just in case the connection drops again, I'll post the output. Thanks anyway.

---

