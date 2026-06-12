---
title: "Activation of network connection failed"
date: 2020-02-14
forum: Networking &amp; Wireless
---

### Post by papa.jinzu on 2020-02-14
I am using Ubuntu x64. I get the following message when on the wifi: activation of network connection failed ubuntu wifi. The wifi keeps dropping. Below are the wifi results:

```
http://paste.ubuntu.com/p/qzcxx3zckF/
```

---

### Post by him610 on 2020-02-15
Looks like your country is not set in /etc/default/crda
```

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: [COLOR="#B22222"]DFS-UNSET[/COLOR]
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

```
I don't know if anything else is wrong with it or not. Go to the second post at this location, [https://ubuntuforums.org/showthread.php?t=2413769&highlight=crda]("https://ubuntuforums.org/showthread.php?t=2413769&highlight=crda") where chilli555 says
> Next, I recommend that your regulatory domain be set explicitly. Check yours: then follow the instructions he provides.

---

### Post by CelticWarrior on 2020-02-16
Yes, regulatory domain may play a part but I think the main problem is at the AP "BlueBird" which is using TKIP. If you can manage this AP you should change it to AES. TKIP was deprecated a long time ago and is known to cause problems with certain adapters and mostly in desktop Linux.

---

