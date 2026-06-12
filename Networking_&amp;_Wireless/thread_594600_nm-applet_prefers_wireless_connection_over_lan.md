---
title: "nm-applet prefers wireless connection over lan"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by ghostlines on 2007-10-28
I'm using Gutsy and it seems that nm-applet prefers wireless connections even if they
aren't working(i don't have the passwords to the wireless routers). I have an ethernet cable hooked up to my laptop from my router. So i would expect that Gutsy like Feisty would prefer the lan over the wireless routers. 

My work around is right clicking the nm-applet icon and deselecting the wireless connection. Then opening a terminal and restarting /etc/init.d/networking . Then it works fine. 

Does anyone have this problem, or know how fix this so that by default nm-applet prefers lan over wireless?

---

