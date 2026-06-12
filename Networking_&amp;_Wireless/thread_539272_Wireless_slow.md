---
title: "Wireless slow?"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by meheheh on 2007-08-31
The other threads are old, and didn't help me, so I decided to create a new one.

I'm currently using a Belkin F5D7010 (BCM4306) with the bcm43xx drivers. However, when using wireless, there are tons of dropped connections, lots of latency (pings within MY OWN NETWORK were getting to 70+ ms) and speeds never go beyond 65 kB/s.

I've already disabled IPV6, and my DNS is set to use OpenDNS (208.67.222.222, 208.67.220.220)

Also, dmesg reveals a whole bunch of messages like these:

```
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1126
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
[  758.668000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1128
```

Also, my internet just zips along when I'm plugged in wired ethernet.

Any help please?

---

### Post by bmartin on 2007-08-31
I used to have this problem, too. Now I use ndiswrapper and the problem's all gone. Try [this thread]("http://ubuntuforums.org/showthread.php?t=405990").

---

### Post by baixinhu on 2008-02-05
same problem now... fresh 7.10 BCM4318 
with the restricted modules the connection is to slow even when I access the router page, and connection drops frequently :S can't install ndiswrapper
help any one

---

### Post by Mogurijin on 2008-02-24
ndiswrapper can be installed via the Ubuntu live cd. Just put it in, disable all of your repositories (in Administration -> Software Sources), and enable the cd-rom (same place).

PS
I'm also having problems with slow internet speeds over my wireless, but it is a Netgear adapter, which requires the use of ndiswrapper (at least for the WG111V1). So, ndiswrapper doesn't help my speeds.

---

