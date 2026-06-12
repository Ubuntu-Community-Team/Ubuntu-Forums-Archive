---
title: "Wireless Networks Not Found"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by HexJunkie on 2006-10-16
I'm trying to use the Ubuntu Network utility to configure my wireless Zyxel G-360 card. The drivers are ACX, and are already included with Ubuntu, so that part is done.

My problem is, the card won't pick up any wireless networks. I know there are several in the area that are picked up by Windows, but not by Ubuntu. When I scan for networks, it tells me that none exist in the area. What could be wrong?

---

### Post by NetworkGuy on 2006-10-16
I have an ACX111 card.   The problem you are probably experiencing is due to the firmware version the kernel is using.   Follow this How-To and it should fix your issue.

[http://ubuntuforums.org/showthread.php?t=233565](http://ubuntuforums.org/showthread.php?t=233565)

---

### Post by HexJunkie on 2006-10-16
I don't want to be too affectionate... but I LOVE YOU! lol
You don't know how frustrated I was trying to get that to work! and that solution solved it! Thanks!

---

### Post by NetworkGuy on 2006-10-16
That's what the community is for.   Just remember that you will have to do this "trick" each time you install a new kernel from update manager or synaptic.

---

