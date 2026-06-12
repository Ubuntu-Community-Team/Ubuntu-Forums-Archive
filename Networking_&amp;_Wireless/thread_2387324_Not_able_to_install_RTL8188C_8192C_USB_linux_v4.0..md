---
title: "Not able to install RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911 driver on Ubuntu"
date: 2018-03-17
forum: Networking &amp; Wireless
---

### Post by amishra2804 on 2018-03-17
Not able to install RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911 driver on Ubuntu  16.04 for my wifi usb adapter. 
```

amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ ./install.sh
bash: ./install.sh: Permission denied
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ chmod + X install.sh 
chmod: cannot access 'X': No such file or directory
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ sudo ./install.h
[sudo] password for amritansh: 
Sorry, try again.
[sudo] password for amritansh: 
sudo: ./install.h: command not found
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ ls
android_ref_codes_JB_4.1             install.sh
android_ref_codes_JB_4.2             readme.txt
android_reference_codes              ReleaseNotes.pdf
android_reference_codes_ICS_nl80211  WiFi_Direct_User_Interface
document                             wireless_tools
driver                               wpa_supplicant_hostapd
hardware_wps_pbc
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ chmod +x install.sh
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ sudo ./install.sh 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911.tar.gz
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/runwpa
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/wlan0dhcp
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_com.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wifi.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/HalPwrSeqCmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_android.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/nic_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ethernet.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_conf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/wireless.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_version.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/h2clbk.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_tdls.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ap.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/sta_info.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/autoconf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_security.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_io.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/circ_buf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/basic_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ip.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/if_ether.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_sdio.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Makefile
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Kconfig
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/HalPwrSeqCmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/clean
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-37-generic/build M=/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-37-generic'
  CC [M]  /home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
In file included from /home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.c:23:0:
/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h: In function ‘thread_enter’:
/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h:1482:2: error: implicit declaration of function ‘allow_signal’ [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^
/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h:1495:6: error: implicit declaration of function ‘signal_pending’ [-Werror=implicit-function-declaration]
  if (signal_pending (current)) 
      ^
/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h:1497:3: error: implicit declaration of function ‘flush_signals’ [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:308: recipe for target '/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o' failed
make[2]: *** [/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o] Error 1
Makefile:1550: recipe for target '_module_/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911' failed
make[1]: *** [_module_/home/amritansh/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-37-generic'
Makefile:584: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911$ 
```

I am a new linux user and am not sure how do i go about this. I tried a few solutions but did not work. Any help would be appreciated. Thank you

---

### Post by jeremy31 on 2018-03-17
See the wireless script link in my signature and post results

---

### Post by amishra2804 on 2018-03-17
Thank you for your quick response Jeremy. The result from the wireless script :
[http://paste.ubuntu.com/p/KKZ68yksbT/](http://paste.ubuntu.com/p/KKZ68yksbT/)

---

### Post by jeremy31 on 2018-03-17
Why are you trying to install that driver?  I don't see any devices that use those chipsets connected and it seems you have a working internal wifi.  See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) for some ways to improve the performance of the internal device

---

### Post by amishra2804 on 2018-03-17
I am connected to the 2.4 Ghz channel presently. But wanted to use the usb wifi adapter to connect to the 5 Ghz channel.

---

### Post by jeremy31 on 2018-03-17
For the USB device do
```
sudo apt-get install git build-essential dkms
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2
```
Reboot

---

### Post by amishra2804 on 2018-03-17
I get the following error on the third command. Tried going step by step based on the instructions given on the git page but still the error persists :

amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads$ git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
Cloning into 'rtl8812au'...
remote: Counting objects: 607, done.
remote: Total 607 (delta 0), reused 0 (delta 0), pack-reused 607
Receiving objects: 100% (607/607), 1.80 MiB | 3.06 MiB/s, done.
Resolving deltas: 100% (244/244), done.
Checking connectivity... done.
amritansh@amritansh-HP-Pavilion-dv6-Notebook-PC:~/Downloads$ sudo dkms add -m rtl8812au -v 4.2.2
Error! Could not find module source directory.
Directory: /usr/src/rtl8812au-4.2.2 does not exist.

---

### Post by jeremy31 on 2018-03-17
Sorry
```
sudo dkms add ./rtl8812au
sudo dkms install -m rtl8812au -v 4.2.2
```
Then reboot

---

### Post by amishra2804 on 2018-03-17
Hi Jeremy31,

My issue is resolved. Thank you for your time and help.

Just adding in the steps given by you with slight modification that worked for me for future reference :

Went to my download directory in the terminal to keep things simple :
```

sudo git clone https://github.com/gnab/rtl8812au.git
```

Once the drivers are downloaded cd rtl8812au 
ran the following command :
```
$ make
$ sudo insmod 8812au.ko
```
//In case the last command does not work try ```
$sudo rmmod 881au 
```
No output for the last command. You can now try the previous command that was :
```
$ sudo insmod 8812au.ko
```

Ran the following command from the Downloads directory and not rtl8812au
```
$ sudo cp 8812au.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
$ sudo depmod

```

Followed by :
```
$ sudo apt-get install build-essential dkms
``` 

And:```

$ sudo dkms add -m 8812au -v 4.2.2
$ sudo dkms build -m 8812au -v 4.2.2
$ sudo dkms install -m 8812au -v 4.2.2
```

Restarted the system and the dongle light started flickering :)

---

### Post by jeremy31 on 2018-03-17
I think the following should have worked as I didn't check all the edits I made
```
sudo apt-get install git build-essential dkms
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add  ./rtl8812au
sudo dkms install -m rtl8812au -v 4.2.2
```

And since you were in ~/Downloads rather than /home post [https://ubuntuforums.org/showthread.php?t=2387324&p=13749248#post13749248](https://ubuntuforums.org/showthread.php?t=2387324&p=13749248#post13749248) didn't help as ```
sudo dkms add -m 8812au -v 4.2.2
``` only works if there is something at /usr/src/8812au-4.2.2

---

