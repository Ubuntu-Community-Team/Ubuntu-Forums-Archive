---
title: "BSNL Teracom DataCard gets extremely hot only with Kubuntu"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by vdeepakkumar on 2013-11-28
I am trying to use BSNL Teracom datacard (with Vodafone 3G SIM) with Kubuntu. Even after 5 minutes of use the data card becomes extremely hot whereas when it runs with Windows 7 (dual boot), I do not find this anomaly. 

Can some one help guide what is happening?

---

### Post by tgalati4 on 2013-11-29
Open a terminal and look through the following:

```
dmesg | tail -40
```

Post anything helpful for troubleshooting.  Try to do it shortly after you plug in the dongle.  It's possible that the device is just not compatible with linux.  Don't let it get too hot or it might fail.

---

