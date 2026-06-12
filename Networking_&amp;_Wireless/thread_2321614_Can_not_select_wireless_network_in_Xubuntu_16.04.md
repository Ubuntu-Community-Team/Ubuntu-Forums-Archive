---
title: "Can not select wireless network in Xubuntu 16.04"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by dongyi on 2016-04-23
The Wifi Network button is greying out in Xubuntu 16.04, so I can not select which WLAN to connect.
What to do?
[ATTACH=CONFIG]268564[/ATTACH]

---

### Post by dongyi on 2016-04-24
I want your help!

---

### Post by him610 on 2016-04-24
I just went through this yesterday myself so maybe I can help -

Execute each of these from a terminal and report the results of each, enclosed within code tags...
```

rfkill list
inxi -b
sudo iw reg get 
sudo iwlist [i/f] scan  where [i/f] = your wireless adapter

```
or read and follow the instructions here... - this is actually the ***recommended first step*** in troubleshooting connection issues
[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

or if you feel adventurous and want to try it yourself, refer to this link...
[http://ubuntuforums.org/showthread.php?t=2321703]("http://ubuntuforums.org/showthread.php?t=2321703")

---

