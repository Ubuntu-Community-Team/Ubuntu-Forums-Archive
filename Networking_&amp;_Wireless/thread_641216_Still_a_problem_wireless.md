---
title: "Still a problem? wireless"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by coolclassic on 2007-12-15
Back when gutsy first came out I found I had a internet connection problem this turned out to be an issue with window scaling. To fix the problem the following entry need to be added to etc/sysctl.conf:-  net.ipv4.tcp_window_scaling = 0

Today I did a fresh install downloading gutsy iso. I found the same problem.

My question is why is there still a problem with window scaling?

---

