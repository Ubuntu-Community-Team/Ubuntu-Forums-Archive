---
title: "Writing a kernel module to extend radiotap fields"
date: 2019-08-20
forum: Networking &amp; Wireless
---

### Post by technosam on 2019-08-20
According to the [man page]("http://manpages.ubuntu.com/manpages/bionic/man9/ieee80211_radiotap.9freebsd.html"), Ubuntu only supports the following fields:

  IEEE80211_RADIOTAP_TSFT

  IEEE80211_RADIOTAP_FLAGS
  IEEE80211_RADIOTAP_RATE
  IEEE80211_RADIOTAP_CHANNEL
  IEEE80211_RADIOTAP_DBM_ANTSIGNAL
  IEEE80211_RADIOTAP_DBM_ANTNOISE
  IEEE80211_RADIOTAP_DBM_TX_POWER
  IEEE80211_RADIOTAP_ANTENNA
  IEEE80211_RADIOTAP_DB_ANTSIGNAL
  IEEE80211_RADIOTAP_DB_ANTNOISE
  IEEE80211_RADIOTAP_XCHANNEL


  I want to write a kernel module that will supply the [VHT]("https://www.radiotap.org/fields/VHT.html") and [MCS]("https://www.radiotap.org/fields/MCS.html") fields if the driver can provide them.

  I've written kernel modules before, but it's been a while, and I'm  not sure exactly where to start for network stuff. I would appreciate a  general outline if anyone is able to give it.

The particular version I'm supporting is 14.04 ARM, but I would expect that the general starting point should be the same as 18.04 x86.

---

### Post by praseodym on 2019-08-20
I have no clue about programming kernel modules, however, you may find some hints in the source code of the module cfg80211

```
modprobe -c | grep -i "IEEE80211_radio"
alias symbol:ieee80211_radiotap_iterator_init cfg80211
alias symbol:ieee80211_radiotap_iterator_next cfg80211
```

---

