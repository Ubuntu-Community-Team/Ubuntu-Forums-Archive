---
title: "rtl8188ee Driver loss"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by Tim_Hallett on 2014-01-23
Hi Aanton,

Long story short, I have been experimenting with various fixes to get my wireless card optimized, then stupidly uninstalled the "Backports-3.12-1" driver. Befoe you say it, "Make Install" again just generates errors Likeley as a result of my attempts to reinstall the kernel.

Attempt to install other driver package just yields
```
Got the tarball, but the make command fails with Error 1 and Error 2
 	 		 			 			 				make -C /lib/modules/3.11.0-12-generic/build  M=/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012  .0516.2013_revison_1-master/base.o
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master/base.c: In function ‘rtl_action_proc’:
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master/base.c:885:32: error: ‘struct  ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master/base.c:886:32: error: ‘struct  ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master/base.c: In function ‘rtl_send_smps_action’:
/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012   .0516.2013_revison_1-master/base.c:1451:24: error: ‘struct  ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012  .0516.2013_revison_1-master/base.o] Error 1
make[1]: *** [_module_/home/tim/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012  .0516.2013_revison_1-master] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [all] Error 2
```
Please help, this is linux, so anythng should be reversible, provided you have the right resources and tools

---

### Post by wildmanne39 on 2014-01-23
Thread closed. Please do not post duplicates, it dilutes community effort. You were already getting help by the best person for wireless issues in your other thread, plesase continue to use that thread.
Thanks

---

