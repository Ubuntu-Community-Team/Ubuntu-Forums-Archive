---
title: "Problem with setting up my wireless card"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by Spectrum2004 on 2007-01-28
I need help setting up my wireless card. I followed the instructions on [this]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo") page and it all worked fine until I got to the part where I have to blacklist the old driver. This is exactly what happens in the terminal:
> sudo echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied


Can anyone help me out with this? I don't understand why I don't have permission to do it if I'm performing the action as root. Any help would be greatly appreciated.

---

### Post by KJoFan on 2007-06-14
I'm going to bump this up because I'm having this exact issue.  anyone have a solution or fix??

Thank you!

---

### Post by linux noooob on 2007-06-14
log in as root type sudo -i then pass or su (username) the password that should log you in as admin and give you all the permision needed.

---

