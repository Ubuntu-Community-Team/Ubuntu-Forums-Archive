---
title: "Asus USB-N13 Adapter Wireless N300"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by GHh3LrM on 2013-10-23
Hello everybody,
I'd really need help with this wireless adapter that I bought for Linux (Ubuntu 12.04 LTS). I tested it on Windows and it works. I know that several similar posts have already been opened and solved but I don't really manage to solve my problem. As far as I understand, Linux sees the adapter because the indicator starts charging, but it never really connects. Probably it has to do something with the fact that the drivers provided are compatible with Linux 2.6 and I am using a more modern version. I tried launching install.sh in the main directory and this is what i get:

```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730
USB-N13 Linux Driver Quick Start.txt
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
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-29-generic/build M=/home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.o
In file included from /home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.c:23:0:
/home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_service.h: In function ‘thread_enter’:
/home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_service.h:575:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/federico/Scrivania/Linux/RTL819xC_USB_linux_v3.4.4_4749.20120806/RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

Following the instruction I found in [http://ubuntuforums.org/showthread.php?t=2133710&page=3](http://ubuntuforums.org/showthread.php?t=2133710&page=3) I took the file from [https://dl.dropbox.com/u/58267392/RT...D.3.2_3192.zip]("https://dl.dropbox.com/u/58267392/RTL819xCU_USB_linux_%20v3%5B1%5D.3.2_3192.zip"), as proposed by chili555, and installed it. When I try making:

```
cd Desktop/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103
sudo su
sh install.sh
```

it gives:
```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103.tar.gz
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/autoconf_rtl8192c_usb_linux.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_xmit.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_ioctl_query.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/efuse/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/efuse/rtw_efuse.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_recv.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_br_ext.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_eeprom.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_debug.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_p2p.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_ieee80211.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_security.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_mlme.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_mp.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_sta_mgt.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_rf.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_pwrctrl.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_wlan_util.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_mlme_ext.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_io.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_ioctl_rtl.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_mp_ioctl.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_ioctl_set.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_iol.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/wlan0dhcp
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/autoconf_rtl8192d_usb_linux.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/osdep_service.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/recv_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/os_intfs.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/usb_intf.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/mlme_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/pci_intf.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/sdio_intf.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/os_dep/linux/xmit_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/wlan_bssdef.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/cmd_osdep.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_recv.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_mlme_ext.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/wifi.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_led.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_recv.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/farray.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192CPhyReg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DPhyCfg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_hal.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_dm.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_rf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_recv.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/nic_spec.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/usb_osintf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_dm.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_xmit.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_event.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_qos.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_pwrctrl.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_xmit.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_spec.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_ce_service.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_ops.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/ieee80211.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/recv_osdep.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_types_linux.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_efuse.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192CUHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_ops_ce.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/usb_ops.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_ht.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/ethernet.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/mp_custom_oid.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_ioctl_rtl.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_ops_linux.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DUHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_spec.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_mlme.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/hal_init.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_types.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DEHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/ieee80211_ext.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_types_ce.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192CPhyCfg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_led.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/swab.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/swabb.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/big_endian.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/little_endian.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/byteorder/generic.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_mp_ioctl.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_ops_xp.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DETestHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_osintf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192CEHWImg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_p2p.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/pci_hal.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_conf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/usb_vendor_req.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_service.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_ioctl_query.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_eeprom.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_types_xp.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_byteorder.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_xmit.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_version.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_cmd.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_ioctl_set.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/h2clbk.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/pci_osintf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_cmd.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192d_rf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/pci_ops.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_cmd.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_event.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/mlme_osdep.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_debug.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_intf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sta_info.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_iol.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_rf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/usb_hal.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/autoconf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_security.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/sdio_hal.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_io.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/Hal8192DPhyReg.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_br_ext.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/circ_buf.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/basic_types.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_hal.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/ip.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_led.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/if_ether.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/xmit_osdep.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtl8192c_sreset.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_mp.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_ioctl.h
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/ifcfg-wlan0
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/Makefile
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/make_drv
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/Kconfig
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/hal_init.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_rxdesc.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_cmd.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_phycfg.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_mp.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_dm.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_rf6052.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/Hal8192DUTestHWImg.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/rtl8192du_recv.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/usb_halinit.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/rtl8192du_xmit.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/Hal8192DUHWImg.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/rtl8192du_led.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/usb/usb_ops_linux.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/hal/rtl8192d/rtl8192d_hal_init.c
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/clean
rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103
[COLOR=#ff0000]Please select card type(1/2):[/COLOR]
[COLOR=#ff0000]1) RTL8192cu[/COLOR]
[COLOR=#ff0000]2) RTL8192du[/COLOR]
[COLOR=#ff0000]#? 1[/COLOR]
[COLOR=#ff0000]You have selected RTL8192cu[/COLOR]
rtw_version.h has existed!
Authentication requested [root] for make clean:
install.sh: 38: [: unexpected operator
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
install.sh: 48: [: unexpected operator
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-29-generic/build M=/home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.o
In file included from /home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.c:23:0:
/home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_service.h: In function ‘thread_enter’:
/home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_service.h:569:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/federico/Scrivania/Wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

Notice that I selected the first card but I don't know what it is talking about.

Then I tried:
```
modprobe -r rtl8192cu
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
modprobe 8192cu
exit
```

but it gave:
```

FATAL: Module 8192cu not found

```

Thanks in advance!

---

### Post by GHh3LrM on 2013-10-23
Oh, and I forgot to tell you that after that Linux doesn't see the adapter anymore :o

---

### Post by GHh3LrM on 2013-10-25
Is it possible that it is so difficult to have a wireless adapter fully compatible with Linux with up-to-date drivers?

---

