---
title: "[SOLVED] Restoring Open Office Apps to my applications menu?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-12-14
Long story short, I deleted the Open Office 2.4 from my hardy install, thinking I could put in v.3.0 instead, until I learned about stability issues in linux with such ventures, so I erased it all, and reinstalled 2.4 from the hardy source repo. Add/remove apps says I do indeed have them reinstalled, but I can't get them to show up in my panel menu window under "office" where they originally were.

How do I do that? Thanks.

---

### Post by Majorix on 2008-12-14
Install the program called alacarte and then run it:
```
sudo apt-get install alacarte
alacarte
```
That script helps you administer your menus.

---

### Post by threezee on 2008-12-14
Right Click on the Menu Bar. Select Edit Menus. Hightlight the office bar and tick all the applications that you want to show up under the office menu.

---

### Post by BastardNamban on 2008-12-14
Thanks guys! All fixed :)

---

