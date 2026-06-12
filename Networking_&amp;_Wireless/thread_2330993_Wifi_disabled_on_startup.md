---
title: "Wifi disabled on startup"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by nalsubaie on 2016-07-17
I have been using ubuntu 16.04 on an HP spectre x360 for a few months now and the experience has been positive. A couple of days ago I noticed that the wifi is _disabled_ on startup. My attempts  to fix this annoying issue have all failed and I very much hope that you can help.

Thank you

---

### Post by wildmanne39 on 2016-07-17
Please try:
```
sudo  systemctl restart NetworkManager.service
```
does that make it connect?

---

