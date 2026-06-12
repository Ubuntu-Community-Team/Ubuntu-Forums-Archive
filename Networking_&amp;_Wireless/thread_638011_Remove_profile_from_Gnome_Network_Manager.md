---
title: "Remove profile from Gnome Network Manager?"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by neocookie on 2007-12-11
I'm using gnome network manager which is working well for me. However, I have two wireless networks at home (one using WPA, the other WEP for my housemate's old laptop). I tried to connect to the WEP profile the other day (which failed), but now every time I try to get online it spends about 5 minutes trying to connect to that profile before it will allow me to switch to the WPA network.

Is there any way I can tell it to ignore the WEP network/profile?

---

### Post by floke on 2007-12-11
open gconf-editor, then go system/networking/wireless/networks and delete the one(s) you don't want to access.

---

### Post by smileone on 2007-12-13
You can modify your configuration from shell.
gconf-edit work on you home directory (example /home/<user-name>/.gconf/system/wireless/networking/networks)
In this folder you can find all wireless network that you use from the beginning.
:popcorn:

---

