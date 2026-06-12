---
title: "Upgrading from 8.04 to 8.10"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-12-18
This is more than likely a simple answered question but id prefer to know im doing this right over messing up my computer. On the ubuntu website its says: 

"Upgrading from Xubuntu 8.04

To upgrade from Xubuntu 8.04, open the Update Manager from the Applications menu under System. It will tell you: "New distribution release '8.10' is available". Click Upgrade and follow the on-screen instructions. "


Well when i go into Update Manager, i see nothing involving new distribution release 8.10, it only says "system is up to date". Yet when i go to my system monitor im still at version 8.04.

---

### Post by Snappo on 2008-12-18
You have to enable normal releases in your software sources manager. It's set on LTS by default.

---

### Post by tom56 on 2008-12-18
Go to System -> Administration -> Software Sources. Choose the "Updates" tab. Where it says "Show new distribution releases", change it from "Long term support releases" to "Normal releases".

---

### Post by kanikilu on 2008-12-18
Try running ```
update-manager -d
```

I think you can also go to System > Administration > Software Sources and under the Update tab, change the "Show new distribution releases" dropdown to "Normal releases".

---

### Post by nilsolaris on 2008-12-18
Thank you mate! Works amazingly! (:

---

### Post by Diabolis on 2008-12-18
A guide with screenshots: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

