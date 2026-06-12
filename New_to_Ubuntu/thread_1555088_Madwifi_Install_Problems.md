---
title: "Madwifi Install Problems"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Acid6x on 2010-08-17
I download. then go to directory in terminal and extract. all the usual commands until I run "make." which outputs:

```

# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /usr/src/linux-headers-2.6.32-24-generic/ SUBDIRS=/usr/src/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /usr/src/madwifi-0.9.3.3/ath/if_ath.o
In file included from /usr/src/madwifi-0.9.3.3/ath/../net80211/ieee80211_monitor.h:45,
                 from /usr/src/madwifi-0.9.3.3/ath/if_ath.c:71:
/usr/src/madwifi-0.9.3.3/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_attach':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:396: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:661: error: 'struct net_device' has no member named 'open'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:662: error: 'struct net_device' has no member named 'stop'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:663: error: 'struct net_device' has no member named 'hard_start_xmit'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:664: error: 'struct net_device' has no member named 'tx_timeout'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:666: error: 'struct net_device' has no member named 'set_multicast_list'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:667: error: 'struct net_device' has no member named 'do_ioctl'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:668: error: 'struct net_device' has no member named 'get_stats'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:669: error: 'struct net_device' has no member named 'set_mac_address'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:670: error: 'struct net_device' has no member named 'change_mtu'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_detach':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:934: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:979: error: 'struct net_device' has no member named 'stop'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_vap_create':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:988: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1058: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_vap_delete':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1211: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_suspend':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1313: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_resume':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1322: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_intr':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1615: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1806: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_init':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1849: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_stop_locked':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:1969: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_stop':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:2033: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_reset':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:2137: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_startraw':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:2290: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_hardstart':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:2505: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_mgtstart':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:2821: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_key_alloc':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3183: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_key_delete':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3244: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_key_set':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3320: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_key_update_begin':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3335: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_key_update_end':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3356: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_mode_init':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3444: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_updateslot':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3495: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3525: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3573: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:3716: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:4308: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_node_alloc':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:4760: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_node_cleanup':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:4795: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_node_free':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:4849: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_rx_capture':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:5344: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_capture':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:5377: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_recv_mgmt':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:5442: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_rx_tasklet':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:5514: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_grppoll_start':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:5953: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_grppoll_stop':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:6166: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_wme_update':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:6381: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_uapsd_flush':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:6400: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_start':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:6595: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7419: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7440: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_tasklet':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7475: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_tx_timeout':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7498: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_calibrate':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7855: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_scan_start':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7921: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_scan_end':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7941: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_set_channel':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7959: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_set_coverageclass':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7975: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_mhz2ieee':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:7985: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_newstate':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8000: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_setup_stationkey':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8389: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_newassoc':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8549: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_getchannels':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8580: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_xr_rate_setup':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8750: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_setup_subrates':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8779: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_rate_setup':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:8822: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_getstats':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9059: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_set_mac_address':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9082: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_change_mtu':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9114: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_ioctl':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9201: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_sysctl_halparam':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9286: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9286: error: too many arguments to function 'proc_dointvec'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9464: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9464: error: too many arguments to function 'proc_dointvec'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: At top level:
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9479: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9484: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9489: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9494: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9499: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9504: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9509: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9515: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9521: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9526: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9531: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9536: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9541: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9546: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9552: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9557: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9563: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_announce':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9653: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c: In function 'ath_rcv_dev_event':
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9797: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.3/ath/if_ath.c:9799: error: 'struct net_device' has no member named 'open'
make[3]: *** [/usr/src/madwifi-0.9.3.3/ath/if_ath.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.3.3/ath] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.3.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2

```

I'm not sure what I'm doing wrong, but honestly I barely have any experience so I wouldn't know what I'm doing right either..

---

### Post by earthpigg on 2010-08-17
can you show us the documentation you followed?

---

### Post by Acid6x on 2010-08-17
[this page]("http://ubuntuforums.org/showthread.php?t=75451") but i changed the wget link and all to the newer package

---

### Post by earthpigg on 2010-08-17
it looks like you aren't the only one with this problem.

take a look at [this]("http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/").

im not sure what's going on with madwifi. many of the links at [their website]("http://madwifi.org/home/") are giving me 'permission denied' and similar.

if we can't get madwifi working, [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") is always an option.

---

### Post by Acid6x on 2010-08-17
Thanks much. It seems to be working. However, I did get an error from the modprobe (that doesn't seem to affect anything but correct me if I'm wrong).

```
$ sudo modprobe ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/madwifi, it will be ignored in a future release.
```

It seems to me that it wants me to put a .conf extension on those two files. am i right? :)

---

### Post by earthpigg on 2010-08-17
eh, maybe. i'd ignore the message. "future release" can potentially mean 2 years from now. cross that bridge when we come to it. who knows, by the time that future release comes, Ubuntu may work with your wifi adapter out of the box.

glad you got things working.

---

### Post by Acid6x on 2010-08-17
My wifi worked perfectly out-of-box, I wanted madwifi for the injection capabilities.

---

