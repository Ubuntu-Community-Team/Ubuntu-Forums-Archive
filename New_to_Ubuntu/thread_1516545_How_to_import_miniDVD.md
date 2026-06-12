---
title: "How to import miniDVD?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by elijahthehun on 2010-06-23
I'm using Ubuntu 10.04 and I want to import some stuff from my camera but it uses miniDVDs to record. I haven't been able to get it working. I initialize my discs on my camera in VR mode usually, but VIDEO mode is also a possibility with my camera. Is there any way to import and edit the clips?

---

### Post by cariboo on 2010-06-23
What does dmesg say when you insert on of the discs? Open a terminal and type:

```
dmesg | tail -n20
```

Paste the output in your next post.

---

### Post by elijahthehun on 2010-06-24
```
[   28.901111] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.926113] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.930797] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.933836] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   29.052930] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.169757] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.175889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.857463] ppdev: user-space parallel port driver
[   35.900063] UDF-fs INFO UDF: Mounting volume '$ Dvd Rewritable Volume $', timestamp 2005/12/31 11:00 (1f10)
[   36.885315] wlan0: deauthenticating from 00:16:b6:a8:b5:fc by local choice (reason=3)
[   36.886667] wlan0: direct probe to AP 00:16:b6:a8:b5:fc (try 1)
[   36.889098] wlan0: direct probe responded
[   36.889104] wlan0: authenticate with AP 00:16:b6:a8:b5:fc (try 1)
[   36.890906] wlan0: authenticated
[   36.890929] wlan0: associate with AP 00:16:b6:a8:b5:fc (try 1)
[   36.893067] wlan0: RX AssocResp from 00:16:b6:a8:b5:fc (capab=0x401 status=0 aid=3)
[   36.893071] wlan0: associated
[   36.894135] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.738301] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   47.677057] wlan0: no IPv6 routers present
```

Seems like a bunch of network stuff, not DVD.

---

### Post by elijahthehun on 2010-06-24
Anyone know?

---

### Post by elijahthehun on 2010-06-24
bump?

---

