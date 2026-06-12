---
title: "Realtek 8814AU (in Edicmax EW-7833uac) DROPS CONNECTION, Ubuntu 16.04"
date: 2017-03-14
forum: Networking &amp; Wireless
---

### Post by lb96179 on 2017-03-14
my realtek RTL8814AU chip (in an Edimax EW7833UAC wifi usb 3.0 dongle), on Ubuntu 16.04, drops the wifi conntion to the router.  
Initial connection seems good for a few minutes.
I've posted the script to pastebin as requested (after updating Ubuntu as suggested) [http://paste.ubuntu.com/24175274/](http://paste.ubuntu.com/24175274/)
I installed the adapter using the vendor supplied driver ([http://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1750_dual-band/ew-7833uac](http://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1750_dual-band/ew-7833uac)) - it's supposed to run on this kernel out of the box.
Any help much appreciated.
(Sorry about the caps in the heading - only saw that after I hit post and I can't see how to change the heading.)

---

### Post by jeremy31 on 2017-03-14
Open a terminal when you are connected and enter ```
watch -n 1 cat /proc/net/wireless
```
Does the value under link change a lot?  It will change value every second but does it go from close to 100 down to under 50?
Also post results for ```
grep [[:alnum:]] /sys/module/8814au/parameters/*
```

---

### Post by lb96179 on 2017-03-14
Thanks.
> **jeremy31 said:**
> Open a terminal when you are connected and enter ```
watch -n 1 cat /proc/net/wireless
```
Does the value under link change a lot?  It will change value every second but does it go from close to 100 down to under 50?

yes
> Also post results for ```
grep [[:alnum:]] /sys/module/8814au/parameters/*
```
```

~$ grep [[:alnum:]] /sys/module/8814au/parameters/*
/sys/module/8814au/parameters/if2name:wlan%d
/sys/module/8814au/parameters/ifname:wlan%d
/sys/module/8814au/parameters/rtw_80211d:0
/sys/module/8814au/parameters/rtw_adaptivity_dc_backoff:2
/sys/module/8814au/parameters/rtw_adaptivity_dml:0
/sys/module/8814au/parameters/rtw_adaptivity_en:0
/sys/module/8814au/parameters/rtw_adaptivity_mode:0
/sys/module/8814au/parameters/rtw_adaptivity_th_edcca_hl_diff:0
/sys/module/8814au/parameters/rtw_adaptivity_th_l2h_ini:0
/sys/module/8814au/parameters/rtw_ampdu_amsdu:0
/sys/module/8814au/parameters/rtw_ampdu_enable:1
/sys/module/8814au/parameters/rtw_amplifier_type_2g:0
/sys/module/8814au/parameters/rtw_amplifier_type_5g:0
/sys/module/8814au/parameters/rtw_antdiv_cfg:2
/sys/module/8814au/parameters/rtw_antdiv_type:0
/sys/module/8814au/parameters/rtw_beamform_cap:2
/sys/module/8814au/parameters/rtw_busy_thresh:40
/sys/module/8814au/parameters/rtw_bw_mode:33
/sys/module/8814au/parameters/rtw_channel:1
/sys/module/8814au/parameters/rtw_channel_plan:97
/sys/module/8814au/parameters/rtw_chip_version:0
/sys/module/8814au/parameters/rtw_decrypt_phy_file:0
/sys/module/8814au/parameters/rtw_enusbss:0
/sys/module/8814au/parameters/rtw_FileMaskEfuse:0
/sys/module/8814au/parameters/rtw_GLNA_type:0
/sys/module/8814au/parameters/rtw_hiq_filter:1
/sys/module/8814au/parameters/rtw_ht_enable:1
/sys/module/8814au/parameters/rtw_hwpdn_mode:2
/sys/module/8814au/parameters/rtw_hwpwrp_detect:0
/sys/module/8814au/parameters/rtw_hw_wps_pbc:1
/sys/module/8814au/parameters/rtw_initmac:(null)
/sys/module/8814au/parameters/rtw_ips_mode:1
/sys/module/8814au/parameters/rtw_kfree:0
/sys/module/8814au/parameters/rtw_lbkmode:0
/sys/module/8814au/parameters/rtw_load_phy_file:68
/sys/module/8814au/parameters/rtw_low_power:0
/sys/module/8814au/parameters/rtw_lowrate_two_xmit:1
/sys/module/8814au/parameters/rtw_max_roaming_times:2
/sys/module/8814au/parameters/rtw_mc2u_disable:0
/sys/module/8814au/parameters/rtw_mp_mode:0
/sys/module/8814au/parameters/rtw_network_mode:0
/sys/module/8814au/parameters/rtw_notch_filter:0
/sys/module/8814au/parameters/rtw_OffEfuseMask:0
/sys/module/8814au/parameters/rtw_pll_ref_clk_sel:15
/sys/module/8814au/parameters/rtw_power_mgnt:2
/sys/module/8814au/parameters/rtw_qos_opt_enable:0
/sys/module/8814au/parameters/rtw_rf_config:15
/sys/module/8814au/parameters/rtw_RFE_type:64
/sys/module/8814au/parameters/rtw_rfintfs:2
/sys/module/8814au/parameters/rtw_rfkfree_enable:2
/sys/module/8814au/parameters/rtw_rxgain_offset_2g:0
/sys/module/8814au/parameters/rtw_rxgain_offset_5gh:0
/sys/module/8814au/parameters/rtw_rxgain_offset_5gl:0
/sys/module/8814au/parameters/rtw_rxgain_offset_5gm:0
/sys/module/8814au/parameters/rtw_rx_stbc:3
/sys/module/8814au/parameters/rtw_smart_ps:2
/sys/module/8814au/parameters/rtw_special_rf_path:0
/sys/module/8814au/parameters/rtw_switch_usb_mode:0
/sys/module/8814au/parameters/rtw_TxBBSwing_2G:255
/sys/module/8814au/parameters/rtw_TxBBSwing_5G:255
/sys/module/8814au/parameters/rtw_tx_pwr_by_rate:0
/sys/module/8814au/parameters/rtw_tx_pwr_lmt_enable:0
/sys/module/8814au/parameters/rtw_usb_rxagg_mode:2
/sys/module/8814au/parameters/rtw_vcs_type:1
/sys/module/8814au/parameters/rtw_vht_enable:1
/sys/module/8814au/parameters/rtw_vrtl_carrier_sense:2
/sys/module/8814au/parameters/rtw_wifi_spec:0
/sys/module/8814au/parameters/rtw_wmm_enable:1

```

---

### Post by jeremy31 on 2017-03-14
It is the variation that is causing the disconnects and I haven't figured out how to fix it.  I actually blamed my cell phone as I can use tethering on 5Ghz but if I remember 2.4 Ghz worked a lot better.
Since you got the driver from the manufacturer send them an email about the 5Ghz issue and they should be able to fix it.  There has to be an issue with their coding involving the RX amplifier

---

### Post by lb96179 on 2017-03-14
Thanks Jeremy.  If I get helpful information in a response I'll post it here.

---

### Post by lb96179 on 2017-04-01
I updated the firmware on router this morning and for the last few hours I have had a trouble free wifi connection with the Edimax EW-7833uac.  So I'm marking the thread as solved.

---

