---
title: "Unstable wireless connection Atheros AR9287"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by Canaryguy on 2013-11-01
Hi,

A friend has a computer with Ubuntu 13.10 x64 installed.

His wireless connection gets disconnected frequently. He has told me that after some minutes the connection is lost and then he has to connect again. He says the signal strength is good. With Windows seems to work without problems.

In "Software & Updates > Additional Drivers" no propietary drivers appear.

He has an Atheros AR9287 card. I include with this post two screenshots that he sent me.

I've searched for solutions on the internet. I told him to try the following solutions:

1º echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf 
But the problem continues.

2º sudo modprobe ath9k
The problem continues.

Anybody has/had the same problem and know how to fix it?

Thanks in advanced.

---

### Post by protoss96 on 2013-11-01
try to manually install drivers, pick the one you need from [http://wireless.kernel.org/en/users/Drivers/Atheros](http://wireless.kernel.org/en/users/Drivers/Atheros) and try to install.

---

### Post by Canaryguy on 2013-11-01
ok protoss96.

So, I go to that page I look for Ath9k and get the lastest version in Backports.
I found backports-3.11.6-1 and I get a compressed file. But neither my friend nor I know how to install it :-(

---

