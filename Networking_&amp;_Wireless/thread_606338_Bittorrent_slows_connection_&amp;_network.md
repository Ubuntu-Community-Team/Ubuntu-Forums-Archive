---
title: "Bittorrent slows connection &amp; network"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by drizkill on 2007-11-07
I'm a n00b with linux and I've searched tirelessly to find an answer so please forgive me if this has been answered already. I've got a new install of Gutsy and while I've had a couple bumps, I love it to no end. However, the one hurdle I cannot seem to overcome is the fact that whenever I start a torrent it destroys my network. I've tried disabling ipv6, adding opendns, enabling ipv6 on my router, recreating the connection, etc. I've tried azureus and deluge but the outcome is the same; whenever I start a torrent, within a few seconds, my bandwidth drops by a factor of ten or more and will only clear up if I kill the torrent and reboot. I can go from DL speeds of 12mbps on startup to a max of ~940kbps after starting a torrent where it stays until a restart. The other issue is even though the box is only pulling 100KB/s, my entire network slows down with it. I've tried limiting the number of open connections per torrent, limited upload speed to 5KB/s but nothing is working. If I don't start a torrent I have full speed with no issues...  Does anyone have any ideas?

Couple specs:

AMD 4200+
AMD64 Gutsy (clean install)
WMP54g v4
WRT54GL (dd-wrt sp2)

---

### Post by csat on 2007-11-07
Hi

Check this thread out.  It could be of some help for you.

[http://www.linuxquestions.org/questions/ubuntu-63/torrent-downloads-terrible-slow-in-ubuntu-7.10-595357/](http://www.linuxquestions.org/questions/ubuntu-63/torrent-downloads-terrible-slow-in-ubuntu-7.10-595357/)

Good luck

Csat

---

### Post by kaltsoplyn on 2007-11-10
I switched to Gutsy recently and decided this time to avoid K-apps as much as possible, thus dropping ktorrent in favour of deluge. I now have the exact same problem. When I start deluge my whole network collapses. It is not enough to quit deluge, I have to reboot if I want firefox to even google something... In deluge prefs encryption is on, random port is used (something like port 40000+) but all these make no difference. I have not yet tried disabling ipv6 or dropping RST packages (although the latter doesn't seem like good practice) as other people advice. Another thing I 'll try is to use rtorrent. Anyway I 'll keep trying and posting. If anybody finds a solution please post...

---

