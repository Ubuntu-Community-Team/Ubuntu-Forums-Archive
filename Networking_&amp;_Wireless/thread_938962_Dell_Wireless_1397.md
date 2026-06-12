---
title: "Dell Wireless 1397"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by yds753 on 2008-10-05
I am trying to install my dell wireless 1397 minicard in Hardy,
after some search, I found out I needed the Broadcom Wireless 43XX drivers, which were explained at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)
but after this installation, it still doesn't work (when I type lshw -C Network in the terminal, it is identified as an 'UNCLAIMED' network controller)
What am I doing wrong ?


EDIT:SOLVED: with the windows drivers of 1390 version and ndiswrapper, it works!

---

