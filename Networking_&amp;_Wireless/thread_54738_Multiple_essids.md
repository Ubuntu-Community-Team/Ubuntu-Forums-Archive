---
title: "Multiple essids"
date: 2005-08-05
forum: Networking &amp; Wireless
---

### Post by bingerthedog on 2005-08-05
I go from school to home to my parents all on wireless networks and was wondering if I can configure my /etc/network/interfaces file to automatically connect to any of these systems on bootup.  I just finally got it to automatically connect to my home network and was thinking it would be cool if it would connect to any of these on bootup.  Here is my interfaces file...

auto lo
iface lo inet loopback


mapping hotplug
        script grep
        map ra0

auto ra0
iface ra0 inet dhcp
wireless-essid Home

iface eth0 inet dhcp


I was thinking if I added the other essids after "Home" that may work but I wanted to ask first.  Thanks

---

### Post by v2.0 on 2005-09-06
i am also looking for a solution to this. so far i see mapping in the interfaces with the use of a script and programs like wlassistant and wpa_supplicant. my deal is that i don't really want to start running a bunch of scripts. i would prefer to do this setting through the backend, like just config'n interfaces or samthin. don't know -- need input...

v2

---

