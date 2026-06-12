---
title: "Network settings not retained after NIC change on Ubuntu 12.04"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by phil215 on 2015-07-06
After a violent thunderstorm the PC failed to connect to the Internet.
Tests eventually determined that one of the Ethernet ports on the router was faulty, but during the process of elimination the NIC was changed for one of the same make and model.
This works as expected after issuing the terminal commands:
```

sudo ifconfig eth1 up
sudo NetworkManager start

```
Unfortunately, these settings are not retained after a reboot. What's the quickest way to ensure that they are retained?

---

