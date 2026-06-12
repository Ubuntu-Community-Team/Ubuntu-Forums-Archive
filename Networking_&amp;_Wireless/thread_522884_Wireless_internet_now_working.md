---
title: "Wireless internet now working"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by helsabot on 2007-08-11
I've been trying many things to get wireless to work but none of them are working at all. I tried to download the Ubuntu network manager and it says i already have it and i have no clue where to find it, and I've tried to configure my network many times and it doesn't connect. Any ideas as to what's wrong?

---

### Post by rlozano on 2007-08-11
welcome to the forums.

what version of ubuntu are you exactly using?

---

### Post by helsabot on 2007-08-11
feisty fawn, or whatever the most recent version is (just dl'd about 2 hours ago)

---

### Post by unisol on 2007-08-11
NetworkManager is a different animal. Do this:

System > Preferences > Sessions

Under Startup Programs, check for Network Manager. If it's there, make sure it's checked off. If it's not there, you may need to re-add the entry:

1) Click New
2) Make name "Network Manager"
3) Make command "nm-applet --sm-disable"
4) Click OK
5) Hit Ctrl + Alt + Bksp to restart GNOME

---

