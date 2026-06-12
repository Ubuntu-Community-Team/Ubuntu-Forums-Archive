---
title: "Atheros Wifi with 2 modes Simultaneously"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-08-26
Dear all,

Can I do like this in my Linux Atheros Wifi? I want to have both AP mode and Ad-hoc mode in my laptop. It is possible?

#wlanconfig **ath0** create wlandev *wifi0* wlanmode **ap**
#wlanconfig **ath1** create wlandev* wifi0* wlanmode **adhoc**

Please assist. Thank you.

---

### Post by nosrednaekim on 2007-08-26
no, you can only use the chipset for one thing at a time.

---

### Post by tturrisi on 2007-08-26
> **nosrednaekim said:**
> no, you can only use the chipset for one thing at a time.

Not entirely true.  Atheros chipsets use virtual interfaces (athX).  The actual interface is wifiX.  Thus with an atheros you can have one virtual athX interface in monitor mode and silmutaneously have another athX interface in managed mode.  See this nmadwifi guide for how to create multiple inyerfaces:
[http://madwifi.org/wiki/UserDocs/MultipleInterfaces](http://madwifi.org/wiki/UserDocs/MultipleInterfaces)
[http://madwifi.org/wiki/UserDocs](http://madwifi.org/wiki/UserDocs)

---

### Post by nosrednaekim on 2007-08-26
hmm interesting.... I guess thats so you can snatch packages while you are connected? Hackers like their internet while they are spying ;)

---

### Post by Paris Heng on 2007-08-27
Okie, thanx

---

