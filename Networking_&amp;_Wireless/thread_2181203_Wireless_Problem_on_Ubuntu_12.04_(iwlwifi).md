---
title: "Wireless Problem on Ubuntu 12.04 (iwlwifi?)"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by yyttr3 on 2013-10-16
I've been having problems with my wifi connection since I switched to Ubuntu 12.04. The wifi will connect fine and work fine, if I move to a different wifi connection however or hibernate for any reason the computer ceases to recognize connections. A reboot tends to fix this. Even when connected however streaming is simply impossible, I can load and search through reddit or these forums very fast but I can't watch a youtube video.

My problem was worse when I first installed ubuntu and was fixed with
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
I'm using intel centrino wireless 1030.

---

