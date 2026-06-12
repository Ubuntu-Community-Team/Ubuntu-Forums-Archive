---
title: "Qualcomm Atheros Killer E2200 on 14.04.2 Ethernet and Wireless Not Working"
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by Tony_Martinez on 2015-05-28
I recently installed Ubuntu 14.04.2 on my Alienware 17 laptop, and haven't been able to connect
to the internet through wifi or wired connection. I tried running the scripts posted in the sticky
but they require an internet connection.

I was able to find out the make of the Ethernet and Network Controllers.

Ethernet Controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 10)
Network Controller: Qualcomm Atheros Device 003e (rev 20)

I also tried checking available drivers to install and didn't find any.

This is my result after running the command " lspci -n | egrep '0200|0280' | awk '{print$3}' "
```

1969:e091
168c:003e

```

---

### Post by wildmanne39 on 2015-05-28
Thread closed. Please do not post duplicates, it dilutes community effort. If you did not get the help you needed in the other thread just bump it and bring it back to the top after about 12 to 15 hours or so it is okay to do so.
Thanks

---

