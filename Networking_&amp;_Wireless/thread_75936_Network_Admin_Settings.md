---
title: "Network Admin Settings"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by AgenT on 2005-10-14
Where does network-admin store its settings? Specifically the profiles (locations) settings.

**ANSWER** (update):
To answer my own question:
 ```
/etc/gnome-system-tools/network/profiles.xml
```  Network settings are stored in:
```
/etc/network/interfaces
``` Removing those (and having them replaced with new ones) may help some if they are having network problems. Especially problems dealing with saving settings.

---

### Post by thechitowncubs on 2005-10-18
I am wondering the same thing

---

### Post by AgenT on 2005-10-19
To answer my own question:
```
/etc/gnome-system-tools/network/profiles.xml
``` Network settings are stored in:
```
/etc/network/interfaces
``` Removing those (and having them replaced with new ones) may help some if they are having network problems. Especially problems dealing with saving settings.

---

