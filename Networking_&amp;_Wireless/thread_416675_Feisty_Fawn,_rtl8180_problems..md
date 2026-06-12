---
title: "Feisty Fawn, rtl8180 problems."
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Deathplanter on 2007-04-21
Since Feisty Fawn I had a few Wifi problems. First of all, module r818x isn't automatically loaded,so I had to add it to /etc/modules. The other problem is that now ESSID is being set to "wlan-a", even though I've set it "wlan-ap" in my /etc/network/interfaces. What could be wrong?

---

### Post by chili555 on 2007-04-21
This is a well-known bug in r818x. In Feisty, the module is blacklisted, so that's why it doesn't load automatically.

The problem of r818x dropping a character from the ESSID has been solved, by some people, by adding an extra character to the ESSID listing in interfaces. In other words, amend interfaces to make wireless-essid wlan-apx so when r818x lops off a character, it comes back to the ESSID you want.

Try it and post back so other r818x fans will know if it works.

---

### Post by Deathplanter on 2007-04-22
It is amazing but It worked! I'm just wondering why this bug wasn't ever fixed... I would never guess it works this way.

---

