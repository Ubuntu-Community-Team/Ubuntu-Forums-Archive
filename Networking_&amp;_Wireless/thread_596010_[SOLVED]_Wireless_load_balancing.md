---
title: "[SOLVED] Wireless load balancing"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by siddartha on 2007-10-29
Hello,

Is it possible to do load balancing with two different wireless networks, and with two net cards of course? How?

Cheers,
Sidd

---

### Post by netztier on 2007-10-29
> **siddartha said:**
> Hello,

Is it possible to do load balancing with two different wireless networks, and with two net cards of course? How?

Cheers,
Sidd

[http://ubuntuforums.org/showthread.php?t=530543](http://ubuntuforums.org/showthread.php?t=530543)
In a nutshell: I don't think it works at Layer2 in the same sense as you can bond two FastEthernet interfaces. One of the reasons might be the lack of mii-tool support on WLAN devices and drivers.

It could however work when set up as two independent Layer2 links and with multipath routing that does round-robin distribution of packets amongst the paths.

And if it's about internet access, you'll have to search with "Dual WAN" as kewords and then read quite a bit of material - since this will require some nifty routing tricks and is pretty advanced stuff.

best regards

Marc

---

### Post by siddartha on 2007-10-29
Thank you for the quick reply. Sounds a bit too complicated for what I would achieve doing it. I was a try to increase the output of the internet connection.

---

