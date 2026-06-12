---
title: "madwifi versus madwifi-ng?"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-04-11
I've noticed that there are both madwifi and madwifi-ng drivers. What's the difference between them? Are the maintained by the same people? Which is better, or what advantages do they have?

I've noticed the "-ng" suffix on other programs as well, like aircrack and aircrack-ng. Does the "-ng" suffix have a universal meaning?

---

### Post by spd106 on 2007-04-11
Generally, ng = next generation

Madwifi-ng is a rewrite of madwifi-old incorporating better code, greater chipset support and new features. It is being developed by the current maintainers of madwifi-old and is considered to be not quite up to the same level of maturity as madwifi-old. That's why it's still at version 0.9.3. I believe the decision to move to -ng on Edgy was taken to enable the support of newer cards. It wasn't quite ready for inclusion in Dapper LTS.

If you want to learn more then have a look around the dev website at [http://madwifi.org](http://madwifi.org). There's an interesting guide to the advanced features of madwifi-ng such as Virtual AP mode.

---

