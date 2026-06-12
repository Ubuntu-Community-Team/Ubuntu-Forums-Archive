---
title: "Eicon Diva adsl problem"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by trikkegitaar on 2006-08-04
Hi,

After I updated Ubuntu to 6.06 LTS, my adsl boot scripts do not work anymore.
I use an Eicon Diva USB adsl modem. The driver software is eciadsl-usermode-0.11.
After boot, ps shows S15rc.adsl, rc.adsl, pppd and eciadsl-pppoeci, but it seems pppd is hanging and /var/log/messages shows nothing, only that pppd was started, nothing else.
After manually executing eciadsl-stop and eciadsl-start, everything works fine. Why doesn't it work at boot time? Before the Ubuntu upgrade, it all worked fine...

Thanks,
Patrick Rotsaert

---

