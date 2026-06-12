---
title: "TP-link T9UH wifi"
date: 2018-05-07
forum: Networking &amp; Wireless
---

### Post by simon114 on 2018-05-07
Good evening, I have downloaded drivers for t9UH from the official site, I could really do with some help installing them. I have a brand new installation of 18.04.
Chipset  is [CENTER][FONT=sans-serif]RTL8814AU
Thank you[/FONT][/CENTER]

---

### Post by jeremy31 on 2018-05-07
simon114, downloading linux source from most manufacturers is a waste of time.  

See my post at [https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426](https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426)
If that doesn't work after a reboot, post results for ```
lsusb
```

---

### Post by simon114 on 2018-05-07
> **jeremy31 said:**
> simon114, downloading linux source from most manufacturers is a waste of time.  

See my post at [https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426](https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426)
If that doesn't work after a reboot, post results for ```
lsusb
```

I have a small problem In that I have zero Internet access with the computer. I can download files with my phone, and transfer them to pc

---

### Post by jeremy31 on 2018-05-07
Can you use USB tethering?

---

### Post by wildmanne39 on 2018-05-07
I removed your duplicate post from public view, please do not post the same thing more then once.

Thanks

---

### Post by simon114 on 2018-05-07
Thanks for removing duplicate post...all a bit fiddly on the phone.. I can confirm that as per the instructions given internet adapter has now been installed. And a very good tip for the USB tethering....havnt done that in years...all up and running. Many many thanks.

---

### Post by jeremy31 on 2018-05-07
Great, please use the thread tools menu near the top right of the page to mark as solved.  I use a different USB wifi that uses the rtl8814au

---

### Post by simon114 on 2018-05-09
Good Morning,
An Update, as of this morning tp-link T9UH adapter has stopped working again,
I'm not sure if its anything I've done, so id like to know the procedure to remove the cloned git and local folders, and start again from scratch using the already mentioned instructions.

Many Thanks

here is the logfile  [https://pastebin.com/C3UNmds2](https://pastebin.com/C3UNmds2)

---

### Post by jeremy31 on 2018-05-09
Can you post results for ```
modinfo 8814au
```

---

### Post by simon114 on 2018-05-09
> **jeremy31 said:**
> Can you post results for ```
modinfo 8814au
```

here it is

```


~$ modinfo 8814au
filename:       /lib/modules/4.15.0-20-generic/updates/dkms/8814au.ko
version:        v4.3.21_17997.20160531
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     86312A75A3E105F2CFA57F5
alias:          usb:v0846p9054d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p809Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p809Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA834d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA833d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep400Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v056Ep400Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1853d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1852d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1817d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p331Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8813d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8814au
vermagic:       4.15.0-20-generic SMP mod_unload 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_rfkfree_enable:int
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
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
parm:           rtw_beamform_cap:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:TH_L2H_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:TH_EDCCA_HL_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_kfree:default kfree config value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)


```

any good? thanks

---

### Post by simon114 on 2018-05-09
So it turns out that the missus was having a cleanup and semi unplugged the adapter wire with the vacuum cleaner. I am so sorry for the inconvenience.

**Rule of thumb** Check the simple things first like, is it plugged in..

Thank you and sorry.

---

