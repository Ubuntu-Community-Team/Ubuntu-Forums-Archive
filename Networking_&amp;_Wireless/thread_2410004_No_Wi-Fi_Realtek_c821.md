---
title: "No Wi-Fi Realtek c821"
date: 2019-01-09
forum: Networking &amp; Wireless
---

### Post by bonfire299 on 2019-01-09
Hello,

My laptop doesn't seem to see wifi adapter, I did apt update, turned off secure boot but it didn't work out.

I have tried also this one - [https://ubuntuforums.org/showthread.php?t=2380522](https://ubuntuforums.org/showthread.php?t=2380522) and didn't succeded


[http://paste.ubuntu.com/p/YywGkjtZfP/](http://paste.ubuntu.com/p/YywGkjtZfP/)

Thank you in advance :)

---

### Post by jeremy31 on 2019-01-09
Try this, it is a bit newer fix
```
sudo apt install git dkms build-essential
git clone https://github.com/tomaspinho/rtl8821ce.git
cd rtl8821ce
sudo ./dkms-install.sh
```
Reboot

---

### Post by bonfire299 on 2019-01-09
I have tried it out and doesn't work, just in case reinstalled ubuntu and did again everything step by step

---

### Post by jeremy31 on 2019-01-09
New wireless script results then

---

### Post by bonfire299 on 2019-01-10
[https://pastebin.com/iZnfqEwM](https://pastebin.com/iZnfqEwM)

---

### Post by jeremy31 on 2019-01-10
Strange, do you get any errors when you
```
cd ~/rtl8821ce
make clean
make
sudo make install
```

---

### Post by bonfire299 on 2019-01-10
> 
bonfire@hp:~$ cd ~/rtl8821ce
bonfire@hp:~/rtl8821ce$ make clean
#make -C /lib/modules/4.15.0-43-generic/build M=/home/bonfire/rtl8821ce clean
cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
bonfire@hp:~/rtl8821ce$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-43-generic/build M=/home/bonfire/rtl8821ce  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-43-generic'
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_cmd.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_security.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_debug.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_io.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_ioctl_query.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_ioctl_set.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_ieee80211.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_mlme.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_mlme_ext.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_mi.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_wlan_util.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_vht.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_pwrctrl.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_rf.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_recv.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_sta_mgt.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_ap.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_xmit.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_p2p.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_tdls.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_br_ext.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_iol.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_sreset.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_btcoex_wifionly.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_btcoex.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_beamforming.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_odm.o
  CC [M]  /home/bonfire/rtl8821ce/core/efuse/rtw_efuse.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/osdep_service.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/os_intfs.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/pci_intf.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/pci_ops_linux.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/ioctl_linux.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/xmit_linux.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/mlme_linux.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/recv_linux.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/wifi_regd.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/rtw_android.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/rtw_proc.o
  CC [M]  /home/bonfire/rtl8821ce/os_dep/linux/ioctl_mp.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_intf.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_com.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_com_phycfg.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_phy.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_dm.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_btcoex_wifionly.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_btcoex.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_mp.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_mcc.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_hci/hal_pci.o
  CC [M]  /home/bonfire/rtl8821ce/hal/led/hal_pci_led.o
  CC [M]  /home/bonfire/rtl8821ce/hal/hal_halmac.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_halinit.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_mac.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_cmd.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_phy.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_dm.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/rtl8821c_ops.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/hal8821c_fw.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_halinit.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_halmac.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_io.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_xmit.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_recv.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_led.o
  CC [M]  /home/bonfire/rtl8821ce/hal/rtl8821c/pci/rtl8821ce_ops.o
  CC [M]  /home/bonfire/rtl8821ce/hal/efuse/rtl8821c/HalEfuseMask8821C_PCIE.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_api.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_api_88xx.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_func_88xx.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_api_88xx_usb.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_api_88xx_sdio.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_api_88xx_pcie.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_8821c_pwr_seq.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_api_8821c.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_func_8821c.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_api_8821c_usb.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_api_8821c_sdio.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_api_8821c_pcie.o
  CC [M]  /home/bonfire/rtl8821ce/hal/halmac/halmac_88xx/halmac_8821c/halmac_8821c_phy.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_debug.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_antdiv.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_antdect.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_interface.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_hwconfig.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/halphyrf_ce.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_dig.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_pathdiv.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_rainfo.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_dynamicbbpowersaving.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_powertracking_ce.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_dynamictxpower.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_adaptivity.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_cfotracking.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_noisemonitor.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_acs.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_beamforming.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_dfs.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/txbf/halcomtxbf.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/txbf/haltxbfinterface.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/txbf/phydm_hal_txbf_api.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_adc_sampling.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_kfree.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_ccx.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/phydm_psd.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8723bwifionly.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8822bwifionly.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8821cwifionly.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8192e1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8192e2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8723b1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8723b2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8812a1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8812a2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8821a1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8821a2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8703b1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8723d1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8723d2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8822b1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8822b2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8821c1ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/btc/halbtc8821c2ant.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/halhwimg8821c_bb.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/halhwimg8821c_mac.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/halhwimg8821c_rf.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/phydm_hal_api8821c.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/phydm_regconfig8821c.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/halphyrf_8821c.o
  CC [M]  /home/bonfire/rtl8821ce/hal/phydm/rtl8821c/phydm_iqk_8821c.o
  CC [M]  /home/bonfire/rtl8821ce/platform/platform_ops.o
  CC [M]  /home/bonfire/rtl8821ce/core/rtw_mp.o
  LD [M]  /home/bonfire/rtl8821ce/8821ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/bonfire/rtl8821ce/8821ce.mod.o
  LD [M]  /home/bonfire/rtl8821ce/8821ce.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-43-generic'
bonfire@hp:~/rtl8821ce$ sudo make install
[sudo] password for bonfire: 
install -p -m 644 8821ce.ko  /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.15.0-43-generic
bonfire@hp:~/rtl8821ce$ 



I have no idea if it would help if I'll install last version of Ubuntu

---

### Post by jeremy31 on 2019-01-10
Reboot and see if it works

---

### Post by bonfire299 on 2019-01-10
You're a wizard, thank you very very much.

---

### Post by jeremy31 on 2019-01-10
Since dkms install didn't seem to work you will have to run these commands after every kernel update
```
cd ~/rtl8821ce
make clean
make
sudo make install
```
Then reboot

---

