---
title: "Libertas.ko installs OK, but no network interfaces"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by rlglende on 2007-11-04
I can see the card with lspci:
05:08.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

I loaded the various driver modules by hand, they didn't have errors:

lsmod | grep 802
ieee80211              38728  1 libertas
ieee80211_crypt_wep     7424  0
ieee80211_crypt_tkip    13312  0
ieee80211_crypt_ccmp     9344  0
ieee80211_crypt         8448  4 ieee80211,ieee80211_crypt_wep,ieee80211_crypt_tkip,ieee80211_crypt_ccmp
mac80211              196360  0
cfg80211                8976  1 mac80211

lsmod | grep libertas

I am missing something, but can't find documentation on OLPC, etc for this driver.  The info available for wireless in general is out of date, chaotic.

Suggestions are very welcome at this point.

Lew

lew@lew-amd64-x2:/var/log$ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

The wireless G router is working fine, a neighbor enjoys using it.



libertas              102928  0
ieee80211              38728  1 libertas

---

