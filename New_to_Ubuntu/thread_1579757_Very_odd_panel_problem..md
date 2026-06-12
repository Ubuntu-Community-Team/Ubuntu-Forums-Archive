---
title: "Very odd panel problem."
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-09-22
Hey, my top panel seems to be acting a bit strange, when i boot up, sometimes my sound control and my wireless icon are gone, and im not able to click my shut down, restart etc icon at the right ether. I came across a program a while back that restored the panels to default but i can't find it anywhere. Dose anyone have it? also, sometimes when i boot up my wireless network option is unticked and my sound wont work till i restart my laptop. Anyone had the same problems?

---

### Post by andrewthomas on 2010-09-22
to restore default panel

```
rm -r ~/.gconf/apps/panel
```

---

