---
title: "wlan not working (3945ABG)"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by alex004 on 2008-10-03
Hello dear community members,

since 3 hours I try to get Intel wireless 3945ABG to run (Dell D620). I have read the posts here and found chili555's recommendations.
Unfortunately I still cannot bring it up to work.

What I tried out:
1.
sudo iwlist wlan0 scan
-> found my WLAN Access point
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
But it doesn't help.

2.
following another recommendation I tried to install linux-backports-modules-hardy-generic.deb
But my Ubuntu 8.04 refuses to install this.

Please give me some hints. Sorry that I am too less experienced or too stupid to solve it my own.

---

### Post by naufiundich on 2008-12-09
My laptop is Compaq 6720s. Windows Vista was installled on it and I installed Ubuntu 8.10 additional on my laptop.
My WLAN Card is 3945ABG.
WLAN didn't work in Ubuntu 8.10. 
I searched for the solution and found the following article in the website _[http://wiki.ubuntuusers.de/Intrepid_Ibex](http://wiki.ubuntuusers.de/Intrepid_Ibex)_

I did as it said and wlan works fine now.
**The article says--------**
WLAN auf Kanälen 12 und 13

In Kernel 2.6.27 sind die Möglichkeiten sich auf den Kanälen 12 und 13 zu Verbinden bei manchen WLAN-Karten deaktiviert {en} . Dieses Problem trifft für alle Treiber zu, die mit dem 802.11-Subsystem des Kernels arbeiten. Also z.B. beim Intel PRO/Wireless 3945ABG {en} Chipsatz, der über das Kernelmodul iwl3945 betrieben wird. Dieser ist in vielen modernen Notebooks verbaut. Sollte man mit Intrepid WLANs nicht mehr finden, die man mit Hardy entdecken konnte, so schafft ein entsprechender Startparameter für das 802.11-Subsystem Abhilfe. Mit einem Editor muss die Datei /etc/modprobe.d/cfg80211 erstellt, und folgender Parameter eingetragen werden:

options cfg80211 ieee80211_regdom="EU"

Das läßt sich natürlich auch mit einem Terminal-Befehl sehr rasch erledigen:

echo 'options cfg80211 ieee80211_regdom="EU"' | sudo tee -a /etc/modprobe.d/cfg80211

Nach einem Neustart des Systems stehen nun, unabhängig vom verwendeten Treiber, alle Funkkanäle von 1 -13 zur Verfügung.
**----------------------**
I hope this would help.

---

### Post by ussndmac on 2008-12-09
For what it's worth:

I have a laptop with 3945ABG and I have been able to get it to connect to my Linksys 802.11b wap (the wap shows a connect and the laptop shows the ssid, frequency, etc. of the wap) but I cannot ping the wap or anything on the network connected to the wap. I have tried numerous "fixes" found in the forums to no avail on hardy or intrepid.

I have an XP laptop with a dlink pcmcia card that works fine with the wap.

I'd love to find a fix...

---

