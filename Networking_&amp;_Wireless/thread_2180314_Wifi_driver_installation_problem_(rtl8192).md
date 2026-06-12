---
title: "Wifi driver installation problem (rtl8192)"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by Filippo_Ceffa on 2013-10-12
I'm using lubuntu 32 bit and i want to install those drivers cause the default one are working very bad.
I downloaded them from the realtek site, and exctract them. I have to run the install.sh file, but if i do, i get this:

```

##################################################Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
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
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-31-generic/build M=/home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  CC [M]  /home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
In file included from /home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c:23:0:
/home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h:575:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/ceffa/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
ceffa@pc:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 



```


As you can see i get this two errors. I don't know what to do, i tried a lot of things reading around internet, but nothing seems to work. ideas?

---

### Post by varunendra on 2013-10-13
Welcome to the forums Filippo_Ceffa !

Let's first make sure that driver is the correct one for your adapter. Please open a terminal (Ctrl-Alt-T) and post back the output of (you may copy-paste) -
```
lsusb
```
..assuming it is indeed a USB adapter.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Filippo_Ceffa on 2013-10-14
Sorry, maybe i've not been clear, it's an internal wireless adapter, connected to my motherboard in the PCI express port.

This is the result of that command:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 001 Device 004: ID 8564:1000  
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 004: ID 1a7c:0068 Evoluent VerticalMouse 3



```


ps: another couple of things that maybe are relevant: 

1) i've the cd driver but if i try to 'make' the make file i receive an error, even if those drivers are certainly correct
2) my lubuntu is permanently installed on a usb

---

### Post by varunendra on 2013-10-14
Ah, you were using a driver that was meant for USB wifi adapters, so I thought you were doing that intentionally for a USB one.

Although sometimes even an internally connected card can be on a USB bus, but from your output it is clear that yours is not. So now we know the driver you originally were trying can't be a correct driver for the card. Now let us see which one you indeed have and if a driver is already loaded for it. Please post back the output of -
```
lspci -nnk | grep -iA2 net
```

---

### Post by Filippo_Ceffa on 2013-10-14
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)	Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
	Kernel driver in use: rtl8192ce
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASRock Incorporation Device [1849:1083]
	Kernel driver in use: atl1c



```

---

### Post by QIII on 2013-10-14
*Moved to **Networking & Wireless***

---

### Post by varunendra on 2013-10-14
> **Filippo_Ceffa said:**
> ```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
	Kernel driver in use: **[COLOR="#0000CD"]rtl8192ce[/COLOR]**

```

Before resorting to the proprietary driver, please try these first -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```

If that doesn't improve connectivity, then -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce fwlps=0
```

If that doesn't help either, then -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce ips=0
```

If still no improvement, then a blind shot with all three options -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```
All these changes are temporary and will be lost at next boot, so try them without rebooting. If any of these help, post back and we'll make it permanent. If none of these makes any positive difference, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Filippo_Ceffa on 2013-10-14
wait....after i try these line of code, i have to try and reinstall the drivers? to see if i get the errors again?

---

### Post by Filippo_Ceffa on 2013-10-14
result of wireless info, but i don't know if it is correct because now i'm wired connected...should i make it with the wireless connection or it is correct either way?


```




*************** info trace ***************


***** uname -a *****


Linux pc 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 002 Device 004: ID 03f0:7404 Hewlett-Packard Printing Support
Bus 002 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 006: ID 8564:1000  


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****


rtl8192ce              52841  0 
rtlwifi                69015  1 rtl8192ce
rtl8192c_common        47075  1 rtl8192ce
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192ce
cfg80211              436243  2 mac80211,rtlwifi
ndiswrapper           192638  0 


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B41EC2D43683C181DF50FB6
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E6FCDEDFF185E90DD643BE4
depends:        mac80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-31-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.58
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     2F19DFC5820B1214E84CFEB
depends:        
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   24.058845] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)


****************** done ******************
```

---

### Post by varunendra on 2013-10-14
> **Filippo_Ceffa said:**
> wait....after i try these line of code, i have to try and reinstall the drivers? to see if i get the errors again?
No, if any of those suggestions could make it better, then job is 'almost' done, we just need to make that permanent. If all those failed, then installing another driver *may* be an option.

> **Filippo_Ceffa said:**
> result of wireless info, but i don't know if it is correct because now i'm wired connected...should i make it with the wireless connection or it is correct either way?
Usually it is okay either way, but it is best to disconnect the cable connection, try connecting via wifi, let it success or fail as usual, then run the script.

It seems you ran it 'After' disabling the wireless? Because it doesn't show up in "lspci" section while it just did in post #5. Perhaps your BIOS is set to disable it when the cable connection is in use? Please check the BIOS settings to see if there is such an option there. Currently, there is nothing about the wifi in the report since it has totally disappeared.

However this is interesting -
```

rtl8192ce              52841  0 
rtlwifi                69015  1 rtl8192ce
rtl8192c_common        47075  1 rtl8192ce
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192ce
cfg80211              436243  2 mac80211,rtlwifi
**[COLOR="#FF0000"]ndiswrapper[/COLOR]**           192638  0 
....
<snip>
....
***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
```
Both rtl8192ce and ndiswrapper are loaded which is probably a result of your desperate attempts with the wifi.

But even more interesting is the udev rules file. Is this a clean install on this system or a migrated one (originally installed to another system, then moved/cloned to this one)?

**EDIT:**
Forgot the suggestion part. Please unplug the cable connection, reboot > try to connect via wifi > run the script again and post back the fresh report.

---

### Post by Filippo_Ceffa on 2013-10-14
i installed diswrapper, the other thing i don't know what that is...

About your suggestion: the wifi works, it works somethimes, and somethimes no, it's very unstable...thats the problem, how can i try those scripts and know if it's ok? i need a long time laps to  verify it

---

### Post by varunendra on 2013-10-14
> **Filippo_Ceffa said:**
> i installed diswrapper, the other thing i don't know what that is...
The 'other' thing is the driver that is actually needed, and ndiswrapper is what is adding to the problem if not creating it. So let us first get rid of ndiswrapper.

In a terminal, please do -
```
sudo modprobe -rv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper
```

> how can i try those scripts and know if it's ok? i need a long time laps to  verify it
If this long laps is going to be just one session (from one booting to power off), just use one pair (sudo modprobe -rv.... & sudo modprobe -v...) at a time. If connection drops, it failed and you can try the next pair in the same session. If you want to test it across multiple sessions, you can either use the same pair of commands to see if it always works, or create a conf file to make it automatically load on each boot so that you don't have to run those commands.

For example, to make the "swenc=1" option permanent, we can create a conf file "rtl8192ce.conf" like this -
```
echo "options rtl8192ce swenc=1" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Then reboot and next time the rtl8192ce driver will automatically load with this parameter.

I suggest you try this and THEN run the wireless_script and post back its fresh report, so that we can verify you did it correctly.

---

### Post by alexaiv on 2014-02-13
Thanks very much! I followed your instructions and after reading so many threads about how to make my wifi stable, it finally worked! The ips=0 command did the trick for me. Thanks again!

---

### Post by varunendra on 2014-02-14
> **alexaiv said:**
> Thanks very much! I followed your instructions and after reading so many threads about how to make my wifi stable, it finally worked! The ips=0 command did the trick for me. Thanks again!

Welcome to the forums alexaiv, and thanks for the feedback! :)

The recent versions of this driver are frequently being reported to be problematic with connectivity, so if this made your connection stable, it is a valuable feedback for us. But of course if the problem returns, feel free to start a new thread and let us know the current situation with reference to this (and whatever else) workaround(s) you tried.

Hope you'd enjoy Ubuntu and our forums here. :)

See you around !

---

### Post by evan8 on 2014-02-16
I know this thread is old. But I been having speed issues with same rtl8188ce

I think "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0" seems to work. But what would be the perm way to do this?

I had speed working fine but I installed and formatted everything. Usually when my speed goes down it always downloads at 300kb max. I can download up to 6MBPS though..I haven't updated any firmware etc. Just need a way to fix it. thanks[/FONT][/COLOR]

---

### Post by varunendra on 2014-02-16
> **evan8 said:**
> I think "sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0" seems to work. But what would be the perm way to do this?

I think only one or at most two of them should be enough, like alexaiv mentioned in post #13 above that only **ips=0** works for him. But whatever works..

To make it permanent, create a .conf file with the desired parameters as in the example in post #12 above. To make all three parameters permanent -
```
echo "options rtl8192ce swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot and all these parameters will automatically load with the driver since next boot.

If this doesn't seem to make the connection satisfactory, start a new thread with a suitable title and full description of the problem. If you do so, feel free to PM me or post here the link to your new thread so we can follow. :)

---

### Post by evan8 on 2014-02-16
Ok. One last question. How do I make a conf file? and have permission to do so? sorry pretty new to ubuntu.And what should I name it. thanks

---

### Post by varunendra on 2014-02-16
The command in my previous post will automatically create it for you, with the desired line in it. That is, open a terminal (Ctrl-Alt-T) and copy-paste the following command in it -
```
[COLOR="#0000CD"]echo "**options rtl8192ce swenc=1 ips=0 fwlps=0**"[/COLOR] | [COLOR="#800000"]sudo tee **/etc/modprobe.d/rtl8192ce.conf**[/COLOR]
```
The 'echo' command 'echoes' the desired line with correct syntax.
The 'Pipe' symbol after it (|) causes this 'echoed' line to become input for the command after it, instead of getting printed on the screen.
The "tee" command prints this 'input' line on the screen while ALSO WRITING it to the file given as its arguement. The "sudo" before it grants it the root access so that it can create that file. Make sure to type in your login password correctly when asked by "sudo" (you won't see anything on the screen while typing the password).

So in short, the part in [COLOR="#0000CD"]BLUE[/COLOR] echoes the desired line, the part in [COLOR="#800000"]BROWN[/COLOR] writes it down to the "/etc/modprobe.d/rtl8192ce.conf" file. All done ! :D

---

### Post by evan8 on 2014-02-16
Ah okay. so the last part is what creates the file name. thanks. and now I know what echo does :)

---

### Post by alexaiv on 2014-02-28
> **varunendra said:**
> Welcome to the forums alexaiv, and thanks for the feedback! :)

The recent versions of this driver are frequently being reported to be problematic with connectivity, so if this made your connection stable, it is a valuable feedback for us. But of course if the problem returns, feel free to start a new thread and let us know the current situation with reference to this (and whatever else) workaround(s) you tried.

Hope you'd enjoy Ubuntu and our forums here. :)

See you around !

Hello again, so I thought I'd write here at first and if you feel this should be a new thread tell me to move it. 

As I wrote I tried the method you suggested and it seemed to work for a few days but I had some stability issues again. I then tried the solution with all commands (swenc = 1, ips = 0, flps = 0) and that seemed to work as well but now things are pretty bad. I have no stable connection at all, my wifi disconnects every few minutes. I am seriously considering to install a 32bit version of Kubuntu, even though I have 8gb of ram on my laptop and from my research on the internet this problem only appears on 64bit versions. 

My question is this: even though Kubuntu is based on Ubuntu, could it be that this is the reason this doesn't work form me? If so, could you suggest another solution? 

Thanks a lot and keep up the great work! :D

---

### Post by varunendra on 2014-02-28
> **alexaiv said:**
> Hello again, so I thought I'd write here at first and if you feel this should be a new thread tell me to move it.

Hello alexaiv! I was suspecting the problem may return later, as I also mentioned in my previous reply to you. If you have made those changes permanent, try deleting the config file you created (I assume it would be /etc/modprobe.d/rtl8192ce.conf). Those parameters are not always necessary and should be only used when they really help.

I am assuming an update must have changed the driver version and the newer driver either isn't helped by those parameters or maybe even having problem with them (although I believe all three of them are completely safe, but just to be sure..).

If reverting to defaults doesn't help, **it would be a good idea to start a new thread** and give us its link here so that anyone following this one may follow yours if required.

---

