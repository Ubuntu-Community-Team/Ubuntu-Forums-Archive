---
title: "WUSB54GPv4 in Feisty"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by 200mg on 2007-05-16
{WUSB54GP}

This card worked in edgy with the islsm driver.  I cannot get it to work with Feisty.  I have tried using ndiswrapper to install the rt2500 driver, seems to install ok.

```
/etc/ndiswrapper/rt2500usb$ ndiswrapper -l
rt2500usb : driver installed
```

Even with those drivers installed I get this


```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

apparently the drivers that came with feisty do not work??

```
lsmod |grep 80211
mac80211              175364  2 prism54usb,prism54common
cfg80211               22920  1 mac80211

```

any ideas?

---

