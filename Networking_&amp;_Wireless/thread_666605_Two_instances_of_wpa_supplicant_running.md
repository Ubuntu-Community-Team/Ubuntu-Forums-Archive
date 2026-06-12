---
title: "Two instances of wpa_supplicant running"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by Jason Spaceman on 2008-01-13
I'm running Ubuntu 7.10 on my laptop.  For some reason, when I boot it up, I get two instances of wpa_supplicant running:

> root      4421  0.0  0.0   3844   644 ?        S<s  13:38   0:00 /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.eth1.p
id -i eth1 -D wext -C /var/run/wpa_supplicant
root      6186  0.0  0.0   3844   632 ?        Ss   13:39   0:00 /sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant/wp
a_supplicant.conf -D wext -P /var/run/wpa_supplicant.pid eth1

Which forces me to manually kill one of the above processes, and then do a 'sudo dhclient eth1' in order to get my wifi up and running.

How do I prevent two instances of wpa_supplicant from starting?

---

