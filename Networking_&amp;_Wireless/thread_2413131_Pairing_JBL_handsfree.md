---
title: "Pairing JBL handsfree"
date: 2019-02-21
forum: Networking &amp; Wireless
---

### Post by Alexander_d on 2019-02-21
I have Xubuntu 18.04 on Vaio VPCS12X9R
Trying to pair JBL bluetooth headset. Blueman does not detect this device. It aslo does not see other bt devices (i tried other JBL loudspeaker). However it sees my Samsung smart TV.

Pairing the above devices with smartphones or with Windows works fine.

How can I fix this issue?

P.S. My ps data is here: [http://paste.ubuntu.com/p/r8zyT8VDc8/](http://paste.ubuntu.com/p/r8zyT8VDc8/)
P.P.S. pactl output is the following:

alex@VPCS:~$ pactl load-module module-bluetooth-discover
Failure: Module initialization failed


Thanks!

---

### Post by Alexander_d on 2019-02-22
Solution: Change adapter settings visibility "Visible always" -> "Visible for 15 minutes"

---

