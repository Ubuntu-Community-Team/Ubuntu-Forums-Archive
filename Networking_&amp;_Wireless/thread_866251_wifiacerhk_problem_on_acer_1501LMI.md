---
title: "wifi/acerhk problem on acer 1501LMI"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by exarkun47 on 2008-07-21
Hi

I have Ubuntu 7.10 installed on an Acer Aspire 1501 LMI, and managed to get wifi working via acerhk a few months ago.
Now I did an update (not a dist-upgrade) and it apearantly broke the way i used to bring the wifi up:

sudo modprobe acerhk force_series=1500 usedritek=1 verbose=1
sudo echo 1 | sudo tee > /proc/driver/acerhk/wirelessled

Now it doesn't show any of my two access points anymore, which it should because I ran the update through one of them just a few minutes earlier. I didn't change anything else - just the update (which required a reboot).

I really don't know where to start looking for the problem.

Any help would be appreciated.

---

