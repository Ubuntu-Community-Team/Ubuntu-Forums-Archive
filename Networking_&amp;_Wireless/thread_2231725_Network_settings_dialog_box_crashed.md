---
title: "Network settings dialog box crashed"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by Eduardo_Ramos_Test on 2014-06-27
Hi all,

Since few days my network settings menu from ubuntu (gnome classic no effects) crashes when invoked (from application->System tools->System settings->Network) without being posible to configure. I can do all the work on command line, but this is annoying me: i have no way to debug this problem because no additional info is shown when this happen. My version is 12.04 but i've heard about similar problems in 13.10.

thank u in advance
BR Eduardo

---

### Post by praseodym on 2014-06-27
Try reinstalling it
```

sudo apt-get install --reinstall network-manager network-manager-gnome
sudo service network-manager restart
```

---

