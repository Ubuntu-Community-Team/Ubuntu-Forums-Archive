---
title: "Acx100 Very Slow"
date: 2005-06-10
forum: Networking &amp; Wireless
---

### Post by blastmotor on 2005-06-10
I have an Airlink B/G PC card, and it is going very slow (average in synaptic is 30KB/s). The average for my wired connection is closer to 200KB/s. In XP pro this is not the case. iwconfig produces this:

wlan0     IEEE 802.11g/b+  ESSID:"NETGEAR"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:DA:8C:56
          Bit Rate=11 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=42/100  Signal level=19/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It originally was set for 1mb/s, but I changed it to 11Mb/s (I only have a 802.11b router). Even at b speeds I should be seeing close to what my wired connection can do for downloads. How else can I speed this up?

Thanks, 
Ryan

---

### Post by blastmotor on 2005-07-12
It's still going very slow. Any ideas? Also, on boot up, it takes about 1-2 mins to get past the network setup part. When I use the wired connection this is not the case.

Thanks in advance,
-Ryan

---

### Post by danjo on 2005-07-16
[QUOTE=blastmotor]It's still going very slow. Any ideas? Also, on boot up, it takes about 1-2 mins to get past the network setup part. When I use the wired connection this is not the case.

Thanks in advance,
-Ryan[/QUOTE]

I don`t have this Problem with my ACX100. But you can try this: [http://houseofcraig.net/acx100_howto.php](http://houseofcraig.net/acx100_howto.php) 

Good look
Danjo

---

### Post by Lunde on 2005-07-16
[QUOTE=danjo]I don`t have this Problem with my ACX100. But you can try this: [http://houseofcraig.net/acx100_howto.php](http://houseofcraig.net/acx100_howto.php) 

Good look
Danjo[/QUOTE]
 The above link is great, but get the latest driver, not the one refered to in Cragis howto.
[http://rhlx01.fht-esslingen.de/~andi/acx100/](http://rhlx01.fht-esslingen.de/~andi/acx100/)

---

### Post by danjo on 2005-07-16
Hello again,

It seems you you have bad link and connection quality.

You can also try to push your tx power up to 18 (this is default value for my acx100).

If this does not work, you can also check the sensitivity value (must try). #

I hope this could help you

Danjo

---

