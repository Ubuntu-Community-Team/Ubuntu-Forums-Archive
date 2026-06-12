---
title: "HP scanner networking fails"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2016-11-06
HPLIP claims to support network scanning on our libraries new HP8740 multifunction printer. It prints fine but can't see the scanner. I can ping the scanner OK. I think the issue is that hplip fails due to missing dependencies. Particularly pyqt and pyqt5-dbus. Maybe others as I can't get past those 2. I see pyqt-* many pkgs but not just pyqt. I can't find them anywhere to download. Before we had a networked HP scanner and HPLIP 3.16.3 configed fine. It was an HP 8600 so I was not anticipating any issues. I need to get this working on 12 xubuntu 16.04 computers very soon. I also opened suggested port 5353 by entering in terminal. I have all users in scanner group.

```
sudo ufw allow 5353
```

Thank you

---

