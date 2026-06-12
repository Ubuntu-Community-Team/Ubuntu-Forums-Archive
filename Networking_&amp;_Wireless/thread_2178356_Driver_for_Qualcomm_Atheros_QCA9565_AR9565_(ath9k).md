---
title: "Driver for Qualcomm Atheros QCA9565/ AR9565 (ath9k) - UBUNTU 12.04"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by mhaebig2 on 2013-10-03
Hi there,
I had to set up my DELL inspiron laptop afresh, and forgot to backup the wireless driver for the ath9k (Qualcomm Atheros QCA9565/AR9565).
So I downloaded the "compat-drivers-3.9-rc4-2-s" and put it on HOME.
Then, these were my steps:
1) sudo apt-get install linux-headers-generic build-essential (worked out)
2) cd compat-drivers-3.9-rc4-2-s (worked)
3) sudo su (worked)
4) ./scripts/driver-select ath9k (worked after changing permissions on two files, allowing file (script) to be executed as programme)
5) make (worked after changing permission to run "scripts/check_config.sh" as programme)
6) using the command "make install", I finally got stuck with this output: "Can't read private key"

Below, find the whole story as it unfolded.

Now, what to do?

Thanks for your help in advance!

Manfred



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
mhaebig@mhaebigDellUbuntu:~$ ls
compat-drivers-3.9-rc4-2-s    Documents         Music     Templates  Videos
compat-wireless-3.6.6-1-snpc  Downloads         Pictures  v3.6
Desktop                       examples.desktop  Public    v3.6.1
mhaebig@mhaebigDellUbuntu:~$ cd compat-drivers-3.9-rc4-2-s
mhaebig@mhaebigDellUbuntu:~/compat-drivers-3.9-rc4-2-s$ sudo su
[sudo] password for mhaebig: 
root@mhaebigDellUbuntu:/home/mhaebig/compat-drivers-3.9-rc4-2-s# ./scripts/driver-select ath9k
bash: ./scripts/driver-select: Permission denied
root@mhaebigDellUbuntu:/home/mhaebig/compat-drivers-3.9-rc4-2-s# ./scripts/driver-select ath9k
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/bcma/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@mhaebigDellUbuntu:/home/mhaebig/compat-drivers-3.9-rc4-2-s# make
make: execvp: ./scripts/check_config.sh: Permission denied
make: *** [modules] Error 127
root@mhaebigDellUbuntu:/home/mhaebig/compat-drivers-3.9-rc4-2-s# make
make -C /lib/modules/3.8.0-31-generic/build M=/home/mhaebig/compat-drivers-3.9-rc4-2-s modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/compat/main.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/compat/compat.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/main.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/regd.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/hw.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/key.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/beacon.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/gpio.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/init.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/main.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/recv.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/xmit.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/link.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/antenna.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/mci.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/rc.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/pci.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ahb.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/debug.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/wow.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/common.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_hst.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/hif_usb.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/wmi.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_txrx.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_main.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_beacon.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_init.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_gpio.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/htc_drv_debug.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9002_hw.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_hw.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/hw.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_phy.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9002_phy.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar5008_phy.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9002_calib.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_calib.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_rtt.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/calib.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/eeprom.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/eeprom_def.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/eeprom_4k.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/eeprom_9287.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ani.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/mac.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9002_mac.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_mac.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_eeprom.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_paprd.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/btcoex.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ar9003_mci.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_hw.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_common.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_htc.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/main.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/status.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/sta_info.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/wep.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/wpa.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/scan.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/offchannel.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/ht.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/agg-tx.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/agg-rx.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/vht.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/ibss.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/iface.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rate.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/michael.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/tkip.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/aes_ccm.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/aes_cmac.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/cfg.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rx.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/spectmgmt.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/tx.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/key.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/util.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/wme.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/event.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/chan.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mlme.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/trace.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/led.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/debugfs.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/debugfs_sta.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/debugfs_netdev.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/debugfs_key.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh_plink.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh_hwmp.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh_sync.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mesh_ps.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/pm.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mac80211.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-regulator.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/core.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/sysfs.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/radiotap.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/util.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/reg.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/scan.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/nl80211.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/mlme.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/ibss.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/sme.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/chan.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/ethtool.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/mesh.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/ap.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/trace.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/debugfs.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/wext-compat.o
  CC [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/wext-sme.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 9 modules
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/compat/compat.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/compat/compat.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_common.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_htc.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_hw.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mac80211.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mac80211.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-regulator.ko
  CC      /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/cfg80211.mod.o
  LD [M]  /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'
root@mhaebigDellUbuntu:/home/mhaebig/compat-drivers-3.9-rc4-2-s# make install

make -C /lib/modules/3.8.0-31-generic/build M=/home/mhaebig/compat-drivers-3.9-rc4-2-s modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  Building modules, stage 2.
  MODPOST 9 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'
make -C /lib/modules/3.8.0-31-generic/build M=/home/mhaebig/compat-drivers-3.9-rc4-2-s "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/compat/compat.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_common.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-regulator.ko
Can't read private key
  INSTALL /home/mhaebig/compat-drivers-3.9-rc4-2-s/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.8.0-31-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'

Note: iwl4965 detected, we're going to disable it. If you would like to enable it later you can run:
    sudo iwl-load iwl4965

Running iwl-enable iwlagn...
Disabling iwl4965 ...    [OK]    Module disabled:
kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
make: execvp: ./scripts/compress_modules: Permission denied
make: *** [install-scripts] Error 127
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---

