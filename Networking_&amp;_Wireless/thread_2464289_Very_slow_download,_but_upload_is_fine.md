---
title: "Very slow download, but upload is fine"
date: 2021-06-28
forum: Networking &amp; Wireless
---

### Post by art0rz2 on 2021-06-28
Just yesterday I installed Kubuntu 21.04 on my new Thinkpad. I quickly realized the download speed while using ethernet is unbearably slow. Speedtest.net reports <1Mbps down and ~5Mbps up (upload is about right for my internet connection). The download speed is fine on Windows on the same laptop. Wifi also works great.

As suggested in other threads, I've tried changing the link speed and duplex and also tried disabling IPv6 but nothing works.

I've also disabled IPv6 as suggested in a few threads.

Any idea what might cause a slow download, but **not** upload?

```
$ speedtest-cli Retrieving speedtest.net configuration...
Testing from XX (xx.xx.xx.xx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by XX (XX) [3.42 km]: 12.151 ms
Testing download speed................................................................................
Download: 0.71 Mbit/s
Testing upload speed......................................................................................................
Upload: 4.55 Mbit/s
```

ethtool -S reports:
```
rx_errors: 414
tx_errors: 0
```

If there's more info I can provide, please let me know.

---

