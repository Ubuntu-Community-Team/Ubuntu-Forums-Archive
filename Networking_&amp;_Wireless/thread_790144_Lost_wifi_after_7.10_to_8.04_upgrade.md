---
title: "Lost wifi after 7.10 to 8.04 upgrade"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by webber224 on 2008-05-11
I have been using my Broadcom 4306 rev 3 driver in Gutsy without problem using the firmware created from bcm43xx-fwcutter in /lib/firmware.
Having upgraded to 8.04 it will not connect, showing a message  about firmware and then failing to open a connection to load fwcutter (I have no wired access). The firmware is still in /lib/firmware why can't 8.04 find it? or should I move it somewhere else.
Needless to say, am I new to Ubuntu and this is my first upgrade. I have tried to follow the many howto's but it is tricky with internet access only via windows. Any help would be greatly appreciated.

---

### Post by f37u5g0d on 2008-05-13
All I can tell you for sure is that the fwcutter you need to use is a new version (11).  The file that is on your computer which you used in 7.10 is the old version (06).  As of right now I don't know if there is a way to get wireless working without a connection although if you can get a wired connection all you would have to do is install the newest version of fwcutter (11) and then use the "windows wireless drivers" app (which handles ndsiwrapper for you) and your wireless will be up and running :).

---

