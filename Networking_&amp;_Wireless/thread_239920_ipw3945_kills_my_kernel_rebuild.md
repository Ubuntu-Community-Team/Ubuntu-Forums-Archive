---
title: "ipw3945 kills my kernel rebuild"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by ese5 on 2006-08-20
I'm trying to build the ubuntu 2.6.15 kernel to include SMP support and am having the following problem.

It seems to be fine until about 10 minutes into the compile when it gets to drivers/built-in.o and ipw3945.c... (I'm trying to build-in support for my intel 3945abg wifi card):
```

drivers/built-in.o: In function `show_channels':ipw3945.c:(.text+0x7d5fc): undefined reference to `ieee80211_get_geo'
drivers/built-in.o: In function `ipw_add_power_capability':ipw3945.c:(.text+0x7f76d): undefined reference to `ieee80211_get_channel'
drivers/built-in.o: In function `ipw_add_supported_channels':ipw3945.c:(.text+0x7f7f9): undefined reference to `ieee80211_get_channel_flags'
:ipw3945.c:(.text+0x7f82d): undefined reference to `ieee80211_get_channel_flags'
:ipw3945.c:(.text+0x7f85d): undefined reference to `ieee80211_get_channel_flags'
:ipw3945.c:(.text+0x7f891): undefined reference to `ieee80211_get_channel_flags'

```

There is about two pages of this (all of it undefined references to iee80211 'stuff') and then it drops me back to the prompt with Error 1.

In menuconfig there are two selections for "Generic IEEE 802.11 networking stack" ...  one of them is (IEEE80211) and one is (IEEE80211_1_1_13)

I have to pick the second one for my intel 3945 wifi card to even show up under device drivers.  If I pick both of them the compile dies when it hits net/built-in.o ... a true conundrum. ](*,)

If anyone has any ideas please let me know as this is driving me crazy.  It's become a three day adventure just to get SMP *and* wifi.  Any help would really be appreciated.  :-)

-ese5

---

