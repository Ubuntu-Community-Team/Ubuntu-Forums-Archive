---
title: "KTorrent Upload Speeds"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by hankaaron88 on 2010-09-30
I was wondering if there is anyway to uncork my upload speed in KTorrent. I just did a speed test on my connection and my upload speed is 0.49Mb/S. The max I've seen my upload speed hit in KTorrent is less than 100KiB/s which by my estimation is less than a quarter of what my max should be.

---

### Post by robsoles on 2010-10-01
Quite a few factors go into how quickly you can upload using any bittorrent client.

1) Is your client itself throttling? (look for speed limit options)
2) Has your ISP identified your P2P traffic and throttled it? (Look for encryption options in your client - require encryption)
3) Say you have 4 leechers (people downloading from you) and each of them has 25KB/s download speed limit - altogether they will only pull 100KB/s
4) Is the OS reserving bandwidth for other activity?

There are other reasons that are too abstract (to me) for me to try to describe and doubtlessly there are reasons that don't occur to me.


I have 800KB/s upload on my connection at home and if I don't throttle my upload out of qBittorrent then it uses too much of my allocated bandwidth, I am on a contract for 100Gb on-peak and 100Gb off-peak. The most I have seen my client upload while unthrottled is about 260KB/s.


HTH.

---

### Post by hankaaron88 on 2010-10-01
I was just wondering if there were some ports that I could open to increase my upload speed like there are for my download speed.

---

