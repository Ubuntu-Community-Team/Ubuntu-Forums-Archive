---
title: "Problems with Driver for Asus USB-AC53 Nano"
date: 2017-05-31
forum: Networking &amp; Wireless
---

### Post by hsisneros on 2017-05-31
Hello,

I have been stuck trying to get this network adapter to work for the past few days now, with no luck [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]  . I checked my device alias and it matches one listed in the 88x2bu  driver. I searched around and found a download link to a 88x2bu driver  (below). I have tried multiple things to get it running; however, When I  type 'make' into the terminal, I receive a bunch of errors (below).  I've also tried ignoring the errors because it seems to install  perfectly using 'sudo make install' but when I try to 'modprobe' it, I  receive another error (below).

88x2bu driver download I found:
[http://www.edimax.com/edimax/mw/cufiles/files/download/Driver_Utility/EW-7822ULC_Linux_Driver_1.0.0.9.zip](http://www.edimax.com/edimax/mw/cufiles/files/download/Driver_Utility/EW-7822ULC_Linux_Driver_1.0.0.9.zip)

'make' error:
```
/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.c:  In function &#8216;rtw_ioctl_wext_private&#8217;:
/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.c:13333:6:  error: implicit declaration of function &#8216;is_compat_task&#8217;  [-Werror=implicit-function-declaration]
  if (is_compat_task())
      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target  '/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.o'  failed
make[2]: ***  [/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.o]  Error 1
Makefile:1491: recipe for target  '_module_/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333'  failed
make[1]: *** [_module_/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-53-generic'
Makefile:1874: recipe for target 'modules' failed
make: *** [modules] Error 2

```

'modprobe' error:
```
modprobe: ERROR: could not insert '88x2bu': Exec format error
```

my device alias:
```
usb:v0B05p184Cd0210dc00dsc00dp00icFFiscFFipFFin00
```

'lusub' of device:
```
Bus 001 Device 003: ID 0b05:184c ASUSTek Computer, Inc.
```

'uname -a' information:
```
Linux hayden-linux 4.8.0-53-generic #56~16.04.1-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux
```

I am sure there are a lot of others who are stuck on this adapter as  well as there doesn't seem to be a whole lot of information on it. If  anyone has any suggestions or can point me in the right direction that  would be great!

Thanks in advance,

Hayden

---

### Post by jeremy31 on 2017-05-31
Split from [https://ubuntuforums.org/showthread.php?t=2362577](https://ubuntuforums.org/showthread.php?t=2362577)

The exec format error usually occurs when you are using the wrong .config or Module.symvers file to compile against.  Post the result for ```
modinfo 88x2bu
```

---

### Post by hsisneros on 2017-05-31
Hello @jeremy31,

These are my results:
```
modinfo 88x2bu
filename:       /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/88x2bu.ko
version:        v5.1.7_19806.20161025_BTCOEX20161024-3333
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     09FE2EFDEA40D5AC4849404
alias:          usb:v7392pB822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392pC822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p184Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p1841d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB812d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB82Cd*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_drv_log_level:set log level when insert driver module, default log level is _DRV_INFO_ = 4 (uint)
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_btcoex_enable:BT co-existence on/off, 0:off, 1:on, 2:by efuse (int)
parm:           rtw_ant_num:Antenna number setting, 0:by efuse (int)
parm:           rtw_force_igi_lb:force IGI low-bound, 0:no specified (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_pwrtrim_enable:int
parm:           rtw_initmac:charp
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_powertracking_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
parm:           rtw_en_napi:int
parm:           rtw_en_gro:int

```

Also, I didn't see that you split the post into this thread so I ended up making a new thread, but it can be deleted now - [https://ubuntuforums.org/showthread.php?t=2362670&p=13651396#post13651396](https://ubuntuforums.org/showthread.php?t=2362670&p=13651396#post13651396) - my apologies.

---

### Post by jeremy31 on 2017-05-31
What is the result for ```
ls /home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
```
It seems your module was built for an older kernel but put in your new kernel directory

---

### Post by hsisneros on 2017-05-31
Results:
```
$ ls /home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
88x2bu.ko     88x2bu.o  hal          Kconfig        Module.symvers  rtl8822b.mk
88x2bu.mod.c  clean     ifcfg-wlan0  Makefile       os_dep          runwpa
88x2bu.mod.o  core      include      modules.order  platform        wlan0dhcp

```

> It seems your module was built for an older kernel but put in your new kernel directory

Ahh yeah, you're right. Hmm, that's not good, I wonder if there's still a way to get it running.

---

### Post by jeremy31 on 2017-05-31
I would try
```
cd /home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
make clean
make
sudo make install
```
Reboot and see if it works.  There were a few differences in the download I got from your link and it built fine after a ran the make clean command

---

### Post by hsisneros on 2017-05-31
I just re-downloaded it (just to be sure) and ran the commands you suggested.

```
make clean
make
sudo make install
```

It gave me this on 'sudo make install'

```
install -p -m 644 88x2bu.ko  /lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/
install: cannot stat '88x2bu.ko': No such file or directory
Makefile:1880: recipe for target 'install' failed
make: *** [install] Error 1

```

It doesn't look like the make file is making the .ko file.

---

### Post by hsisneros on 2017-06-01
I also found this [https://github.com/brandon-bailey/rtl8822bu](https://github.com/brandon-bailey/rtl8822bu) which states that my device should work with it; however, I haven't had luck with this one either. This driver compiles and installs perfectly with no errors, I can also modprobe it just fine. The problem is that my usb device doesn't recognize it (still says driver = to nothing) and my device alias is different than the device alias' within the driver. I'm not sure if there's a way to add my device alias into the driver before compiling.

When comparing the two, it looks like the 88x2bu is the same as 8822bu driver (I could be wrong though).

Edit:

I seemed to get a little farther. I added the device and vendor id to '/sys/bus/usb/drivers/rtl8822bu/new_id' and it seems to register it now; however, I get these errors in 'dmesg':

```
[30209.181520] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.read_chip_version ###
[30209.181522] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.init_default_value ###
[30209.181524] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.intf_chip_configure ###
[30209.181525] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.read_adapter_info ###
[30209.181527] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_power_on ###
[30209.181529] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_power_off ###
[30209.181531] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_init ###
[30209.181532] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_deinit ###
[30209.181534] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.init_xmit_priv ###
[30209.181536] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.free_xmit_priv ###
[30209.181538] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_xmit ###
[30209.181539] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.mgnt_xmit ###
[30209.181541] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_xmitframe_enqueue ###
[30209.181543] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.init_recv_priv ###
[30209.181545] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.free_recv_priv ###
[30209.181546] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.inirp_init ###
[30209.181548] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.inirp_deinit ###
[30209.181550] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.dm_init ###
[30209.181552] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.dm_deinit ###
[30209.181554] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_dm_watchdog ###
[30209.181555] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.set_bwmode_handler ###
[30209.181557] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.set_channel_handler ###
[30209.181559] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.set_chnl_bw_handler ###
[30209.181561] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.SetHwRegHandler ###
[30209.181563] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.GetHwRegHandler ###
[30209.181564] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.GetHalDefVarHandler ###
[30209.181566] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.SetHalDefVarHandler ###
[30209.181568] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.GetHalODMVarHandler ###
[30209.181570] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.SetHalODMVarHandler ###
[30209.181571] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.UpdateRAMaskHandler ###
[30209.181573] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.SetBeaconRelatedRegistersHandler ###
[30209.181575] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.Add_RateATid ###
[30209.181577] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.fill_h2c_cmd ###
[30209.181578] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.fill_fake_txdesc ###
[30209.181580] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.hal_get_tx_buff_rsvd_page_num ###
[30209.181582] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.fw_dl ###
[30209.181584] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_init_value ###
[30209.181586] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_reset_value ###
[30209.181587] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.silentreset ###
[30209.181589] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_xmit_status_check ###
[30209.181591] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_linked_status_check ###
[30209.181593] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_get_wifi_status ###
[30209.181595] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.sreset_inprogress ###
[30209.181596] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.init_mac_register ###
[30209.181598] RTW: ### rtw_hal_ops_check - Error : Please hook HalFunc.init_phy ###
[30209.181616] RTW: rtw_usb_primary_adapter_init Failed!
[30209.181617] RTW: usb attached..., try to reset usb device

```

---

### Post by jeremy31 on 2017-06-01
Let's see if we can find the module built by the other source code and install it
```
locate 88x2bu.ko
```

---

### Post by hsisneros on 2017-06-01
Yeah, when you first download the file from Edimax (the link in first post) it comes with:

```
88x2bu.ko
88x2bu.mod.c
88x2bu.mod.o
88x2bu.o
```

files in the driver folder. It removes them when you use 'make clean'.

I re-downloaded the driver and '88x2bu.ko' is located in:

```
/home/hayden/Downloads/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
```

'locate 88x2bu.ko' returns:

```
/lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/88x2bu.ko
/lib/modules/4.8.0-53-generic/kernel/drivers/net/wireless/88x2bu.ko

```

---

### Post by jeremy31 on 2017-06-02
What version of Ubuntu are you using?  I can get the module to compile with Ubuntu 16.04 with kernel 4.4.0-66 but it fails with the 4.8 kernels

I might have a fix
```
cd Desktop
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu
make clean
make
sudo make install
```
Reboot

---

### Post by hsisneros on 2017-06-04
Thank you so much for your help Jeremy!

I changed my kernel to 4.4.70, performed:

```
make clean
make
sudo make install
modprobe 88x2bu
```

and it compiled and installed without any problems at all. My wireless adapter immediately started working and I was able to connect to my wifi.

Thank you again so much for the help!

Hayden

---

### Post by walts48 on 2017-11-01
I recently bought one of these and also had no problems when following the instructions. Thanks Jeremy!

I had a kernel upgrade recently. It appears I will have to compile and install after each new kernel, and it will no longer work when my 16.04 LTS updates to 18.04 LTS.

Is this correct?

---

### Post by helektron on 2018-06-07
Hi jeremy, sorry for bother you but I need your magic to fix a problem compiling your driver [https://github.com/jeremyb31/rtl8822bu](https://github.com/jeremyb31/rtl8822bu) for kernel 4.15

I've this error compiling it. Could you please help me? I'll pay you a beer :) Many thanks!!

```
&#10140;  Desktop git clone https://github.com/jeremyb31/rtl8822bu.gitcd rtl8822bu
make clean
make
sudo make install
Cloning into 'rtl8822bu'...
remote: Counting objects: 779, done.
remote: Total 779 (delta 0), reused 0 (delta 0), pack-reused 779
Receiving objects: 100% (779/779), 3.48 MiB | 2.60 MiB/s, done.
Resolving deltas: 100% (347/347), done.
make -C /lib/modules/4.15.0-22-generic/build M=/home/helektron/Desktop/rtl8822bu clean
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-22-generic'
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-22-generic'
cd hal/phydm/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/phydm/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-22-generic/build M=/home/helektron/Desktop/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-22-generic'
  CC [M]  /home/helektron/Desktop/rtl8822bu/core/rtw_cmd.o
In file included from /home/helektron/Desktop/rtl8822bu/include/osdep_service.h:41:0,
                 from /home/helektron/Desktop/rtl8822bu/include/drv_types.h:32,
                 from /home/helektron/Desktop/rtl8822bu/core/rtw_cmd.c:22:
/home/helektron/Desktop/rtl8822bu/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/helektron/Desktop/rtl8822bu/include/osdep_service_linux.h:262:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/helektron/Desktop/rtl8822bu/include/osdep_service_linux.h:263:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/helektron/Desktop/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/helektron/Desktop/rtl8822bu/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/home/helektron/Desktop/rtl8822bu' failed
make[1]: *** [_module_/home/helektron/Desktop/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-22-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2



```

---

### Post by jeremy31 on 2018-06-07
Try [https://github.com/MeissnerEffect/rtl8822bu.git](https://github.com/MeissnerEffect/rtl8822bu.git) after doing a ```
rm -r rtl8822bu
``` or delete the rtl8822bu directory from /home

---

### Post by dld521 on 2018-06-29
All hail Jeremy.  His fix works perfectly; I am using Kubuntu 16.04 with kernel 4.13.:p

---

