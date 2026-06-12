---
title: "madwifi hostapd how the f***"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by vaalbygaardsvej on 2008-01-12
well i have set in mind the stupidest thing that i will build a linux box that routes and acts as AP
got everything up and running smooth except security on the wireless.. i need hostapd to do this. got it.. dosnt work

before this projekt i knew nothing about configing linux. so im dumb in this area.
i have set up the machine to act as AP but with no security. is there someone out there that can help me on how to set it up? i have run out of things to try

and BTW sorry for the lack of info, but i really dont know what to post :confused:

well migt at least post what happens when i run:

sudo hostapd /etc/hostapd/hostapd.conf

this is what happens:


Configuration file: /etc/hostapd/hostapd.conf
Configure bridge br0 for EAPOL traffic.
madwifi_set_privacy: enabled=0
BSS count 1, BSSID mask ff:ff:ff:ff:ff:ff (0 bits)
madwifi_sta_deauth: addr=ff:ff:ff:ff:ff:ff reason_code=3
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Could not connect to kernel driver.
Mode: IEEE 802.11g  Channel: 60  Frequency: 0 MHz
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=0
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=1
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=2
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=3
Using interface ath0 with hwaddr 00:1b:2f:c6:f6:5c and ssid 'Porten'
madwifi_set_privacy: enabled=0
l2_packet_receive - recvfrom: Network is down
Wireless event: cmd=0x8b1a len=15
Wireless event: cmd=0x8b19 len=8

and here it just stops.

---

### Post by vaalbygaardsvej on 2008-01-13
bump pretty please ](*,)

---

