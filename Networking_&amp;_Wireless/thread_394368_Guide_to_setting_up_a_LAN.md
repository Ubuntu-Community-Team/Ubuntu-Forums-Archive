---
title: "Guide to setting up a LAN?"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-03-26
I have a laptop and a PC running 6.10.

Anybody know of an easy guide out there that shows me how to set up file and printer sharing?  I have some folders I'd like to copy over to the laptop via the network.

Thanks!

---

### Post by chili555 on 2007-03-26
From Windows to Ubuntu? [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)  If linux to linux, I congratulate you on completing your recovery program. Post back and we'll have it done quickly.

---

### Post by diablo75 on 2007-03-26
From Linux to Linux, man.  I don't know what to do...

---

### Post by Mr. C. on 2007-03-27
For just copying files:
```

scp *files **username*@*desthost*:
```

Replace files, username, and desthost as appropriate for your needs.

Easy enough ?
MrC

---

### Post by diablo75 on 2007-03-27
Actually, I got SMB to work very easily.  Had a couple bugs though, but went smoothly after restarting both systems.

---

