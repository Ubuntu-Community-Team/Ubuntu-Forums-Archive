---
title: "Lost my wireless"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Joseph1110 on 2007-08-15
Well i had my wireless connection and was surfing the net fine. I decided to go into working out how to use aircrack-ng. It said do this wlanconfig destroy ath0 command. Now i cant connect to my wireless card. Clicking on the icon next to the clock has wired network greyed out. And when i goto network settings its only got wired connection and modem connection now. Any help?.

---

### Post by spd106 on 2007-08-15
You need to recreate the ath0 interface, look here [http://madwifi.org/wiki/UserDocs/StationInterface](http://madwifi.org/wiki/UserDocs/StationInterface)

Alternatively reload the driver in the Restricted Drivers Manager.

---

### Post by Joseph1110 on 2007-08-15
when i type

sudo wlanconfig ath create wlandev wifi0 wlanmode sta

i get

wlanconfig: ioctl: no such device

---

