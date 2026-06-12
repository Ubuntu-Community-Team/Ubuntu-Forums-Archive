---
title: "Edimax EW-7811Un driver won't compile"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by Charles_H on 2014-12-05
Brand new to Linux, but not afraid of the terminal (just will likely need the commands/what y'all are looking for as output spelled out)  Running 14.04 LTS, and having a hard time getting wifi to work.

Been trying all day to get my shiny new Edimax EW-7811Un USB wireless adapter to work.  It just won't show up in lsusb or lsmod at all, and ifconfig shows nothing for wlan0.  Trying ifconfig wlan0 up produces an "ERROR while getting interface flags: No such device".  After poking around on the forums and other places, it seems as if my kernel (3.13.0-40) is newer than what the driver was written for (2.6.18-2.6.33); further it supposedly relies on a function that was deprecated in order to compile - would explain the errors I am getting, but I am not sure how to read it.

Here is the output from the terminal whenever I try to compile the driver via the install.sh script as copied from the CD:

```
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-40-generic/build M=/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-40-generic'
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.o
  CC [M]  /home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: In function &#8216;rtw_proc_init_one&#8217;:
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:3: error: implicit declaration of function &#8216;create_proc_entry&#8217; [-Werror=implicit-function-declaration]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
   ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:11: warning: assignment makes pointer from integer without a cast [enabled by default]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
           ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:3: error: implicit declaration of function &#8216;create_proc_read_entry&#8217; [-Werror=implicit-function-declaration]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
         ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:326:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("log_level", S_IFREG | S_IRUGO,
         ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:332:8: error: dereferencing pointer to incomplete type
   entry->write_proc = proc_set_log_level;
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:348:21: warning: assignment makes pointer from integer without a cast [enabled by default]
   padapter->dir_dev = create_proc_entry(dev->name,
                     ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:379:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("write_reg", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:385:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_write_reg;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:387:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("read_reg", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:393:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_read_reg;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:396:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("fwstate", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:404:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sec_info", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:412:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mlmext_state", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:420:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("qos_option", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:427:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_option", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_info", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:441:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ap_info", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:448:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("adapter_state", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:455:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("trx_info", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:462:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:469:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:476:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:483:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:490:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:497:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:504:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:511:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:520:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump3", S_IFREG | S_IRUGO,
         ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:527:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump4", S_IFREG | S_IRUGO,
         ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:537:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("all_sta_info", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:555:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("best_channel", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:561:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_best_channel;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:564:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_signal", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:570:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_signal;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:572:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_enable", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:578:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ht_enable;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:580:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("cbw40_enable", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:586:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_cbw40_enable;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:588:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ampdu_enable", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:594:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ampdu_enable;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:596:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_stbc", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:602:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_stbc;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:605:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("path_rssi", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:608:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("vid", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("pid", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rssi_disp", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:628:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rssi_disp;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:631:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sreset", S_IFREG | S_IRUGO,
        ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: At top level:
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: (near initialization for &#8216;rtw_netdev_ops.ndo_select_queue&#8217;) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/charles/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-40-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

I also tried a couple patches found...somewhere among the dozens of tabs related to these forums, AskUbuntu, you name it, in the last 7 hours that held the promise of fixing it, but still no dice.  I've attached the pair of files.[ATTACH]258416[/ATTACH][ATTACH]258417[/ATTACH].  In the name of a tidy OP, here is a link to a [pastebin of what happens]("http://paste.ubuntu.com/9391956/") when I try running install.sh with these two in the directory.  Tried fixes in [this article]("http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu") as well, and still nothing...

 I am just completely lost in trying to figure out what I need to do in order to make this thing show up...and that's under the assumption that the wlan0 interface shows up once this gets working!

Thanks in advance for the help, y'all.

---

### Post by mikewhatever on 2014-12-06
First, you need to look at the output of **lsusb**. Edimax EW-7811Un usually has rtl8192cu inside (which is recognized out of the box), but they may have changed it.
Don't compile a driver from the CD, those are usually old, and won't work with newer kernels. 
Try this instead: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

---

### Post by praseodym on 2014-12-06
Right, install it like this:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

---

### Post by Charles_H on 2014-12-06
> **mikewhatever said:**
> First, you need to look at the output of **lsusb**. Edimax EW-7811Un usually has rtl8192cu inside (which is recognized out of the box), but they may have changed it.
Don't compile a driver from the CD, those are usually old, and won't work with newer kernels. 
Try this instead: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Here is the output of lsusb:

```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 008 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Somehow it's not even seeing the module, unlike with the other one I've tried before this one (and gave up on because it was being too difficult)  Think it might just be a bad adapter?  No idea if it is, but the thought just occurred to me...

> **praseodym said:**
> Right, install it like this:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

Unfortunately, that was one of the things I tried before.  Tried it again, and still no change in the adapter

---

### Post by mikewhatever on 2014-12-06
...not much we can do, if it's not recognized at all. How about the output of **dmesg | tail** right after the adapter is plugged in?

---

### Post by Charles_H on 2014-12-06
Here's that output... doesn't look all that promising, from what I'm seeing.

```

[18370.816621] usb 4-2: device descriptor read/64, error -32
[18371.056484] usb 4-2: new full-speed USB device number 19 using ohci-pci
[18371.196196] usb 4-2: device descriptor read/64, error -32
[18371.440174] usb 4-2: device descriptor read/64, error -32
[18371.679983] usb 4-2: new full-speed USB device number 20 using ohci-pci
[18372.087517] usb 4-2: device not accepting address 20, error -32
[18372.223482] usb 4-2: new full-speed USB device number 21 using ohci-pci
[18372.631135] usb 4-2: device not accepting address 21, error -32
[18372.631237] hub 4-0:1.0: unable to enumerate USB device on port 2
[19215.209595] usb 1-5: new high-speed USB device number 11 using ehci-pci

```

Regardless, thanks for all the help!  I've always been more of a software guy than hardware, and dealing with these problems I've been having (with this adapter and the other one before) have been beyond my knowledge entirely.

---

### Post by chili555 on 2014-12-06
> hub 4-0:1.0: unable to enumerate USB device on port 2It looks defective to me. Does it appear as expected when inserted into any other computer?

---

### Post by praseodym on 2014-12-07
Or is it plugged to the hub?

```
Bus 008 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
```

---

