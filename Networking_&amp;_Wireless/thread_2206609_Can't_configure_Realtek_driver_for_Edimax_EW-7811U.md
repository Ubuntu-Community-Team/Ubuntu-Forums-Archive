---
title: "Can't configure Realtek driver for Edimax EW-7811Un?"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by joseph13 on 2014-02-19
I've read many other threads and tutorials on how to install this specific wifi adapter, yet I'm having a problem nothing has solved.

First, I downloaded the latest driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=274&DownTypeID=3&GetDown=false&Downloads=true#2742"). 

Afterwards I opened "/etc/modules.d/blacklist.conf" in gedit in sudo mode, and pasted the following at the bottom:

```
# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

Then I opened the terminal, located the extracted driver folder, and typed

```
sudo bash install.sh
```

After all the articles and tutorials I've read, I thought this was going to work. Instead, I got this:

```
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```

I read somewhere that this problem was due to not having a Linux header package. I have, however, had this package the entire time, up to date.

I'm really new to Ubuntu, and Linux in general. I have no idea where to turn from here.

Can anyone please explain this problem to me in a beginner-friendly way? :) Thanks much.

EDIT: Forgot to mention what ubuntu version I'm using. I'm using 13.10.

---

### Post by chili555 on 2014-02-19
Without seeing the exact error, it's very hard to troubleshoot. I compiled the package and got lots of errors like this:> /os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete typeI am assuming that the package was written for an earlier kernel and gcc version than that included in Ubuntu 13.10.

I suggest we troubleshoot your existing rtl8192cu before we try to hammer this older driver into service. 

If we decide a newer driver is the best option, let's try this instead: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) > This is a port of Realtek's own 8192cu driver for USB Wifi chipsets, ported to kernel 3.11 as ships with Ubuntu 13.10.I expect you may need a bit of assistance to build a driver from github.

What is happening or not with the built-in rtl8192cu?

---

### Post by joseph13 on 2014-02-19
Here's what shows up.

```

rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_rtl.crtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp_ioctl.c
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
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-17-generic/build M=/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-17-generic'
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.o
  CC [M]  /home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
   ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:11: warning: assignment makes pointer from integer without a cast [enabled by default]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
           ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
         ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:326:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("log_level", S_IFREG | S_IRUGO,
         ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:332:8: error: dereferencing pointer to incomplete type
   entry->write_proc = proc_set_log_level;
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:348:21: warning: assignment makes pointer from integer without a cast [enabled by default]
   padapter->dir_dev = create_proc_entry(dev->name,
                     ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:379:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("write_reg", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:385:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_write_reg;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:387:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("read_reg", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:393:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_read_reg;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:396:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("fwstate", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:404:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sec_info", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:412:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mlmext_state", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:420:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("qos_option", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:427:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_option", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_info", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:441:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ap_info", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:448:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("adapter_state", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:455:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("trx_info", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:462:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:469:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:476:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:483:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:490:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:497:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:504:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:511:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:520:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump3", S_IFREG | S_IRUGO,
         ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:527:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump4", S_IFREG | S_IRUGO,
         ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:537:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("all_sta_info", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:555:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("best_channel", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:561:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_best_channel;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:564:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_signal", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:570:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_signal;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:572:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_enable", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:578:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ht_enable;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:580:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("cbw40_enable", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:586:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_cbw40_enable;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:588:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ampdu_enable", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:594:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ampdu_enable;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:596:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_stbc", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:602:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_stbc;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:605:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("path_rssi", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:608:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("vid", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("pid", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rssi_disp", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:628:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rssi_disp;
       ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:631:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sreset", S_IFREG | S_IRUGO,
        ^
/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
cc1: some warnings being treated as errors
make[2]: *** [/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/aphos/Downloads/wifi/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-17-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

I'm afraid that's all I know. I downloaded the file from github, but the installation instructions make no sense to me whatsoever.

(I just started using Linux yesterday...)

---

### Post by joseph13 on 2014-02-20
Bump.

---

### Post by chili555 on 2014-02-20
> **joseph13 said:**
> Bump.As I said previously, I suggest we troubleshoot your existing rtl8192cu before we try to hammer this older driver into service. What is happening or not with the built-in rtl8192cu?

---

### Post by soum_axetuirk on 2014-02-20
The Edimax EW7811-UN is a wireless USB adapter that complies with the  802.11b/g/n IEEE standards. The device has a Realtek RTL8188CUS based  chipset which has support for Windows, Mac & Linux.
1)  Insure that the 7811uN device is not plugged into any USB port on your computer.  
2)  Insure that no similar driver is loaded on your machine with "lsmod | grep 8192". 
If the result  shows that the "8192cu" driver module is loaded, you have nothing left to do.  
If the result is nil,continue with this installation.
If it shows some other "...8192..." driver, uninstall it with 
"rmmod -r ".  
3)  In your favorite browser navigate to <a href="[http://www.realtek.com.tw/downloads/]("http://ubuntuforums.org/view-source:http://www.realtek.com.tw/downloads/")" rel="nofollow">www.realtek.com.tw/downloads/</a><br>4)  
Since links may change with time, drill down to the download from this webpage by selecting (starting in the left hand panel under "Downloads")
Communications Network ICs --&gt; Wireless LAN ICs --&gt; WLAN NIC --&gt;IEEE 802.11b/g/n Single Chip --&gt; Software
5) Now you are on the "Software: Drivers and Utilities" page.  Under "Step 1. Select one or more models"check the box by RTL8192CU.
Now click on the "go" button under "Step 2."
6) The new webpage should be subtitled "RTL8192CU".  Under "Unix (Linux)", click on a mirror site for the "Linux Kernel 2.6.18-2.6.38 and Kernel 3.0.8 Version 3.4.4_4749" download.
Note that the name<br>    and revision of this download may change as Realtek updates the driver.
7) The driver file will be downloaded as appropriate for your browser.
The file downloaded as of this writing is  RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip.
8) Create a directory ~/temp (or some convenient name like that).
```


mv ~/Downloads/RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip ~/temp/
cd ~/temp
tar xvf RTL8192xC*.zip
cd ~/temp/RTL8188C_8192C_USB_linux_3.4.4_4749.20121105
```

13)  Invoke the installation script with 
```
./install.sh
```
14)  Plug the 7811uN into a USB port on your computer.
15)  Check that the module was installed by running 
```
lsmod | grep 8192
```
16)  Now configure the wireless device using the network configuration tools of your Linux distro.

---

### Post by chili555 on 2014-02-20
> RTL8192xC_USB_linux_v3.4.4_4749.[COLOR="#FF0000"]2012[/COLOR]1105.zipThis old-timer will *NOT* compile on Ubuntu 13.10. Please do not waste your time.> 6) The new webpage should be subtitled "RTL8192CU". Under "Unix (Linux)", click on a mirror site for the "[COLOR="#FF0000"]Linux Kernel 2.6.18-2.6.38 and Kernel 3.0.8[/COLOR] Version 3.4.4_4749" download.Ubuntu 13.10 uses kernel version 3.11.0-xx which is incompatible with the package mentioned.

---

### Post by joseph13 on 2014-02-21
> **chili555 said:**
> As I said previously, I suggest we troubleshoot your existing rtl8192cu before we try to hammer this older driver into service. What is happening or not with the built-in rtl8192cu?

As I also said previously, I'm new to Linux and the lingo that surrounds it... I don't know how to troubleshoot the driver, and I have no idea what's happening with it. I didn't even know there was a built in rtl8192cu.

---

### Post by chili555 on 2014-02-21
> **joseph13 said:**
> As I also said previously, I'm new to Linux and the lingo that surrounds it... I don't know how to troubleshoot the driver, and I have no idea what's happening with it. I didn't even know there was a built in rtl8192cu.I apologize. Let's go back to basics and I'll try harder to explain what we're doing. 

First, let's see specifically what wireless device you have and go forward after we know the facts. We will work from the terminal since that is the easiest way to gather information quickly. Please insert your Edimax, open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Thanks.

I will do better in the future.

---

### Post by joseph13 on 2014-02-23
> **chili555 said:**
> I apologize. Let's go back to basics and I'll try harder to explain what we're doing. 

First, let's see specifically what wireless device you have and go forward after we know the facts. We will work from the terminal since that is the easiest way to gather information quickly. Please insert your Edimax, open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Thanks.

I will do better in the future.

No worries. :)

This is the output from the terminal.

```
aphos@Joseph-PC:~$ lsusbBus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
aphos@Joseph-PC:~$ 

```

---

### Post by chili555 on 2014-02-24
> **7392:7811** Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]As you may already know, the correct driver for this device is rtl8192cu. It appears in the alias list in the driver in Ubuntu 13.10:```
$ modinfo rtl8192cu | grep 7811
alias:          usb:v[COLOR="#FF0000"]7392[/COLOR]p[COLOR="#FF0000"]7811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```Since the driver exists in Ubuntu 13.10 and, hopefully, claimed your device, my question that I ham-handedly posed a few posts ago remains. What was it about the driver rtl8192cu that's built in to Ubuntu 13.10 didn't work for you? What was it that motivated you to look for and install a different driver?

---

### Post by joseph13 on 2014-02-26
> **chili555 said:**
> As you may already know, the correct driver for this device is rtl8192cu. It appears in the alias list in the driver in Ubuntu 13.10:```
$ modinfo rtl8192cu | grep 7811
alias:          usb:v[COLOR=#FF0000]7392[/COLOR]p[COLOR=#FF0000]7811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```Since the driver exists in Ubuntu 13.10 and, hopefully, claimed your device, my question that I ham-handedly posed a few posts ago remains. What was it about the driver rtl8192cu that's built in to Ubuntu 13.10 didn't work for you? What was it that motivated you to look for and install a different driver?

Now I see. Yes, the pre-existing driver was not working in the way it should have. I'd put in the adapter and it would detect my network, but it refused to connect.

I have since fixed this problem. I re-installed ubuntu, only during the installation this time it had an internet connection via an ethernet cable. Afterwords, I put in the adapter again, and it worked perfectly fine. My guess is it never installed certain things it needed to operate.

Oh well. Thanks for the help :)

---

