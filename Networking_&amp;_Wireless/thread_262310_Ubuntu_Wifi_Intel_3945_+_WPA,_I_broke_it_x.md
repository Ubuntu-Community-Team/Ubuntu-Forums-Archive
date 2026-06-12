---
title: "Ubuntu Wifi: Intel 3945 + WPA, I broke it :x"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by Buchardt on 2006-09-21
Hey

First of all, I'm completely new to Linux, but I'm really giving it a serious try and want to stay with it. So far I'm a noob though.

I just got my new laptop, Thinkpad x60s, and I have installed Kubuntu on it. The wireless works out of the box, and I have installed knetworkmanager on it. It doesn't work with WPA, and thats my problem!

2 things:

a) I installed a shitload of new packages in the first adept update after the fresh install. On the boot-select-os screen, I had two different linux kernels to choose from - the new and the original, I assume. The thing is, that when choosing the new kernel, the Wifi doesnt work at all :x ?

b) I then used the original kernel, and the wifi still worked, but couldn't connect when trying my WPA network. I tried to install the drivers (I guess I thought they were broken?!), and I think I've ****** up the ieee80211 installation... After a reboot, the wireless didn't work at all in. When I write **dmesg | grep ipw** i get the following lines:
```
[17179592.612000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179592.612000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179592.612000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179592.612000] ipw3945: Unknown symbol ieee80211_txb_free
[17179592.612000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179592.612000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179592.612000] ipw3945: Unknown symbol escape_essid
[17179592.612000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179592.612000] ipw3945: Unknown symbol ieee80211_set_geo
[17179592.612000] ipw3945: Unknown symbol ieee80211_rx
[17179592.612000] ipw3945: Unknown symbol ieee80211_get_channel
[17179592.612000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179592.612000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179592.612000] ipw3945: Unknown symbol ieee80211_get_geo
[17179592.612000] ipw3945: Unknown symbol free_ieee80211
[17179592.612000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179592.612000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179592.612000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179592.612000] ipw3945: Unknown symbol alloc_ieee80211

```

I'm completely and utter lost. Can anyone point me in the right direction / give me some help?

Thanks in advance!

---

### Post by Buchardt on 2006-09-21
To bring an end to this topic:

I completely reinstall Ubuntu (not Kubuntu). I then installed the network-manager-gnome, and it seemed that it still couldn't connect to the WPA network. But, I fixed it...

The thing causing all the trouble is because there was a 'ø' (special danish char) in the key. I changed the key in the router to one without an 'ø', and then it worked instantly.

WPA on my laptop, working out of the box. Nice :>

---

