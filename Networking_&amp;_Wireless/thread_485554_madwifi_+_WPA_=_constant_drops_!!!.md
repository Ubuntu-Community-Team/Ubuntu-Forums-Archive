---
title: "madwifi + WPA = constant drops !!!"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by vettedude on 2007-06-27
Situation:

Toshiba A135-S2386
Atheros AR5006EG
Ubuntu 7.04
latest madwifi driver 0.9.30.13 installed


I can make wireless  [WPA] connections, but they fail frequently and when I do get a connection, they drop often.  Connections to open AP's setup much faster and are more stable.  When I boot this system into Vista, the connections are very stable ... I'm using one now. The signal strength is much bettr in Vista than in Ubuntu.

What is wrong ??

---

### Post by vettedude on 2007-06-27
bump

---

### Post by ugm6hr on 2007-06-27
Do you use Network Manager to auto-connect with a WPA wireless router? If so - I think it is a known issue with Network Manager that has been reported. They feel it is some kind of conflict between the madwifi wireless driver and Network Manager.

Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/64173)

I would suggest trying Wicd (v1.2.9) or using WEP.

---

### Post by vettedude on 2007-06-28
I tried some of the ideas in the referenced articles, but the WPA connection is still not reliable.

---

### Post by ugm6hr on 2007-06-29
Those articles merely list the problems - not solutions (as far as I know).

For a possible solution - try:
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

I would suggest Wicd v1.2.9 (rather than v1.2.7).  Reboot after installing.  Then in Wicd Preferences: WPA driver "wext" and interface "ath0"

---

