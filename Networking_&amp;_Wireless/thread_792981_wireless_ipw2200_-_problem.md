---
title: "wireless ipw2200 - problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by jrdm on 2008-05-13
hi all!

i accidentally remove my ipw2200 with this command:

```
sudo modprobe -r ipw2200
```

Now, my wireless network isn't working. Can someone help me solving this problem?

Have an Acer aspire 1692WMmi, 1Gb Ram,  Intel Centrino 1,73Ghz, Ati x700, Inel PRO/Wireless 2200BG

thanks,
jrdm

---

### Post by chili555 on 2008-05-13
```
sudo modprobe ipw2200
```That will re-insert it. By the way, if you do:```
sudo apt-get install linux-backports-modules-hardy-generic
```I believe it includes a slightly improved ipw2200 driver.

---

### Post by jrdm on 2008-05-13
> **chili555 said:**
> ```
sudo modprobe ipw2200
```That will re-insert it. By the way, if you do:```
sudo apt-get install linux-backports-modules-hardy-generic
```I believe it includes a slightly improved ipw2200 driver.

well, i've tried the 
```
sudo modprobe ipw2200
```

but i've got this message right here:

```
joao@iAcerLaptop:/$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
:(

i installed the linux-backports-modules-hardy-generic but didn't notice any changes...

Am i doing the things right?
Thanks for the patience, i'm still a rookie.

---

### Post by chili555 on 2008-05-13
What did dmesg tell us?```
dmesg | grep ipw2200
```You might also try:```
sudo modprobe ieee80211
sudo modprobe ipw2200
```

---

### Post by jrdm on 2008-05-13
> **chili555 said:**
> What did dmesg tell us?```
dmesg | grep ipw2200
```

```
joao@iAcerLaptop:~$ dmesg | grep ipw2200
[   16.707657] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   16.707797] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   16.707842] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   16.708002] ipw2200: Unknown symbol ieee80211_txb_free
[   16.708073] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   16.708261] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   16.708303] ipw2200: Unknown symbol escape_essid
[   16.708413] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   16.708674] ipw2200: Unknown symbol ieee80211_set_geo
[   16.708835] ipw2200: Unknown symbol ieee80211_rx
[   16.708963] ipw2200: Unknown symbol ieee80211_channel_to_index
[   16.709250] ipw2200: Unknown symbol ieee80211_rx_mgt
[   16.709294] ipw2200: Unknown symbol ieee80211_get_geo
[   16.709374] ipw2200: Unknown symbol free_ieee80211
[   16.709593] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   16.709701] ipw2200: Unknown symbol alloc_ieee80211
[  127.655511] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[  127.655830] ipw2200: Unknown symbol ieee80211_wx_set_encode
[  127.655942] ipw2200: Unknown symbol ieee80211_wx_get_encode
[  127.656326] ipw2200: Unknown symbol ieee80211_txb_free
[  127.656496] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[  127.656879] ipw2200: Unknown symbol ieee80211_wx_get_scan
[  127.656985] ipw2200: Unknown symbol escape_essid
[  127.657237] ipw2200: Unknown symbol ieee80211_freq_to_channel
[  127.657818] ipw2200: Unknown symbol ieee80211_set_geo
[  127.658183] ipw2200: Unknown symbol ieee80211_rx
[  127.658474] ipw2200: Unknown symbol ieee80211_channel_to_index
[  127.659111] ipw2200: Unknown symbol ieee80211_rx_mgt
[  127.659223] ipw2200: Unknown symbol ieee80211_get_geo
[  127.659409] ipw2200: Unknown symbol free_ieee80211
[  127.659900] ipw2200: Unknown symbol ieee80211_is_valid_channel
[  127.660147] ipw2200: Unknown symbol alloc_ieee80211

```

> **chili555 said:**
> You might also try:```
sudo modprobe ieee80211
sudo modprobe ipw2200
```

```
joao@iAcerLaptop:~$ sudo modprobe ieee80211
FATAL: Module ieee80211 not found.

```

:(
once again, thanks.

---

### Post by chili555 on 2008-05-13
> FATAL: Module ieee80211 not found.Wow! That's pretty weird. Is this the stock built-in ipw2200 module or did you compile some tar.gz from somewhere? If the latter, it sounds like it did not go well. Please do:```
sudo updatedb
locate ieee80211.ko
```*updatedb* will take a few moments. Please let us know.

---

