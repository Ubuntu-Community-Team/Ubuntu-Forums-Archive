---
title: "Slow Wifi speeds witn INTEL PRO 4965 card"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by kudar on 2007-10-21
when I try to install the drivers from intel's site this is the errors that i get


root@ubuntubox:/home/kudar/Desktop/iwlwifi-1.1.18# make
Makefile:22:
Makefile:23: WARNING: $SHELL not set to bash.
Makefile:24: If you experience build errors, try
Makefile:25: 'make SHELL=/bin/bash'.
Makefile:26:
make -C /lib/modules/2.6.22-14-generic/source O=/lib/modules/2.6.22-14-generic/build M=/home/kudar/Desktop/iwlwifi-1.1.18/compatible/ EXTRA_CFLAGS="-DCONFIG_IWLWIFI_DEBUG=y -DCONFIG_IWLWIFI_SPECTRUM_MEASUREMENT=y -DCONFIG_IWLWIFI_HT=y -DCONFIG_IWLWIFI_HT_AGG=y -DCONFIG_IWLWIFI_SENSITIVITY=y -DCONFIG_IWLWIFI_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.o
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1824: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1824: warning: its scope is only this definition or declaration, which is probably not what you want
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘iwl_fill_probe_req’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1926: error: ‘WLAN_EID_HT_CAPABILITY’ undeclared (first use in this function)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1926: error: (Each undeclared identifier is reported only once
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1926: error: for each function it appears in.)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1927: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_ht_capability’
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1929: warning: passing argument 2 of ‘iwl_set_ht_capab’ from incompatible pointer type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1930: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_ht_capability’
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘iwl_tx_skb’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:2880: error: ‘IEEE80211_TXCTL_HT_MPDU_AGG’ undeclared (first use in this function)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: At top level:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8009: warning: ‘struct ieee80211_ht_additional_info’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8009: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘sta_ht_info_init’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8024: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8025: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8035: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8035: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8040: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8040: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8053: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8054: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8059: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8061: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: At top level:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8073: warning: ‘struct ieee80211_ht_additional_info’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8073: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘iwl_mac_conf_ht’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8080: warning: passing argument 1 of ‘sta_ht_info_init’ from incompatible pointer type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8080: warning: passing argument 2 of ‘sta_ht_info_init’ from incompatible pointer type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8095: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: At top level:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8103: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8104: error: conflicting types for ‘iwl_set_ht_capab’
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:1824: error: previous declaration of ‘iwl_set_ht_capab’ was here
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘iwl_set_ht_capab’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8120: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8121: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8123: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8124: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8125: error: dereferencing pointer to incomplete type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: At top level:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8130: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: In function ‘iwl_mac_get_ht_capab’:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8143: warning: passing argument 2 of ‘iwl_set_ht_capab’ from incompatible pointer type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c: At top level:
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8859: error: unknown field ‘conf_ht’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8859: warning: initialization from incompatible pointer type
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8860: error: unknown field ‘get_ht_capab’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8860: warning: excess elements in struct initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8860: warning: (near initialization for ‘iwl_hw_ops’)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8862: error: unknown field ‘ht_tx_agg_start’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8862: warning: excess elements in struct initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8862: warning: (near initialization for ‘iwl_hw_ops’)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8863: error: unknown field ‘ht_tx_agg_stop’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8863: warning: excess elements in struct initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8863: warning: (near initialization for ‘iwl_hw_ops’)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8864: error: unknown field ‘ht_rx_agg_start’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8864: warning: excess elements in struct initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8864: warning: (near initialization for ‘iwl_hw_ops’)
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8865: error: unknown field ‘ht_rx_agg_stop’ specified in initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8865: warning: excess elements in struct initializer
/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.c:8865: warning: (near initialization for ‘iwl_hw_ops’)
make[3]: *** [/home/kudar/Desktop/iwlwifi-1.1.18/compatible/iwl4965-base.o] Error 1
make[2]: *** [_module_/home/kudar/Desktop/iwlwifi-1.1.18/compatible] Error 2
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2




I am sure that SHELL is set to /bin/bash but i think there is something else terribly wrong here. any suggestions would be appreciated.

---

