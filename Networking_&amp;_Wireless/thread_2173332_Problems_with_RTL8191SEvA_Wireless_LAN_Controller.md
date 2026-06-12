---
title: "Problems with RTL8191SEvA Wireless LAN Controller"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by yNAbd7M on 2013-09-09
Hi!

After installing 12.10 I lost my wireless connection. I have found out that this is a common problem and the fix is fairly simple. I downloaded rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 from Realtek and followed this instruction:> [COLOR=#000000]*1. Change to the driver directory*[/COLOR]
[COLOR=#000000]*2. sudo su*[/COLOR]
[COLOR=#000000]*3. make*[/COLOR]
[COLOR=#000000]*4. make install*[/COLOR]
[COLOR=#000000]*5.reboot*[/COLOR]So I:
1. cd to rtl8192se folder inside the rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 folder
2. command sudo su
3. command make and get:> make -C /lib/modules/3.5.0-23-generic/build M=/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se modulesmake[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/hw.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/table.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/sw.o
/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/sw.c: In function &#8216;__check_swenc&#8217;:
/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/sw.c:383:1: warning: return from incompatible pointer type [enabled by default]
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/trx.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/led.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/fw.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/phy.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rf.o
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/dm.o
  LD [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "rtl_query_rxpwrpercentage" [/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko] undefined!
WARNING: "rtl_evm_db_to_percentage" [/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko] undefined!
WARNING: "rtl_signal_scale_mapping" [/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko] undefined!
WARNING: "rtl_process_phyinfo" [/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko] undefined!
  CC      /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se/rtl8192se.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'4. command make install and get:> make: *** No rule to make target `install'.  Stop.

Not knowing what's going on, I try the same procedure in the rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 folder. That is, I exit sudo su and then
1. move up one directory with cd ..
2. sudo su
3. make and get:> make -C /lib/modules/3.5.0-23-generic/build M=/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modulesmake[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o
/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:319:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:319:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o] Error 1
make[1]: *** [_module_/home/celer/What/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [all] Error 2
4. make install and get the same as above

I have no idea what I'm looking at here. Help?

---

