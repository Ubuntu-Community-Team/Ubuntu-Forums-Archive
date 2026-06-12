---
title: "My Network Not in List"
date: 2016-10-07
forum: Networking &amp; Wireless
---

### Post by Crimple on 2016-10-07
Hi.

I've been having trouble with some live USBs, the wireless networks are listed and available for connection but not my own network.
This happened with Ubuntu, Xubuntu (16.04, 16.04.1) and Mint 18. Manjaro and OpenSuse show my lan on the list.

Any ideas?
Thanks.

---

### Post by Crimple on 2016-10-07
I managed to find the solution,
I changed the router channel and things were dandy again.
[http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/](http://www.howtogeek.com/howto/21132/change-your-wi-fi-router-channel-to-optimize-your-wireless-signal/)

---

### Post by DuckHook on 2016-10-07
A great CLI tool for finding open channels in Linux is wavemon:```
sudo apt install wavemon
```

---

### Post by Crimple on 2016-10-08
> **DuckHook said:**
> A great CLI tool for finding open channels in Linux is wavemon
Thanks.

---

