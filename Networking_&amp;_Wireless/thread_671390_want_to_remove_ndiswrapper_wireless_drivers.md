---
title: "want to remove ndiswrapper wireless drivers"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by 1976saint on 2008-01-18
Hi I've have my installation wireless working OK, then all of a sudden it started playing up. Wireless would crash and then cause application to either not load or a FORCE shut-down was required to close them. One thing lead to another and I decided to reinstall the wireless drivers. However, when I issued the NDISWRAPPER -i WMP11NDS.inf (yes its a Linksys) I got the message, wmp11nds is already installed. I manually deleted the drivers at this point. and tried again but the same message appeared.

If I try to remove it with a NDISWRAPPER -e WMP11NDS.inf it responds with couldn't delete /etc/ndiswrapper/WMP11NDS.inf: no such file or directory.

This I suspect is my fault as I manually deleted the folder.

If I issue the ndiswrapper -l to list the drivers it returns 

wmp11nds : invalid driver!

How can I get ndiswrapper to reinstall the driver as I seem to be in a catch 22 here ?

Cheers Paul.

---

### Post by reckless2k2 on 2008-01-18
well one thing is that you don't put the .inf at the end of the driver when removing. it's also case sensitive as well. 

if you are still having problems, reinstall ndis and then remove the drivers and then remove ndis. dropping the .inf might be the simple fix though but you need to drop it no matter what.

---

