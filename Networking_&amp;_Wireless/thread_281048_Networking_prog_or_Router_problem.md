---
title: "Networking prog or Router problem?"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2006-10-20
I have put:

Internet---DSL Modem-----(Wireless Router)----(wlan0-ubuntu)
                 LAN-----LAN port
So that:
Internet IP ---------------------------------->(wlan0 ubuntu)
DSL Modem works as a bridge, and also so does the Wireless router    
with LAN ports connected.

Then I do: deactivate wlan0 in networking GUI.
macchanger wlan0 -A
Activate wlan0.

Sometimes I got:
root# ip route
x.x.176.0/21 dev wlan0  proto kernel  scope link  src x.x.178.154
No default?
sometimes:
root# ip route
x.x.176.0/21 dev wlan0  proto kernel  scope link  src x.x.177.54
default via x.x.176.1 dev wlan0
sometimes:
inet addr:192.168.0.100...

DHCP server on wireless Router is Off.
Is there problems with GUI Network-admin not updating & putting default route?
or is the problem in my Wireless router?

---

