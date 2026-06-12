---
title: "Can't see or connect to wireless network (noob)"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by applexcore on 2008-05-24
I installed Ubuntu 8.04 on my old Dell Latitude D600 to see if I liked it.

There are no wireless networks being displayed so I clicked on "Connect to other wireless network." I typed in my wireless network name that doesn't have a password and it won't connect. 

I typed in: ```
sudo iwlist scan
```

and got: ```
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wmaster0 Interface doesn't support scanning.
wlan0 Interface doesn't support scanning : Network is down
```


Any help would be appreciated. I'm new to Linux so I might need extra details. Thanks

---

### Post by applexcore on 2008-05-24
BTW, my wireless router is a Linksys WRT54G.

Wireless card is a Broadcom BCM4309 802.11a/b/g (rev 02)
(Hardware Support on Ubuntu.com doesn't have it listed, just BCM4306)

What should I do?

---

### Post by Ayuthia on 2008-05-25
Your card appears to be partially supported by the Linux native Broadcom driver.  You might want to try NDISwrapper.

Here is a decent step by step guide:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Here is another one with more options:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If you want to try the native driver:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

