---
title: "Broadcom/Wireless error wlan0: disassociate(reason=3)"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by johnehowe on 2008-11-03
In troubleshooting a Broadcom Wireless issue I discovered that I was getting repeated errors when executing the **dmesg** command in a terminal window 

[ 4137.748058] **wlan0: disassociate(reason=3)**
[ 4138.535906] wlan0: Initial auth_alg=0
[ 4138.535914] wlan0: authenticate with AP 00:21:29:68:80:9a
[ 4138.537405] wlan0: RX authentication from 00:21:29:68:80:9a (alg=0 transaction=2 status=0)



I removed the wpa-supplicant.conf file and added the encryption key to the /etc/network/interfaces file. This resolved the issue

---

### Post by mattydee on 2008-12-08
Did you ever discover what the underlying reason was? What is "reason=3"?

I am having the same issues so I'll give your solution a shot.

---

