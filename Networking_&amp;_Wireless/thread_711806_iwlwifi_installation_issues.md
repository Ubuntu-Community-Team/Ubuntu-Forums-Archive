---
title: "iwlwifi installation issues"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by enbuyukfener on 2008-03-01
[B]***

DISCARD THIS. Sorry, initial google searches and a search here didn't lead me to virtually the exact same issue at [http://ubuntuforums.org/showthread.php?p=4396697](http://ubuntuforums.org/showthread.php?p=4396697) and only described in a Launchpad bug

***[/B]

[COLOR="Silver"]I've been having many problems trying to get wireless working on Hardy and the dev kernel (worked on Gutsy).

After the restricted driver manager will not manage to install the drivers or get them "in use", I tried iwlwifi. 

My network card is the Intel Pro/Wireless A/B/G 3945. I have been following the instructions of [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi). After downloading and extracting the Linux source, creating appropriate symlinks and some other stuff not mentioned in the todo, I finally got rid of the errors and the make command started to run, however it is unsucessful:

(note, I am using SHELL=/bin/bash based on the recommendation from not using it)[/COLOR]

```
root@vostro:~/iwlwifi-1.2.25# make SHELL=/bin/bash
make -C /lib/modules/2.6.24-10-generic/source O=/lib/modules/2.6.24-10-generic/build M=~/iwlwifi-1.2.25/compatible/ EXTRA_CFLAGS="-DCONFIG_IWL3945_DEBUG=y -DCONFIG_IWL4965_DEBUG=y -DCONFIG_IWL3945_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_SENSITIVITY=y -DCONFIG_IWL3945_QOS=y -DCONFIG_IWL4965_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-source-2.6.24'
  CC [M]  ~/iwlwifi-1.2.25/compatible/iwl3945-base.o
In file included from ~/iwlwifi-1.2.25/compatible/iwl3945-base.c:51:
~/iwlwifi-1.2.25/compatible/iwl-3945.h:443: error: expected specifier-qualifier-list before &#8216;ieee80211_key_alg&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_add_station&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:539: error: implicit declaration of function &#8216;MAC_ARG&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:539: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_commit_rxon&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:1161: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_update_sta_key_info&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:1400: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;alg&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:1401: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:1402: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:1402: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_build_tx_cmd_hwcrypto&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2594: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;alg&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2597: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2597: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2597: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2597: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2597: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2617: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2620: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2620: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2620: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2620: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;key&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2620: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;keylen&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2626: error: &#8216;ALG_NONE&#8217; undeclared (first use in this function)
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2626: error: (Each undeclared identifier is reported only once
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2626: error: for each function it appears in.)
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2631: error: &#8216;struct iwl3945_hw_key&#8217; has no member named &#8216;alg&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_get_sta_id&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2739: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_tx_skb&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2820: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:2903: warning: comparison is always true due to limited range of data type
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_print_rx_config_cmd&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:4514: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:4516: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_bg_post_associate&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:6804: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_mac_add_interface&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7096: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_mac_config_interface&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7282: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7286: error: &#8216;IEEE80211_HW_NO_PROBE_FILTERING&#8217; undeclared (first use in this function)
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7302: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: At top level:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7447: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;set_key_cmd&#8217;
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_mac_set_key&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7463: warning: too few arguments for format
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:7472: error: &#8216;cmd&#8217; undeclared (first use in this function)
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: At top level:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:8441: error: unknown field &#8216;open&#8217; specified in initializer
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:8442: warning: initialization from incompatible pointer type
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:8447: warning: initialization from incompatible pointer type
~/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function &#8216;iwl3945_pci_probe&#8217;:
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:8516: error: &#8216;IEEE80211_HW_WEP_INCLUDE_IV&#8217; undeclared (first use in this function)
~/iwlwifi-1.2.25/compatible/iwl3945-base.c:8665: warning: too few arguments for format
make[3]: *** [~/iwlwifi-1.2.25/compatible/iwl3945-base.o] Error 1
make[2]: *** [_module_~/iwlwifi-1.2.25/compatible] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.24'
make: *** [modules] Error 2

```

---

