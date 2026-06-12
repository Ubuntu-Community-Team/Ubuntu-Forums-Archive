---
title: "Problem accessing certain sites"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by yosubis on 2007-10-12
I have a problem accessing certain sites. The problem is only in my computer (I checked using other computers in my home) but it's not specific to any browser (Firefox, Opera, Internet Explorer) or OS (Windows, Ubuntu and Linspire LiveCD). The sites I have problems with are:

[www.ign.com](www.ign.com)
[www.destructoid.com](www.destructoid.com)

Could it be connected to following problem that started about a day ago: If I launch aMule with a certain port, it connects without a problem. If I shut it down and launch it again, it says it can't listen to it. I change the port, shut it down and launch it. No problems. Shut it down, and launch again, same problem. I then change to the first port I used, and the circle starts all over again.

I know it's not my network card, since I have two installed and I checked them both.

Any idea, advice or something that can help?

---

### Post by Lambert on 2007-10-13
Try changing the mtu setting

sudo ifconfig mtu 1492

---

### Post by yosubis on 2007-10-13
Didn't work.

---

### Post by yosubis on 2007-10-14
I don't know how, but the problem went away.
Thanks, anyway.

---

