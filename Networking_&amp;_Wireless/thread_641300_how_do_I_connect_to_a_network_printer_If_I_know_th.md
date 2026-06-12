---
title: "how do I connect to a network printer If I know the printers IP address"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by mitchelljj on 2007-12-15
hi,

How do I connect to a network printer If I know the printers IP address.

Thanks,

John

---

### Post by vanadium on 2007-12-18
You can use System - Administration - Printing or trhough a browser, [http://localhost:631/](http://localhost:631/) to add a printer. The URI will look like: lpd://xxx.xxx.xx.xx/ Don hold your breath though: I am trying to print on a networked printer. I can set it up, the configuration utlitity detects it, but when I print  the job stalls at "Spooling LPR job, 3% complete..." forever. I once managed to get a test page through, but since then, I never managed printing to work again.

---

