---
title: "weird ZD1211 problem - uploading 'data' when no applications are sending any"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by jonnylinuxnerd on 2007-12-01
I have two zd1211 USB wifi dongles which both have the same problem. The first one has just about broke anyway (it has two be plugged in and out before the firmware gets uploaded), but my second one works fine in this aspect. 

The problem is, on both dongles, when I'm on the internet and I go on KWaveControl (it displays the exact same info in ifconfig as well), I appear to be uploading huge amounts of data  (over 8Mb/s, faster than my ISP allows so it can't be something connecting to the internet). However, when i type 'sudo lsof -i' and close ALL(daemons included) apps, there still appears to be huge amount of data being transferred (it occurs in spikes every few seconds).:confused: Of course all this 'data' transfer makes my internet dead slow, because it maxes out the wireless bandwidth. This is so weird because I cannot find any applications that are using the connection, PLUS the problem doesn't occur using a wired connection.

If any one has the slightest clue what is going on it would be appreciated. Thanks.:)

---

### Post by Lambert on 2007-12-02
> **jonnylinuxnerd said:**
> I have two zd1211 USB wifi dongles which both have the same problem. The first one has just about broke anyway (it has two be plugged in and out before the firmware gets uploaded), but my second one works fine in this aspect. 

The problem is, on both dongles, when I'm on the internet and I go on KWaveControl (it displays the exact same info in ifconfig as well), I appear to be uploading huge amounts of data  (over 8Mb/s, faster than my ISP allows so it can't be something connecting to the internet). However, when i type 'sudo lsof -i' and close ALL(daemons included) apps, there still appears to be huge amount of data being transferred (it occurs in spikes every few seconds).:confused: Of course all this 'data' transfer makes my internet dead slow, because it maxes out the wireless bandwidth. This is so weird because I cannot find any applications that are using the connection, PLUS the problem doesn't occur using a wired connection.

If any one has the slightest clue what is going on it would be appreciated. Thanks.:)

If it's not happening on wired connection, I don't think it's a demon or app. 

A copule things I would suggest.

Check your syslog file for anything happening with wireless connection.

run the iwconfig command and look for dropped packets or transmission errors. (what kind of encryption are you using? maybe turn off encryption and see if you still have the problesm)

use the tcpdump command to see what the actuall traffic is. If you don't know how to use this, do a search or use the "man tcpdump" page to read about it. or come back here and I or someone can help. A simple use would be.

```

sudo tcpdump -i wlan0

```

---

### Post by jonnylinuxnerd on 2007-12-06
According to iwconfig they are no dropped packets. I usually use WPA encryption I tried WEP and no-encryption and it didn't make any difference.


However, tcpdump came up with some intresting things when all I was doing was pinging google.
```
19:43:09.437262 IP 192.168.11.2 > eh-in-f99.google.com: ICMP echo request, id 40265, seq 34, length 64
19:43:09.625429 IP eh-in-f99.google.com > 192.168.11.2: ICMP echo reply, id 40265, seq 34, length 64
19:43:09.625672 IP 192.168.11.2.33345 > buffalo.setup.domain: 47319+ PTR? 99.207.14.72.in-addr.arpa. (43)
19:43:09.674797 IP buffalo.setup.domain > 192.168.11.2.33345: 47319 1/0/0 (77)
19:43:10.440804 IP 192.168.11.2 > eh-in-f99.google.com: ICMP echo request, id 40265, seq 35, length 64
19:43:10.601138 IP eh-in-f99.google.com > 192.168.11.2: ICMP echo reply, id 40265, seq 35, length 64
19:43:10.604963 IP 192.168.11.2.33345 > buffalo.setup.domain: 26289+ PTR? 99.207.14.72.in-addr.arpa. (43)
19:43:10.629760 IP buffalo.setup.domain > 192.168.11.2.33345: 26289 1/0/0 (77)
19:43:11.444386 IP 192.168.11.2 > eh-in-f99.google.com: ICMP echo request, id 40265, seq 36, length 64
19:43:11.608455 IP eh-in-f99.google.com > 192.168.11.2: ICMP echo reply, id 40265, seq 36, length 64
19:43:11.608701 IP 192.168.11.2.33345 > buffalo.setup.domain: 31993+ PTR? 99.207.14.72.in-addr.arpa. (43)
19:43:11.633843 IP buffalo.setup.domain > 192.168.11.2.33345: 31993 1/0/0 (77)
```
That keeps happening over and over as long as I keep pinging google

Also the most intresting thing I could find in syslog is this
```

Dec  6 19:42:24 jonathan-desktop kernel: [10562.632651] eth2: no IPv6 routers present
Dec  6 19:43:01 jonathan-desktop kernel: [10583.151944] device eth2 entered promiscuous mode
Dec  6 19:43:01 jonathan-desktop kernel: [10583.151953] audit(1196970181.893:20): dev=eth2 prom=256 old_prom=0 auid=4294967295
Dec  6 19:43:27 jonathan-desktop kernel: [10597.422774] device eth2 left promiscuous mode
Dec  6 19:43:27 jonathan-desktop kernel: [10597.422784] audit(1196970207.614:21): dev=eth2 prom=0 old_prom=256 auid=4294967295

```
Not sure if that promiscuous thing is normal but it sounds intressting :lolflag:

Anyway, it appears as I suspected that my computer is tallking to my router too much but I still don't know why. It is a Buffalo WHR-G54S. Should I try resetting it (I'd rather not if I don't have to because I'd have to reconfigure it again)?

Also, thanks Lambert for your previous suggestions. :)

---

