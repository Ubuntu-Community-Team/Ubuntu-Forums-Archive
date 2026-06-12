---
title: "Networking problems since upgrading to Hardy"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by DAE_JA_VOO on 2008-05-04
How's it guys

I just installed Hardy on my girlfriend's machine. She was running Gutsy before.

Since the upgrade, she has NO network connectivity. I've assigned the exact same IP, subnet, and gateway address details but it still doesn't work.

Any idea what's going on?

---

### Post by superprash2003 on 2008-05-04
are you able to ping the router(gateway)?

---

### Post by DAE_JA_VOO on 2008-05-04
Nope, i can't even ping the router. It's definitely running, as the rest of the network is running fine (i'm posting this from one of the windows machines).

Is there a possibility that the NIC driver wasn't installed? How would i check?

---

### Post by superprash2003 on 2008-05-04
type ifconfig in the terminal and post output here..

---

### Post by c007c on 2008-05-04
I found this problem trying to upgrade wirelessly. Not sure, but it appears that the upgrade sequence disables wireless at critical time, which doesnt allow the backport/restricted drivers to download/install. I plugged in the ethernet, and after about 5 mins, the drivers updated, and wireless was back.

---

### Post by iosdb on 2008-05-04
i have the same problem so i use the 7.10 version...
if someone can help how i can resolve the problem with the network please tell me... thnx..

---

