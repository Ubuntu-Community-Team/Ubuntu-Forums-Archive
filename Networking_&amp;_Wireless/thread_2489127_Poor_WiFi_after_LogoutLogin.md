---
title: "Poor WiFi after Logout/Login"
date: 2023-07-19
forum: Networking &amp; Wireless
---

### Post by speartip on 2023-07-19
After shutdown my WiFi speeds are roughly 240mb Download / 70mb upload, more or less where they should be. However after a logout/in, Download drops to about 20mb and upload to zero.
Disabling then re-enabling WiFi resolves the problem, but why is this happening? and is there a way to automatically disable/re-enable WiFi after a logout without having to do it manually?

---

### Post by TheFu on 2023-07-28
My only guess is that there are 2 modes for wifi networking.
* Server, runs at boot.
* Login-based, only runs once a login is performed.

There are pros and cons for each mode.
[https://help.ubuntu.com/lts/ubuntu-help/net-othersedit.html.en](https://help.ubuntu.com/lts/ubuntu-help/net-othersedit.html.en) might be helpful.  You didn't mention any release or DE, so I'm guessing 22.04/Gnome.

---

### Post by speartip on 2023-08-01
Thanks for your reply @TheFu.
The problem was Powersave in /etc/networkmanager/conf.d. Changing the value from 3 to 2 then rebooting solved the problem.

---

