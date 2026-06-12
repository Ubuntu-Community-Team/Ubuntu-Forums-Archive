---
title: "Manual setup for WEP and wireless"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by chocolatedude91 on 2007-05-09
Hi,

I have a RaLink RT2500 chip in a Linksys card that I cannot seem to make work.  Can anyone point me to a manual setup method (in the interfaces file) instead of Network Manager?  I use an ASCII 5-digit WEP key.

Thanks.

---

### Post by chocolatedude91 on 2007-05-09
I saw the WPA method on the home page of the forums.  Is the procedure the same for WEP?  I know nothing technological, and I want my internet to work!  Otherwise, Ubuntu is great.

---

### Post by chili555 on 2007-05-09
Here is a disguised version of my interfaces file:```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid GBR1
wireless-key 096cxxxxxxxxxxxe4afe 

```If your key is ASCII, prepend the key with s: like this:```
wireless-essid s:123xy
```

WPA is a whole different matter. If you need WPA, and you probably do, check here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

