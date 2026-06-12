---
title: "Transmission Problem"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by cgoodman on 2010-09-18
Perhaps this isn't the place to post such a specific question however, I class myself as a beginner. I have been using ubuntu for around six months now and have developed a problem with my torrent client - Transmission. Whenever I use Transmission it chokes my normal internet use. The second I open Transmission my browser(Chrome and Firefox) cannot load pages at all. I get speeds of 14m/b and thus should be able to download and browse, None of my torrents are coming down at 14m/b so why is my browser unable to work? Help me please!!!!

Carl

---

### Post by CharlesA on 2010-09-18
By default, it'll use whatever bandwidth you have avalible. You can set the speed limits in the settings of Transmission.

---

### Post by cgoodman on 2010-09-18
O.k. I've had a look at the speed settings and I don't really understand what I need to change to stop this from happening. My speeds are unlimited and this has never affected my browsing before. I have moved house and this is when the problem started. What do I need to change exactly?

---

### Post by lovinglinux on 2010-09-18
You need to set the UPLOAD limit in Transmission to 80% of your UPLOAD bandwidth. Also limiting the download speed could help.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

