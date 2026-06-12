---
title: "MAC address filtering"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by cetol on 2007-05-26
Having just installed 7.04 on my Dell laptop I finally got the wireless working. I needed to disable MAC address filtering on my router. Can ay one tell me why this is? If possible I prefer to enable this function

---

### Post by RomeReactor on 2007-05-27
Hi. The only reason I can think of as to why you would need to disable mac filtering, would be not knowing the correct mac address of your wireless card. Open a terminal (Applications-->Accessories-->Terminal) and enter the following:
```
sudo lshw -class network
```
find your card, and look at the **serial:** number. Now check that it is the same on your router's configuration.

---

