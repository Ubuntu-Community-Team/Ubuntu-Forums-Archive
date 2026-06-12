---
title: "ipw2100 and monitor mode"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by zircon on 2005-06-07
I can't switch from managed mode to monitor mode with my ipw2100
Switching to ad-hoc works but nothing happened with 
"iwconfig eth1 mode monitor"
Any idea for my problem?

---

### Post by Silwenae on 2005-06-07
[QUOTE=zircon]I can't switch from managed mode to monitor mode with my ipw2100
Switching to ad-hoc works but nothing happened with 
"iwconfig eth1 mode monitor"
Any idea for my problem?[/QUOTE]
 Have you upgraded from the stock ipw2200 drivers in Ubuntu (0.19) to 1.04 and upgraded to the latest firmware?  There's a pretty good How-To in the Customization forums.

---

### Post by zircon on 2005-06-07
[QUOTE=Silwenae]Have you upgraded from the stock ipw2200 drivers in Ubuntu (0.19) to 1.04 and upgraded to the latest firmware?  There's a pretty good How-To in the Customization forums.[/QUOTE]

I'm on ipw2100, not 2200 and I'm using drivers v1.1.0 (last version available...)

---

### Post by Gianluca-VLSI-vs-Coss-TDS on 2007-01-01
> **zircon said:**
> I'm on ipw2100, not 2200 and I'm using drivers v1.1.0 (last version available...)

Try to make:
ifconfig eth0 down or ifdown eth0
iwconfig eth0 mode monitor
ifconfig eth0 up or ifup eth0
luck!!

mine goes well but using airodump ERROR


unsupported hardware link type 803
expected ARPHRD_IEEE80211 or ARPHRD_IEEE80211_PRISM
did you put your card in monitor mode ?

---

