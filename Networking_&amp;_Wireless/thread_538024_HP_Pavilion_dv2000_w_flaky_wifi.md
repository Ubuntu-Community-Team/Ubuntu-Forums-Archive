---
title: "HP Pavilion dv2000 w/ flaky wifi"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2007-08-29
So my sister has the notebook listed in the title. I installed the bcm43xx-fwcutter (the one in the main repositories) as it has a broadcom chipset and the wireless began to work. However, though it works, it is working really flaky. Sometiems it connects, sometimes it doesn't. On the front is a little wireless indicator light that I think turns orange when wifi isn't working and blue when it is or something (correct me if I am wrong) and I am not sure how it works or how to get it to work with linux. Anyone having similar problems with their machine or any ideas?

---

### Post by bmartin on 2007-08-30
I had this problem when I used the firmware, too. Use ndiswrapper instead. [Here's a thread]("http://ubuntuforums.org/showthread.php?t=405990") that'll install it using a graphical installer. If you feel more comfortable installing everything by hand, [here's a thread]("http://ubuntuforums.org/showthread.php?t=297092") for that.

---

