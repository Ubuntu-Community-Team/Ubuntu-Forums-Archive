---
title: "wlan0_rename help."
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by wildseven on 2008-04-05
Hello, i am using ndiswrapper for my broadcom chip in my HP dv6636nr laptop. It was working fine, and all of a sudden my wlan0 device was renamed to wlan0_rename. The blue light is still on and i can see networks under network manager. I can't connect to an AP. I tried manually doing it with
```
iwconfig wlan0_rename essid "essid"
```
and then dhclient wlan0_rename but i get no IP.

I have blacklisted the bcm43xx drivers in order to use ndiswrapper. Can someone please help me. I reinstalled but my /home has it's own partition. After reinstall i mounted it to /home. I reinstall ndiswrapper and i still have it. Is it something in my /home partition?

---

### Post by wildseven on 2008-04-05
ok, well now i can connect but not to my schools APs, just wireless routers kids have brought to school. It's weird. I don't get it. Why is it being renamed and why can't i connect to my School APs?

---

