---
title: "RT61 connects to router, not to internet"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by AlliumPorrum on 2007-02-12
I have installed my new RT61 - chipset PCMCIA WLAN- card to my Ubuntu 6.06 laptop. Everything seems to be OK; Ubuntu is getting an IP- address (static one) and I can ping my router. I'm using WEP- encryption with shared password, and I have set the password and all other settings to the 'rt61sta.dat'- as it was instructed in driver's readme- file. I'm sure that the password is correct because my other laptop can access the network with the same settings. I also have added my Ubuntu machine's MAC- address to the firewall's accepted list, so everything should be OK. 

But for some reason I just can't connect anywhere outside my own network. Could some one please help me, what should I do so that I can access internet, not just my own router???

---

### Post by AlliumPorrum on 2007-02-13
Doesn't anyone have any ideas how could I start solving this problem? What might cause that I cannot access any IP's outside my router on my Ubuntu laptop??

---

### Post by AlliumPorrum on 2007-02-13
Ok, i solved this problem.  I had to do following, for some reason:

 sudo route add default gw 192.168.*.*

where *.* is set as your router, mine is 2.1

---

