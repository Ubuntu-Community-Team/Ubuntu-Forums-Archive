---
title: "Gnome Network Manager"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by sn0m on 2007-02-05
network manager is doing my head.

My system crushed after trying to remove beryl, my fault, did not write down all the changes to reverse them.
Anyway, i have a compaq pressario v5000 with a broadcom wireless build in card.
I have manged to install the driver with ndiswrapper following one of the great guides here then i installed gnome network manager with wpa supplicant from repositories and disabled the wireless one from the default network manager of ubuntu.
re-boot, network manager up and running, it can see my home network, but when i tried to connect to it, putting my password and chosing TKIP, by the way, i have a personal WPA encryption mode on my wireless, it doesn't connect...arrhhhh:mad: 
Also, before i would get a notification from keyring manager about a password to store the key each time the network manager would connect me to my wireless, this time is not doing it....why not:confused: , i have checked that wpa supplicantis installed.
what am i doing wrong here.
thanks for your word of wisdom.
Koli

---

### Post by 23meg on 2007-02-05
Try deleting your password from the keyring and entering it manually again (System / Administration / Keyring Manager). Log out and log in again before trying to connect.

---

### Post by sn0m on 2007-02-05
This is a fresh install of ubuntu, no passwords have yet been stored in keyring manager and there aren't any there.

---

### Post by sn0m on 2007-02-06
no suggestion, has anyone wth broadcom wireless laptop had a  good experience with wpa, if so can they post here how to?

---

