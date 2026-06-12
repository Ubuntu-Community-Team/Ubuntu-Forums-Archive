---
title: "Unable to Connect Wifi Adapter USB2.0 802.11N to lubuntu 16.04"
date: 2019-04-27
forum: Networking &amp; Wireless
---

### Post by sameercshah on 2019-04-27
i have installation cd and have below error

i am new to ubuntu and not coder or software langaauge guy,,,have read on net and run below command, kindly guid step by step

```
sameer@sameer-desktop:~$ cd /media/sameer/6420-75E5/Driver/linux/RTL8188EUS_linux_v4.1.4_6773.20130222
sameer@sameer-desktop:/media/sameer/6420-75E5/Driver/linux/RTL8188EUS_linux_v4.1.4_6773.20130222$ chmod +x install.sh
sameer@sameer-desktop:/media/sameer/6420-75E5/Driver/linux/RTL8188EUS_linux_v4.1.4_6773.20130222$ bash install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188EUS_linux_v4.1.4_6773.20130222.tar.gz
rtl8188EUS_linux_v4.1.4_6773.20130222/
rtl8188EUS_linux_v4.1.4_6773.20130222/runwpa
rtl8188EUS_linux_v4.1.4_6773.20130222/core/
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_xmit.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_ioctl_query.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_bt_mp.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/efuse/
rtl8188EUS_linux_v4.1.4_6773.20130222/core/efuse/rtw_efuse.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_recv.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_br_ext.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_wapi.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_eeprom.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_debug.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_tdls.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_p2p.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_ieee80211.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_security.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_cmd.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_mlme.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_mp.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_wapi_sms4.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_sreset.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_sta_mgt.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_rf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_pwrctrl.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_wlan_util.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_mlme_ext.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_io.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_ap.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_led.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_ioctl_rtl.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_mp_ioctl.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_ioctl_set.c
rtl8188EUS_linux_v4.1.4_6773.20130222/core/rtw_iol.c
rtl8188EUS_linux_v4.1.4_6773.20130222/wlan0dhcp
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/osdep_service.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/ioctl_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/recv_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/os_intfs.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/pci_ops_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/custom_gpio_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/usb_intf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/mlme_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/gspi_intf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/pci_intf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/sdio_intf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/rtw_android.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/xmit_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/gspi_ops_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/usb_ops_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/sdio_ops_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/os_dep/linux/ioctl_cfg80211.c
rtl8188EUS_linux_v4.1.4_6773.20130222/include/
rtl8188EUS_linux_v4.1.4_6773.20130222/include/hal_com.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/wlan_bssdef.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/cmd_osdep.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_recv.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_mlme_ext.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/wifi.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_led.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_recv.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/custom_gpio.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/HalPwrSeqCmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_dm.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_dm.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8192CPhyReg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/gspi_ops_linux.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_pg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8192DPhyCfg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_dm.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_rf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_android.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types_gspi.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_recv.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_recv.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/nic_spec.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/usb_osintf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_dm.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_recv.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_xmit.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_event.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8188EPhyReg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_qos.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_pwrctrl.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_xmit.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_spec.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/gspi_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_ce_service.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_ops.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_sreset.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_rf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/ieee80211.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/recv_osdep.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types_linux.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_efuse.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/gspi_ops.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_ops_ce.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/usb_ops.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_xmit.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ht.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/HalVerDef.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/ioctl_cfg80211.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/ethernet.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8188EPhyCfg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/mp_custom_oid.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ioctl_rtl.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_ops_linux.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8723APhyCfg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_spec.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_mlme.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_sreset.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/ieee80211_ext.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types_ce.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8192CPhyCfg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8723APhyReg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_cmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_rf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_led.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/swab.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/swabb.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/big_endian.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/little_endian.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/byteorder/generic.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_mp_ioctl.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_ops_xp.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/usb_ops_linux.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_xmit.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_osintf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8723PwrSeq.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_sreset.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_p2p.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/pci_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_conf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/usb_vendor_req.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/linux/
rtl8188EUS_linux_v4.1.4_6773.20130222/include/linux/wireless.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_service.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_led.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/gspi_osintf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ioctl_query.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_eeprom.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types_xp.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_cmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_byteorder.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_xmit.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_version.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_spec.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_cmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ioctl_set.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/h2clbk.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/pci_osintf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_bt_mp.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_cmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192d_rf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/pci_ops.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_tdls.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_cmd.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_event.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/mlme_osdep.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_debug.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ap.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/osdep_intf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_wapi.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/hal_intf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sta_info.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8188e_spec.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_iol.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_mp_phy_regdef.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_rf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8188EPwrSeq.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/usb_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/autoconf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_security.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/sdio_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_io.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/Hal8192DPhyReg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_br_ext.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/circ_buf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/basic_types.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_hal.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/ip.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_led.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/if_ether.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/xmit_osdep.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8192c_sreset.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_bt-coexist.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_mp.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtw_ioctl.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/drv_types_sdio.h
rtl8188EUS_linux_v4.1.4_6773.20130222/include/rtl8723a_led.h
rtl8188EUS_linux_v4.1.4_6773.20130222/ifcfg-wlan0
rtl8188EUS_linux_v4.1.4_6773.20130222/Makefile
rtl8188EUS_linux_v4.1.4_6773.20130222/Kconfig
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_types.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/HalPhyRf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/HalPhyRf.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_RegDefine11N.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_precomp.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/Hal8188EReg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_BB.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/odm_RTL8188E.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/Hal8188ERateAdaptive.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_RF.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_RF.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_FW.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalPhyRf_8188e.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/odm_RegConfig8188E.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/odm_RTL8188E.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_MAC.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/Hal8188EFWImg_CE.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_MAC.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_BB.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/Hal8188EFWImg_CE.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalHWImg8188E_FW.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/odm_RegConfig8188E.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/Hal8188ERateAdaptive.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/rtl8188e/HalPhyRf_8188e.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_HWConfig.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_debug.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_interface.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_interface.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_HWConfig.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_reg.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_RegDefine11AC.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/OUTSRC/odm_debug.h
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/hal_intf.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_sreset.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_rxdesc.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_cmd.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_rf6052.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/Hal8188EPwrSeq.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_mp.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_phycfg.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_dm.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/usb_halinit.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/rtl8188eu_led.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/rtl8188eu_recv.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/rtl8188eu_xmit.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/usb/usb_ops_linux.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_hal_init.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/rtl8188e/rtl8188e_xmit.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/hal_com.c
rtl8188EUS_linux_v4.1.4_6773.20130222/hal/HalPwrSeqCmd.c
rtl8188EUS_linux_v4.1.4_6773.20130222/clean
rtl8188EUS_linux_v4.1.4_6773.20130222
Authentication requested [root] for make clean:
Password: 

sameer@sameer-desktop:~$ lsusb
Bus 001 Device 003: ID 1ecb:02e2  
Bus 001 Device 006: ID 058f:9380 Alcor Micro Corp. Flash Drive
Bus 001 Device 002: ID 1908:2310 GEMBIRD 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2188:0ae1  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by mörgæs on 2019-04-27
Hi, welcome to the fora.

Lubuntu 16.04 is out of support so I recommend that you begin with a fresh install (no upgrades) of a recent Lubuntu.

According to [https://github.com/quickreflex/rtl8188eus](https://github.com/quickreflex/rtl8188eus) there is still development work going on for Linux kernel 5 so I suggest Lubuntu 19.04 which is built upon a kernel in the 5-series. Use a wired connection when installing.

Please post back if the wifi adapter still gives trouble here.

---

### Post by sameercshah on 2019-04-27
Thanks for your reply. 
still any way out on 16.04...i am use to 16.04 & my system is desktop with 2 GB ram dualcore processor.Pentium R.

---

### Post by mörgæs on 2019-04-27
As mentioned above 16.04 is out of support meaning that security bugs are not fixed. It should not be used even if the wifi adapter worked.

---

### Post by him610 on 2019-04-28
Hello,

FWIW, I have a similar wireless USB that uses same driver. Could not get it to work consistently using LTS 18.04+. Installed 19.04 a couple of months ago. Now it connects every time.
```

inxi -N
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           Device-2: TP-Link TL WN823N [COLOR="#FF0000"]RTL8192EU[/COLOR] type: USB driver: rtl8xxxu 
....
lsusb |grep RTL
Bus 001 Device 002: ID 2357:0109 TP-Link TL WN823N [COLOR="#FF0000"]RTL8192EU[/COLOR]

```
No special driver downloads were needed. The driver came from regular *buntu 19.04 repository.

---

### Post by praseodym on 2019-04-28
Try this one instead

```
sudo apt-get install git linux-headers-generic build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/blacklist-rtl8xxxu.conf
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8192eu.conf
```
Reboot.

Source
[https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)

---

### Post by sameercshah on 2019-04-29
Thanks Brothers, I have Upgraded to 19.04 and in terminal complete  commands as given by Praseodym comment 6 , i have following output on  terminal....Still i cannot see wifi network...something i am  missing,,,please guide.
sameer@sameer-pc:~$ lsusb
Bus 001 Device 004: ID 0bda:f179 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1ecb:02e2  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2188:0ae1  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sameer@sameer-pc:~$ ls -rv
rtl8192eu-linux-driver  Templates  Pictures  Downloads  Desktop
Videos                  Public     Music     Documents

rtl 8188eus driver require

---

### Post by jeremy31 on 2019-04-29
For that wifi see [https://github.com/kelebek333/rtl8188fu](https://github.com/kelebek333/rtl8188fu)

---

### Post by sameercshah on 2019-04-29
i have upgraded to 19.04.
downloaded the .zip file github as link provided by you.

what next steps i have to follow.
compling & builiding  files i have no idea.

---

### Post by jeremy31 on 2019-04-29
The steps to follow are on that github page [https://github.com/kelebek333/rtl8188fu/blob/master/README.md](https://github.com/kelebek333/rtl8188fu/blob/master/README.md)

---

### Post by sameercshah on 2019-04-29
Thanks , My problem got solved by jeremy..last thread reply.

---

### Post by sameercshah on 2019-04-29
jeremy31, thanks a lot.
with your help, my problem get solved.

---

### Post by sameercshah on 2019-05-05
jeremy, your command works for both 16.04 & 19.04

---

### Post by mörgæs on 2019-05-07
Good, please mark the thread 'solved'.

---

