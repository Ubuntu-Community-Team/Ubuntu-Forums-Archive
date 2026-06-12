---
title: "[SOLVED] SMC2635W - doesn't connect"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by almos.dinnyes on 2008-08-26
Dear All,

I try to use an SMC2635W PCMCI wifi card, after an ubuntu reinstall (it worked before). I see in the network manager my router's ssid, but it doesn't connect :( My router is not secured at all, so it should connect easily.

What shall I do?

---

### Post by Elpram on 2008-08-26
I have the same problem.  My SMC wireless card (2005L or something) used to work in fiesty, but no longer works in Hardy.  I am using the 64bit version.  Networks show up, but never connect.

Thanks,
Elpram

---

### Post by almos.dinnyes on 2008-08-28
SOLVED! :)

I used this guide: 
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

I had to blacklist rt2400pci
I downloaded the driver from here:
[http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html)

---

