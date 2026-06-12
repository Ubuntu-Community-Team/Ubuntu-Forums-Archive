---
title: "Wi-Fi networks not detected on Ubuntu 14.04 LTS (rtl8723be)"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by dave189 on 2015-08-02
I have an hp pavillion 15-ab030tx and I recently dual booted windows 8.1  with Ubuntu 14.04LTS. No Wifi networks are being displayed, but if I  host a hotspot from my phone it is visible and I am able to connect from  my laptop. I am also able to connect to hidden networks if I am close  to the router. On windows I am able to connect to any network and range  and visibility arent any issues. I installed the drivers for realtek  found on git hub (rtlwifi_new) with no success. My kernel verision is  3.16.0.45-generic and network adapter is rtl8723be. Any help would be  greatly appreciated.

---

### Post by praseodym on 2015-08-02
Try

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by dave189 on 2015-08-03
Yes I have already done that, but there is no change.

---

