---
title: "How to synchronize clock of two computers in the same LAN within millisecond level?"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by Igenyar on 2014-03-27
After running "ntpdate ntp.ubuntu.com" on both computers, I still see the difference more than 10 seconds between the two. 

Is there a way to synchronize it better? Thanks.

---

### Post by tgalati4 on 2014-03-27
To within milliseconds--use *ntp*.

[http://askubuntu.com/questions/297560/ntpd-vs-ntpdate-pros-and-cons](http://askubuntu.com/questions/297560/ntpd-vs-ntpdate-pros-and-cons)

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

With a driftfile and some tweaking, you can get down to milliseconds.

The Swiss definition of a chromometer specification is +6 to -4 seconds per day, so it's conceivable that your real-time clocks drift, so between two computers it's quite possible to get a 10-second difference.

---

