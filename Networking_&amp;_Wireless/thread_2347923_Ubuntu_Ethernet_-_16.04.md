---
title: "Ubuntu Ethernet - 16.04"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by oblivion12 on 2016-12-29
Problem | Ethernet
I was just playing some CSGO then out of no where all my connections dropped, so i just replugged my Ethernet cable. That basically did nothing. My Computer also doesnt show wireless connections near by, so I had been using a ethernet for this entire time but now it doesnt connect to the ethernet even though it says its plugged it. I am stuck with a PC without any internet. Please help.

---

### Post by praseodym on 2016-12-30
Please show the output of
```

lspci -nnk | grep -iA2 net
```

---

