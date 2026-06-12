---
title: "realtek rtl8185L need some help"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by johnficca on 2007-12-28
ok so I got my wireless card working with the help of the driver that realtek has for my card. this is what I did 

first script I ran was ./makedrv

> #!/bin/bash

tar -zvxf stack.tar.gz
tar -zvxf rtl8185.tar.gz
cd ieee80211
make clean
make
cd ../rtl8185
make clean
make
cd ../

then ./wlan0up

> #!/bin/bash

cd ieee80211
insmod ieee80211_crypt-rtl.ko
insmod ieee80211_crypt_wep-rtl.ko
insmod ieee80211_crypt_tkip-rtl.ko
insmod ieee80211_crypt_ccmp-rtl.ko
insmod ieee80211-rtl.ko

cd ../rtl8185
insmod r8180.ko

cd ../

ifconfig wlan0 up

and they have a wlan0down one too

> #!/bin/bash

ifconfig wlan0 down

rmmod r8180
rmmod ieee80211-rtl
rmmod ieee80211_crypt_ccmp-rtl
rmmod ieee80211_crypt_tkip-rtl
rmmod ieee80211_crypt_wep-rtl
rmmod ieee80211_crypt-rtl

ok so the deal is I would like my card to work at boot what should I do? when I reboot I have to run ./wlan0up and ./wlan0down and it starts working...what should I do?

---

