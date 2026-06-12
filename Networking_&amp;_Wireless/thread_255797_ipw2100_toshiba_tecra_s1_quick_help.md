---
title: "ipw2100 toshiba tecra s1 quick help"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by inspired7 on 2006-09-12
Been looking through the forums for some sort of resolution but am having difficulties.  I have installed dapper drake 6.06 and a lsmod shows iwp2100 module installed but no wireless devices are showing up with iwconfig.  A dmesg command returns the following:

[17179601.184000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.4
[17179601.184000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[17179601.808000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17179601.968000] ipw2100: eth0: Error initializing Symbol
[17179601.968000] ipw2100: eth0: Error loading microcode: -5
[17179601.968000] ipw2100: eth0: Failed to power on the adapter.
[17179601.968000] ipw2100: eth0: Failed to start the firmware.
[17179601.968000] ipw2100Error calling register_netdev.
[17179601.968000] ipw2100: probe of 0000:02:04.0 failed with error -5


Can someone help me understand how to fix this?  Thanks in advance.

---

### Post by inspired7 on 2006-09-12
I have also tried installing the ndiswrapper now and my lsmod and dmesg commands no longer show the ipw2100 but still nothing shows up in my network settings.  The ndiswrapper says that the device driver is loaded.  Does anyone know how to get this card running?  It is suppose to work out of the box.

---

### Post by mengsk on 2006-09-25
Having the same problem with dapper drake.. was unable to get it to work on any other distros i tried either (Suse, gentoo)

---

### Post by mahmed on 2006-11-18
inspired, 
 have you tried using the ipw2200, i know uit seems silly but i think i've seen this before.

try 
```

> modprobe -r ipw2100
> modprobe -a ipw2200

```

and see what output dmesg returns.  then reload the ipw2100 module 

cheers

---

### Post by Dr. Claw on 2008-02-01
I am also having a problem with getting this interface working. I'm using a Tecra M2 running Ubuntu 7.10.
I get this:
```
:/$ dmesg |grep ipw2100
[   17.176000] ipw2100: Unknown symbol ieee80211_wx_get_encodeext
[   17.176000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[   17.176000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[   17.176000] ipw2100: Unknown symbol ieee80211_txb_free
[   17.176000] ipw2100: Unknown symbol ieee80211_wx_set_encodeext
[   17.176000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[   17.176000] ipw2100: Unknown symbol ieee80211_set_geo
[   17.176000] ipw2100: Unknown symbol ieee80211_rx
[   17.180000] ipw2100: Unknown symbol ieee80211_rx_mgt
[   17.180000] ipw2100: Unknown symbol free_ieee80211
[   17.180000] ipw2100: Unknown symbol alloc_ieee80211
[  748.176000] ipw2100: Unknown symbol ieee80211_wx_get_encodeext
[  748.176000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[  748.176000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[  748.176000] ipw2100: Unknown symbol ieee80211_txb_free
[  748.176000] ipw2100: Unknown symbol ieee80211_wx_set_encodeext
[  748.176000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[  748.176000] ipw2100: Unknown symbol ieee80211_set_geo
[  748.176000] ipw2100: Unknown symbol ieee80211_rx
[  748.176000] ipw2100: Unknown symbol ieee80211_rx_mgt
[  748.176000] ipw2100: Unknown symbol free_ieee80211
[  748.176000] ipw2100: Unknown symbol alloc_ieee80211
[ 1255.152000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[ 1255.152000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[ 1255.152000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[ 1255.232000] ipw2100: eth1: Error initializing Symbol
[ 1255.232000] ipw2100: eth1: Error loading microcode: -5
[ 1255.232000] ipw2100: eth1: Failed to power on the adapter.
[ 1255.232000] ipw2100: eth1: Failed to start the firmware.
[ 1255.236000] ipw2100Error calling register_netdev.
[ 1255.236000] ipw2100: probe of 0000:02:05.0 failed with error -5
```

Any help?

---

### Post by der_vegi on 2008-03-09
I had the same problem getting the '... error -5'. Reinstalling the kernel package linux-image-generic did solve the problem for me. Maybe the state of the key, you can deactivate the card with, does matter at the moment of the kernel (re)installation.?

---

