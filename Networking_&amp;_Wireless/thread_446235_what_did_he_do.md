---
title: "what did he do"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by bandofmercy on 2007-05-16
first, the background from last week:
[http://ubuntuforums.org/showthread.php?t=439175](http://ubuntuforums.org/showthread.php?t=439175)

i was having problems getting my laptop wireless working (detected networks & tried to connect but couldn't, maybe router, maybe hex key, i don't know) but it worked fine when i brought it to my apartment.  then my friend came to visit and i told him he could use the comp for internet only.  then yesterday he told me that it had mysteriously stopped working... no blinking wireless light, no networks detected where i had at least 5 in range the day before.  who can i blame for this?  where do i start now?  reinstall madwifi and network-manager or something?

---

### Post by spd106 on 2007-05-18
This might not be your friends fault, I've had a devil of a time getting network manager to work. It's not that it just doesn't work, it's the intermittent failure that's most frustrating. Every time I reboot it's a gamble whether it will work or not.

The most reliable way I have found to get it working is to remove ath_pci, then reinsert it.
```
sudo modprobe -r ath_pci
```
```
sudo modprobe ath_pci
```

Sometimes NM fails so you have to restart it with this command
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

---

