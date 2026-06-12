---
title: "USB Wireless setup problem"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by ntt2007 on 2008-01-07
Hi I need some help with my USB Wireless setup (WEP encryption). I have the Linksys WUSB54G which is supposed to be supported under linux. But neither knetworkmanager nor KMenu->System Settings->Network could set it up (knetworkmanager doesn't even notice there's an wireless device). I don't now if this is significant but I found this error in dmesg log:

[   39.398924] ieee80211_init: failed to initialize WME (err=-17)
[   39.428215] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   39.428245] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   39.428271] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   39.428312] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register

FYI, my distro is Kubuntu Gutsy 7.10 amd64. The following kernel packages are installed:

ii  linux-generic                              2.6.22.14.21
ii  linux-headers-2.6.22-14                    2.6.22-14.47
ii  linux-headers-2.6.22-14-generic            2.6.22-14.47
ii  linux-headers-generic                      2.6.22.14.21
ii  linux-image-2.6.22-14-generic              2.6.22-14.47
ii  linux-image-generic                        2.6.22.14.21
ii  linux-kernel-devel                         2.6.22-14.47
ii  linux-libc-dev                             2.6.22-14.47
ii  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.10
ii  linux-restricted-modules-common            2.6.22.4-14.10
ii  linux-restricted-modules-generic           2.6.22.14.21
ii  linux-ubuntu-modules-2.6.22-14-generic     2.6.22-14.37

Any helps is appreciated.

Thanx,
Toan

---

### Post by rustybronco on 2008-01-07
what version are you using v1, v2 or v4 of the wusb54g (they have different chipsets)

---

### Post by ntt2007 on 2008-01-07
I have version 4. Is it supported in Linux ?

---

### Post by Hightide on 2008-01-08
You may find this thread useful

[http://ubuntuforums.org/showthread.php?t=588045&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=588045&highlight=Linksys+WUSB54G)

:guitar:

---

### Post by ntt2007 on 2008-01-08
Thanks a lot. I follow the instruction and it works now.

Cheers,
Toan

---

