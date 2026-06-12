---
title: "My WiFi icon has gone missing"
date: 2014-11-03
forum: Networking &amp; Wireless
---

### Post by hakeeminsaf on 2014-11-03
Hello
A few days ago I was downloading all kinds of themes for my computer but then I realized that the WiFi icon in the top right corner of the panel is missing. Even though i restored all the defaults in my Appearance section and all the Icons are default and the theme is Ambiance but the icon is still missing.
Thanks

---

### Post by grahammechanical on 2014-11-03
You can try this

```
killall unity-panel-service
```

That will kill unity-panel-service and it should restart automatically. If it does not.  Run this

```
/usr/lib/unity/unity-panel-service
```

I just tested the first command on my system even though I have all the icons i need. unity-panel-service did restart but it messed up the theme a little bit and a system restart set that right.

Regards.

---

### Post by hakeeminsaf on 2014-11-04
Thanks a lot for trying to help but they didn't work. The first code restarted all the icons as you said but the WiFi icon didn't come back. The second one however gave an error message and removed all the icons so I used the first code to get them back.
Thanks

---

