---
title: "Manual Networking Changed Won't Work After Upgrade to Hardy"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by Spaceman Spiff on 2008-09-02
Hey guys, I had a nice little setup for Gutsy with my manual networking.  Pretty much I used my interfaces file, along with my wpa_supplicant file to connect to my school's wireless.  I would change the files then type sudo /etc/init.d/networking restart

Before it would show me messages in Terminal, such as listening to DHCP or w.e networking lingo it would throw out at me, now it does nothing.. any tips?

Here is my old setup:


```

interfaces

auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp
#wpa-driver wext
#wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

wpa_supplicant.conf

#Lehigh University
network={
        ssid="lu"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="my username!!"
        password="and my password"
}


```

Any help would be appreciated thanks.

---

