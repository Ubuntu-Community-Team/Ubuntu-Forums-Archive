---
title: "nm-applet &amp; changing ap names"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Gladier on 2007-08-03
hey guys,

ive finally got wireless working with nm-applet under gnome.

however because i have the exact same network config at home and at work combined with vpns we get a great big mess.... 

so its working ... but ive changed the name of the access point down here. when i first plug in the wifi card (madwifi-ng ath5212) it sees the new essid - but if it disconnects then it comes back up with the old one *sigh*

ive looked through gconf and removed the wireless folder and cant find anywhere else on the drive where it could be pulling it from.

---

### Post by Gladier on 2007-08-04
figured it out

all the places i looked for answers for this all said run sudo gconf-editor, which brings up roots gconf - you need to run it without the sudo to get it to work

---

