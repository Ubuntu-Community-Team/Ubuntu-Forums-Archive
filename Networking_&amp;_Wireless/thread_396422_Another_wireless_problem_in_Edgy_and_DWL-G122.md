---
title: "Another wireless problem in Edgy and DWL-G122"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by keonne on 2007-03-29
Hi guys,

 Just another wireless problem in Edgy. I have tried all I know (which i admit is rather limited) to get my D-LINK DWL G122 to work

Basically i installed the Serial Monkey drivers ([http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)) successfully so when i run iwconfig i get

```

RT73 WLAN ESSID:"The Force"
Mode: Managed  Frequency:2.462 Ghz  Access Point: 00:00:00:00:00:00
Bit Rate=54 Mb/s
RTS thr:off  Fragment thr:off
Link Quality=87/100 Signal level: -52 dBm Noise level:-79 dBm
Link Quality:0 Signal level:0 Noise level:113
Rx invalid nwid:0  Rxinvalid crypt:0  Rxinvalid frag:0
Tx excessive retries:0 Invalid: misc Missed beacon:0

```



and when I do 

```

 ifconfig rausb0 up
iwlist rausb0 scanning

```

I get:

```

rausb0    Scan completed :
Cell 01 - Address: 00:00:00:00:00:00
ESSID: "The Force"
Mode:Managed
Channel:1
Encryption key:off
Bit Rates: 0 kb/s

```

Obviously the access points arent 00:00:00:00:00:00
While the wireless network is successfully sniffed, it isnt sending any information... therefore i cant get on the interwebs!

any suggestions

Thanks,

Keonne

---

### Post by keonne on 2007-03-29
any ideas?

---

