---
title: "Wireless/Internes problems (dapper)"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by kurenai on 2007-03-30
Hi all. first post for me.
im sure ill post more once i get my internet working.
ok...so:

i installed Ndiswrapper.
i got the XP drivers for my PCI card (netgear 311v2)
i installed that, it installed fine. i followed the instructions to make ndiswrapper run everytime i use computer etc.
the lights are up on the card.

however. when i do iwconfig, for wlan0 it seems not to show me the mac address for my router or even my mac address.

if you guys have any tips for me, please tell me. also im sorry if this comes up often as i imagine it might.

thanks in advance.

Aaron

---

### Post by chili555 on 2007-03-30
Try:```
iwlist wlan0 scan
```Post back if you need more help.

---

### Post by kurenai on 2007-03-30
yeah, "No Scan Results"

---

### Post by kurenai on 2007-03-30
update.

when i do ifconfig it has my mac address.

when i do iwconfig. it has IEEE 802.11b/g ok good. it has the right ESSID good. however
Access Point: Not-Associated. and i cant see the routers mac address anyhere.

thanks

---

### Post by kurenai on 2007-03-30
bump... (sorry)

---

### Post by kurenai on 2007-03-31
bump, 
anyone know the next step for me? ( i gotta get the net working!)

---

### Post by spd106 on 2007-03-31
Which chipset does your card have? You can find out by running this command ```
lspci
```

I thought that the 311v2 was broadly acx111 based. If that's what you have then check  this page [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

There are guides in this forum and the Ubuntu wiki as well.

---

### Post by kurenai on 2007-03-31
yeah it is. but i couldnt get it working via acx so i went for ndiswrapper.

---

