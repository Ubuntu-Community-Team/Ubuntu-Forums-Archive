---
title: "I meess something baddly fith wifi"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by qbox on 2007-10-28
Hi

I have dell inspiron 1520 laptop with dell wireless-n mini card
That is intel ipw4965 wireless card (i think, i search a lot on google for this)
I try to install new drivers and I don't know what I did exactly
i try lot things, step by step guides and everything i find on the internet but nothing.
on the end i follow this steps: 
[http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)
[http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965)

I tried to patch kernell to instal mac4965 and on the final step i receive error message:

qbox@qbox:~/tools/iwlwifi-1.1.19$ sudo modprobe iwl4965
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I don't know what to do and I'm missed in all this thing.
I only waht to install drivers somehow, to get my fiwi card online (to work propertly) and to enable packet capture for my school security project.

Can same one write for me (or to give me links where I can reed more) one step by step guide how to do this tings on the right way. I trying to do this all week, and I'm a lot confused, I search on google all time, I look everywhere on this forum and I don't know what to do any more. I don't know what I have install or remove or modify. 
I'm ready to start from the begining.
Please same one to help me.
Thank a 

p.s. sorry for bad English

---

### Post by qbox on 2007-10-29
Ok back on the way I think.
After this guide
[http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965)
I finally get good results. I didnt receive error message after command
sudo modprobe iwl4965

I didnt receive any message at all. 
now im going on with this guide
[http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)
Can sameone tell me if Im on right way?

---

### Post by qbox on 2007-10-29
Im stack again

I do this
Download, build, and install from snapshots [Recommended]

% wget \
  [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.1.19.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.1.19.tgz)
% tar xvf iwlwifi-1.1.19.tgz
% cd iwlwifi-1.1.19 
% make

then I receive alot of errors.
qbox@qbox:~/tools/iwlwifi-1.1.19$ make
Makefile:22: 
Makefile:23: WARNING: $SHELL not set to bash.
Makefile:24: If you experience build errors, try
Makefile:25: 'make SHELL=/bin/bash'.
Makefile:26: 
make -C /lib/modules/2.6.22-14-generic/source O=/lib/modules/2.6.22-14-generic/build M=/home/qbox/tools/iwlwifi-1.1.19/compatible/ EXTRA_CFLAGS="-DCONFIG_IWLWIFI_DEBUG=y -DCONFIG_IWLWIFI_SPECTRUM_MEASUREMENT=y -DCONFIG_IWLWIFI_HT=y -DCONFIG_IWLWIFI_HT_AGG=y -DCONFIG_IWLWIFI_SENSITIVITY=y -DCONFIG_IWLWIFI_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.o
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1889: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1889: warning: its scope is only this definition or declaration, which is probably not what you want
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘iwl_fill_probe_req’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1991: error: ‘WLAN_EID_HT_CAPABILITY’ undeclared (first use in this function)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1991: error: (Each undeclared identifier is reported only once
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1991: error: for each function it appears in.)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1992: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_ht_capability’ 
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1994: warning: passing argument 2 of ‘iwl_set_ht_capab’ from incompatible pointer type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1995: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_ht_capability’ 
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘iwl_tx_skb’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:2945: error: ‘IEEE80211_TXCTL_HT_MPDU_AGG’ undeclared (first use in this function)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: At top level:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8095: warning: ‘struct ieee80211_ht_additional_info’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8095: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘sta_ht_info_init’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8110: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8111: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8121: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8121: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8126: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8126: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8139: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8140: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8145: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8147: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: At top level:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8159: warning: ‘struct ieee80211_ht_additional_info’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8159: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘iwl_mac_conf_ht’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8166: warning: passing argument 1 of ‘sta_ht_info_init’ from incompatible pointer type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8166: warning: passing argument 2 of ‘sta_ht_info_init’ from incompatible pointer type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8181: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: At top level:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8189: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8190: error: conflicting types for ‘iwl_set_ht_capab’
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:1889: error: previous declaration of ‘iwl_set_ht_capab’ was here
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘iwl_set_ht_capab’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8206: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8207: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8209: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8210: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8211: error: dereferencing pointer to incomplete type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: At top level:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8216: warning: ‘struct ieee80211_ht_capability’ declared inside parameter list
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: In function ‘iwl_mac_get_ht_capab’:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8229: warning: passing argument 2 of ‘iwl_set_ht_capab’ from incompatible pointer type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c: At top level:
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8949: error: unknown field ‘conf_ht’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8949: warning: initialization from incompatible pointer type
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8950: error: unknown field ‘get_ht_capab’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8950: warning: excess elements in struct initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8950: warning: (near initialization for ‘iwl_hw_ops’)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8952: error: unknown field ‘ht_tx_agg_start’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8952: warning: excess elements in struct initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8952: warning: (near initialization for ‘iwl_hw_ops’)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8953: error: unknown field ‘ht_tx_agg_stop’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8953: warning: excess elements in struct initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8953: warning: (near initialization for ‘iwl_hw_ops’)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8954: error: unknown field ‘ht_rx_agg_start’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8954: warning: excess elements in struct initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8954: warning: (near initialization for ‘iwl_hw_ops’)
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8955: error: unknown field ‘ht_rx_agg_stop’ specified in initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8955: warning: excess elements in struct initializer
/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.c:8955: warning: (near initialization for ‘iwl_hw_ops’)
make[3]: *** [/home/qbox/tools/iwlwifi-1.1.19/compatible/iwl4965-base.o] Error 1
make[2]: *** [_module_/home/qbox/tools/iwlwifi-1.1.19/compatible] Error 2
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

Please anyone.

---

### Post by qbox on 2007-10-29
I make with success until here. Now I see this error

qbox@qbox:~/tools/iwlwifi-1.1.19$ ./load
./load: 4: Syntax error: "(" unexpected

---

### Post by qbox on 2007-10-29
can someone translate for me something from this?

[http://forum.ubuntu-fr.org/viewtopic.php?id=128278](http://forum.ubuntu-fr.org/viewtopic.php?id=128278)

---

### Post by qbox on 2007-10-29
I need help
PLEASE

---

