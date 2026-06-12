---
title: "Installing Wsky Wireless driver Ubuntu 16.04"
date: 2017-12-26
forum: Networking &amp; Wireless
---

### Post by normster2 on 2017-12-26
Hi, 

I'm having trouble installing the driver for my wifi adapter, specifically the one found at [this link]("https://www.amazon.com/gp/product/B071F5LWS1/ref=oh_aui_detailpage_o00_s01?ie=UTF8&psc=1")

I tried installing the drivers the manufacturer linked to on the [product page]("http://www.szedup.com/support/driver-download/ep-db1607-driver/") but upon running install.sh I get several compilation errors:

```

##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_query.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi_sms4.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_rtl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/rtw_efuse.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sta_mgt.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_io.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_rf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_vht.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_set.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_iol.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_odm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ap.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_pwrctrl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_tdls.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_bt_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_eeprom.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_beamforming.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wlan_util.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_p2p.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp_ioctl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ieee80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_br_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mem.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_security.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_br_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_pci.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mp_custom_oid.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_vht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_iol.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swabb.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/little_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/big_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swab.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/generic.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_io.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8821APwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_conf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ip.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wifi_regd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_vendor_req.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_efuse.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_android.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/xmit_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/autoconf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_query.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wapi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wifi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_version.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/if_ether.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mlme_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_beamforming.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_data.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/circ_buf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalPwrSeqCmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_byteorder.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/nic_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wlan_bssdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_p2p.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/custom_gpio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ethernet.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_rtl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/wireless.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_qos.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_phycfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ap.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/recv_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_pwrctrl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_odm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_h2c.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mem.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_tdls.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_set.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/basic_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_bt_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_eeprom.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/h2clbk.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_phy_regdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/cmd_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_security.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_bsd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalVerDef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sta_info.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/runwpa
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/clean
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Kconfig
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/ifcfg-wlan0
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Makefile
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/wlan0dhcp
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/hal_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/efuse_mask.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11N.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_pre_define.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11AC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/hal_usb_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_hal_init.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8821APwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rf6052.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8812PwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_halinit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtcOutSrc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/HalPwrSeqCmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_phy.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/wifi_regd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/custom_gpio_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/xmit_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/mlme_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/os_intfs.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/recv_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_android.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/osdep_service.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_WMT_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_arm_act_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNnI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_sprd_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_RTK_DMP_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
Authentication requested [root] for make clean:
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
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
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-42-generic/build M=/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-42-generic'
  CC [M]  /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o
In file included from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:95:0,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h:412:13: error: ‘file_path’ redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^
In file included from ./include/linux/seq_file.h:10:0,
                 from ./include/linux/pinctrl/consumer.h:17,
                 from ./include/linux/pinctrl/devinfo.h:21,
                 from ./include/linux/device.h:24,
                 from ./include/linux/dmaengine.h:20,
                 from ./include/linux/netdevice.h:38,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:35,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
./include/linux/fs.h:2680:14: note: previous declaration of ‘file_path’ was here
 extern char *file_path(struct file *, char *, int);
              ^
In file included from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:65:0,
                 from /home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c: In function ‘btinfo_evt_dump’:
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3293:2: note: in expansion of macro ‘DBG_871X_SEL_NL’
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3296:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3308:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3311:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3314:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^
scripts/Makefile.build:294: recipe for target '/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed
make[2]: *** [/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
Makefile:1524: recipe for target '_module_/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/home/norman/Downloads/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-42-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

I've tried following the instructions found in this [previous forum post]("https://ubuntuforums.org/showthread.php?t=2378892"), but to no success (that user was trying to install the AC 1200 version of the adapter on 17.10 whereas I am installing the AC 600 version of the adapter on 16.04). Thanks in advance!

---

### Post by chili555 on 2017-12-26
Let's confirm your exact device. With the device inserted, please run and post:```
lsusb
```

---

### Post by normster2 on 2017-12-26
I ran lsusb and got the following output:

```

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c338 Logitech, Inc. 
Bus 003 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Without the device plugged in we get:

```

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c338 Logitech, Inc. 
Bus 003 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

i.e. the device is Bus 005 Device 002: ID 0bda:a811 Realtek Semiconductor Corp.

---

### Post by uRock on 2017-12-26
If it is an internal card, then please run,
```
lspci
```
We're looking for something like,```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
```

---

### Post by normster2 on 2017-12-26
I ran lspci:

```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
06:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

```

---

### Post by Hadaka on 2017-12-26
Hi, your post # 3 shows...
 lsusb..
```
Bus 005 Device 002: ID [COLOR=#ff0000]0bda[/COLOR]:[COLOR=#ff0000]a811[/COLOR] Realtek Semiconductor Corp.
```
modinfo 8812au shows..
```
alias:  usb:v[COLOR=#ff0000]0BDA[/COLOR]p[COLOR=#ff0000]A811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```
So rtl8812au is the correct driver..
From a WORKING WIRED connection...Please follow the instructions in post # 5 here..
[https://ubuntuforums.org/showthread.php?t=2375603&p=13705226#post13705226](https://ubuntuforums.org/showthread.php?t=2375603&p=13705226#post13705226)
Thanks.

---

### Post by normster2 on 2017-12-27
Just followed the instructions and it worked wonderfully! Thank you everyone for your help

---

### Post by Hadaka on 2017-12-27
Hi, Glad Dr Chili555's guide resolved the wifi problem.. Enjoy !
 and Thank You for marking your thread Solved.

---

