---
title: "A better way to WPA SUPPLICANT"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by ashrack on 2007-01-24
In order to connect I must use wpa supplicant.

So I've created a bash that does the following:
```
#!/bin/bash

sudo wpa_supplicant -w -i eth0 -D wired -c /etc/wpa_supplicant/wpa_supplicant.conf &
sudo dhclient
```

But I was wondering if there is a better way to do the above thing?

---

### Post by spd106 on 2007-01-24
You can put this information in the /etc/network/interfaces file, see the sub-forum's WPA sticky.

---

