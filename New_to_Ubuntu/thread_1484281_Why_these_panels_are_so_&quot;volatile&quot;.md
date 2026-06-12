---
title: "Why these panels are so &quot;volatile&quot;?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by PraveenP on 2010-05-15
Even after locking panel. They are moving here and there on. 

[IMG]http://lh5.ggpht.com/_qcaNf_kWDf0/S-7hI4K7wnI/AAAAAAAAAJQ/W38VpnplY-k/panle.png[/IMG]

Check this screenshot. All panels positions changed. You can see two battery icons, two ibus icons and 2/3 part of wired network connection icon.

WHY???

---

### Post by Phrea on 2010-05-15
I don't know, but mine are in the wrong order there too.

---

### Post by Phrea on 2010-05-15
Made a screenshot of how it looks here.

---

### Post by MichealH on 2010-05-15
This could be that the system reads all the gconf strings in the wrong order thus making them load wrong. This is because every panel item that is default on install is set to a location which is way off the screen. It then sticks to the right. Moving them back will solve the problem

---

### Post by PraveenP on 2010-05-17
> **MichealH said:**
> This could be that the system reads all the gconf strings in the wrong order thus making them load wrong. This is because every panel item that is default on install is set to a location which is way off the screen. It then sticks to the right. Moving them back will solve the problem
Then why two battery icons? why 2 ibus icons? why partial wired network icon? why gconf-editor catches wrong strings? from where? I am sure that I did'nt do anything over there. I feel somebody must fix this..

---

