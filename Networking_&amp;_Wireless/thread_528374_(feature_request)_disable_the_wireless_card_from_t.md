---
title: "(feature request) disable the wireless card from the network applet"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by AlexBCD on 2007-08-17
Hello,

I don't know if the forum is the right place to submit a feature request (is it ?), but there is something I would like to suggest :

On the network applet on the top-right corner of the screen, you can disable the wireless network. On my laptop, it doesn't really disable the card. In particular, it doesn't save power. The only way I found to do  this is to unload the driver :

```
sudo /sbin/ipw3945*blabla* --kill
sudo rmmod ipw3945
```

I think that it would be nice (especially for newbies) to have this done  by the network applet.

Thank you,

Alexandre

---

