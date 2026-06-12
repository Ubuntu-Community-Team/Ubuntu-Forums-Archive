---
title: "can't view wireless networks"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by fartonmyear on 2007-03-19
very new to linux. 

ok so when i click the little netork icon on the top right it takes me to connection properties: ath0. there's a configure button, but it just lets me configure the current unsecure network i'm on.  but nowhere does it show available wireless networks. how do i get this to work?

oh one more thing. i'm using beryl. how do i disable the shader? it's when i double click the toolbar and the window minimizes into the toolbar.

---

### Post by spd106 on 2007-03-21
This function was broken in Edgy, so you will have to resort to scanning from a terminal with ```
sudo iwlist ath0 scan
``` Alternatively you can install Network Manager [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

