---
title: "Strange issue with broadcom wireless card"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by betamike on 2007-07-25
I recently helped a friend install 7.04 on his laptop.  The only issue we knew we'd have to deal with was his broadcom wireless card, but his model (4303) is supported by the native drivers, so I assumed we wouldn't have any issues.  I installed the native drivers with no problem (following the wiki page).

Network Manager shows any wireless networks in the vicinity, but it will not connect to any of them (encrypted or not).  Here is some relevant information that might help:

lspci reports:
```
02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)  
```

dmesg:
```

[   71.652000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   71.652000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  181.140000] NET: Registered protocol family 17
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  256.376000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  256.384000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  267.148000] SoftMAC: Open Authentication with 00:14:bf:2e:ae:b2 failed, error code: 1
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  323.476000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134
[  323.484000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  326.820000] SoftMAC: Open Authentication with 00:14:bf:2e:ae:b2 failed, error code: 1
   
```

Can anyone shed some light on the problem?

---

### Post by gnomee on 2007-10-04
I have a similar issue with my broadcom that I was going to post about.

To solve my connection issue I go to connect to other wireless networks and type in a bogus name like "test" then click connect then go back to the list of real networks and boom it works just fine.

---

### Post by DOH on 2007-10-04
Just a question....does the sticky above apply to 4303. I have no idea was just wondering.

---

