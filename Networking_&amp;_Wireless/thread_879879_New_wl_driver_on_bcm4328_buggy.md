---
title: "New wl driver on bcm4328 buggy?"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by PinkFloyd102489 on 2008-08-04
I upgraded using the hardy-proposed repos yesterday to grab the latest restricted modules so I can finally get rid of the wretched ndiswrapper. The wl driver pops right up and is in use, except Network Manager shows it disconnecting and reconnecting like crazy. It's not actually doing that, just showing that it is.

Also, it's very temperamental about simultaneous actions going on. If Im downloading one thing then download another, the speed on the first download drops to almost nothing.

Then I find out that the wl driver doesnt support packet injection.


Is anyone else having this problem or know what to do?

---

### Post by jjrp78 on 2008-11-09
Yes sir, Im having the same problem plus this driver reports to be connected with a lower speed than ndiswrapper so I had to go back to ndiswrapper =(

---

