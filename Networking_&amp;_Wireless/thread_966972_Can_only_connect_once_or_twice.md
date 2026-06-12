---
title: "Can only connect once or twice"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by hanzomon4 on 2008-11-01
I 'm running 8.10 on a 3.1 macbook pro, ath9k oss driver. I'm using wicd and what happens is when I try to switch to a different wifi network it refuses to connect if I try to go back to the wifi network I was just on it won't connect.

---

### Post by hanzomon4 on 2008-11-02
Oh please help this is the only thing keeping me from having a reliable Ubuntu setup again. 

Here's the out put from dmesg ```
[12443.213177] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12443.213231] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12443.413170] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12443.613065] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12443.812093] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12465.255779] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12465.255830] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12465.453146] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12465.654235] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12465.852096] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12478.574413] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12478.574617] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12478.772110] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12478.972171] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12479.176257] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12500.773921] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12500.774005] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12500.973179] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12501.172041] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12501.372173] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12513.977035] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12513.977085] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12514.177168] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12514.377089] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12514.577098] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12533.579182] wlan0: authenticate with AP 00:06:25:60:a3:67
[12533.780095] wlan0: authenticate with AP 00:06:25:60:a3:67
[12533.976082] wlan0: authenticate with AP 00:06:25:60:a3:67
[12534.180122] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12546.747073] wlan0: authenticate with AP 00:06:25:60:a3:67
[12546.747126] wlan0: authenticate with AP 00:06:25:60:a3:67
[12546.945093] wlan0: authenticate with AP 00:06:25:60:a3:67
[12547.145094] wlan0: authenticate with AP 00:06:25:60:a3:67
[12547.345042] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12555.217918] wlan0: authenticate with AP 00:06:25:60:a3:67
[12555.418150] wlan0: authenticate with AP 00:06:25:60:a3:67
[12555.616778] wlan0: authenticate with AP 00:06:25:60:a3:67
[12555.820081] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12622.930978] wlan0: authenticate with AP 00:06:25:60:a3:67
[12622.931062] wlan0: authenticate with AP 00:06:25:60:a3:67
[12623.129953] wlan0: authenticate with AP 00:06:25:60:a3:67
[12623.332054] wlan0: authenticate with AP 00:06:25:60:a3:67
[12623.532104] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12636.267915] wlan0: authenticate with AP 00:06:25:60:a3:67
[12636.368089] wlan0: authenticate with AP 00:06:25:60:a3:67
[12636.568735] wlan0: authenticate with AP 00:06:25:60:a3:67
[12636.771608] wlan0: authenticate with AP 00:06:25:60:a3:67
[12636.970822] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12644.586299] wlan0: authenticate with AP 00:06:25:60:a3:67
[12644.788054] wlan0: authenticate with AP 00:06:25:60:a3:67
[12644.988305] wlan0: authenticate with AP 00:06:25:60:a3:67
[12645.184203] wlan0: authentication with AP 00:06:25:60:a3:67 timed out
[12689.220022] wlan0: authenticate with AP 00:06:25:60:a3:67
[12705.814811] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12706.013080] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12706.213087] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12706.413191] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12721.143083] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12721.143165] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12721.341094] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12721.540046] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12721.740100] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12734.446588] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12734.446671] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12734.648077] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12734.844045] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12735.045521] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12757.270089] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12757.270143] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12757.469081] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12757.669090] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12757.869050] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
[12770.619538] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12770.625739] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12770.825120] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12771.025127] wlan0: authenticate with AP 00:1c:df:21:b8:63
[12771.225177] wlan0: authentication with AP 00:1c:df:21:b8:63 timed out
``` 

BUMP,BUMP,BUMP!!!!!

---

### Post by hanzomon4 on 2008-11-03
Ok I've narrowed it down... if I remove and then modprobe the ath9k driver I can connect again, however the same problem remains if I try to switch to a different wifi or wired connection.

Any tips on what to look into next?

---

### Post by hanzomon4 on 2008-11-03
Well I reported it [Bug Report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/292975")

---

