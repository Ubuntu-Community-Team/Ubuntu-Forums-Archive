---
title: "ipw2200: Unknown symbol ieee80211_xx"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by s-bris on 2007-02-06
Hi,

I tried to follow the article by luca-linux on setting up wireless.  It appears now that I'm in a worse situation than before - after performing the remove-old and make on the downlaod and extracted ieee802 file my eth1 is no longer working and picking up anything....

Below is the steps I went through after I did the remove-old in the dir.
I get the following symbol errors after I do the make and make install...

steve@steve-laptop:~/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3$ make

make -C /lib/modules/2.6.17-10-generic/build M=/home/steve/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3 MODVERDIR=/home/steve/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
rm: cannot remove `/home/steve/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3/net': Is a directory
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2


steve@steve-laptop:~/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3$ dmesg | grep ipw[17179588.124000] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[17179588.124000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[17179588.124000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[17179588.124000] ipw2200: Unknown symbol ieee80211_txb_free
[17179588.124000] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[17179588.124000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[17179588.124000] ipw2200: Unknown symbol escape_essid
[17179588.124000] ipw2200: Unknown symbol ieee80211_freq_to_channel
[17179588.128000] ipw2200: Unknown symbol ieee80211_set_geo
[17179588.128000] ipw2200: Unknown symbol ieee80211_rx
[17179588.128000] ipw2200: Unknown symbol ieee80211_channel_to_index
[17179588.128000] ipw2200: Unknown symbol ieee80211_rx_mgt
[17179588.128000] ipw2200: Unknown symbol ieee80211_get_geo
[17179588.128000] ipw2200: Unknown symbol free_ieee80211
[17179588.128000] ipw2200: Unknown symbol ieee80211_is_valid_channel
[17179588.128000] ipw2200: Unknown symbol alloc_ieee80211



steve@steve-laptop:~/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

