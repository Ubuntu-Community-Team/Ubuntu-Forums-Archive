---
title: "rtl8187b installation error"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by JBMaxman on 2010-10-27
Hi people,

Can anyone assist. Am following the post on installing rtl8187b. After the ./makedrv i try to run ./wlan0up. this is what i get

jb@jbpc:/wifi$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8187.ko': -1 File exists

Assist coz i need the wireless card.

---

### Post by Silent Warrior on 2010-10-27
Well, I can tell you right off the bat that you're getting those messages because there are files with the same name present already. Are you sure you need to install the driver manually? I have a Realtek 8187B myself, and it has been working with the drivers in the kernel for over a year... You ARE using a release later than 8.04, right?

---

