---
title: "Linksys Wireless Only 1Mb/s"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Rich930 on 2008-07-29
Hey guys. Thanks to many helpful people here ive got most of my ubuntu stuff working properly. There's just one more thing i need help with.

My wireless card only connects with a speed of 1Mb/s as opposed to 54Mb/s, like it should. I read somewhere on this forum that by doing the following you can resolve this issue:

```
iwconfig wlan0 rate fixed
iwconfig wlan0 rate 11M
ifconfig wlan0 down
ifconfig wlan0 up 
```

i tryed this, but every time i do it, the internet dies. It remains connected to the router, but i cant actually get on the internet (no packets are sent at all) for at least 5 minutes and then it comes back again, but STILL at only 1Mb/s.

Any ideas?
Thanks. :D

---

### Post by Rich930 on 2008-07-29
ah ok, so ive got it to 11Mb/s but now it keeps reverting back to 1Mb/s on reboot.

any ideas?
cheers.

---

