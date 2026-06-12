---
title: "nm-applet requires an entry in {{/etc/modules}}"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by lawrence1992 on 2007-08-08
nm-applet requires an entry in {{/etc/modules}} to start ndiswrapper on system startup. It uses keyring to authenticate my wpa2 pre shared keys, is there any way to get around this? 





Thanks in advance- Larry

---

### Post by kevdog on 2007-08-08
Im not sure what you are asking??

To put ndiswrapper inside /etc/modules:

echo ndiswrapper | sudo tee -a /etc/modules

Are you getting some kind of error message or something???
Your post is a little vague on the details.

---

### Post by spd106 on 2007-08-08
The steps to automate the keyring authentication are given on the wiki page here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

