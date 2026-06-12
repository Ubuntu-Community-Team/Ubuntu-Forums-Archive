---
title: "Trying to connect to internet through wireless adapter - B-Link BL_LW05-AR5"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by ridgechris20 on 2014-03-02
[SIZE=3]Hello,

[COLOR=#333333][FONT=UbuntuRegular]I am new using Ubuntu and I am trying to make my old optiplex wireless with the LB Link Wireless adapter. I have tried download and installing the rtl8192_8188cu driver but I get a error message when running in terminal. [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I am not really sure what I am doing wrong, excuse my ignorance on this issue (first time doing this). Here is the information of what i am using:[/FONT][/COLOR][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=3]Computer - Dell Optiplex 755 - Intel® Core&#8482;2 Duo CPU E8400 @ 3.00GHz × 2 OS - Ubuntu 12.07 LTS Wifi Adapter - LB-Link Model: BL_LW05-AR5.[/SIZE]

[/FONT][/COLOR]
    ```
chris@OptiPlex:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715$ sudo bash install.sh
[sudo] password for chris: 
        Auto install for 8192cu
        September, 1 2010 v 1.0.0
rtl8192_8188CU_linux_v3.0.2164.20110715/
rtl8192_8188CU_linux_v3.0.2164.20110715/autoconf_rtl8192c_usb_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/clean
rtl8192_8188CU_linux_v3.0.2164.20110715/core/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/rtw_efuse.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_debug.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_eeprom.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ieee80211.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_io.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_query.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_rtl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_set.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme_ext.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp_ioctl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_p2p.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_pwrctrl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_rf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_security.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_sta_mgt.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_wlan_util.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_dm.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_sreset.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0
rtl8192_8188CU_linux_v3.0.2164.20110715/include/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig
rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c
rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa
rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp
rtl8192_8188CU_linux_v3.0.2164.20110715
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-36-generic/build M=/home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-36-generic'
  CC [M]  /home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/chris/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-36-generic'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg
```
[COLOR=#333333][FONT=UbuntuRegular]
[SIZE=3]**Here is the output for code lsusb in terminal:**[/SIZE]

[/FONT][/COLOR]
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by varunendra on 2014-03-03
Welcome to the forums ridgechris20!

The drivers supplied with these devices are usually too outdated, and in your case it indeed is. The driver you are using is from 2011 which won't compile on currently supported kernel versions.

But have you tried using it without installing the driver? Most often these devices are natively supported and you don't need to install any third party drivers for them.

Your lsusb is not showing 'Any' USB device plugged in. Was the adapter plugged when you ran the command?

Please plug in the adapter, then post back the output of lsusb again, when it is showing up in the output. Along with the lsusb output, please also post the output of -
```
nm-tool
```

---

### Post by ridgechris20 on 2014-03-03
Thank you for the quick response. Yes I did just try seeing if it worked without doing the driver and it just sat there like nothing was plugged in. I made sure it was plugged in and tried again, here is the results ok lsusb.

```
chris@OptiPlex:~$ lsusb
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


Here is the output of nm-tool:

```
chris@OptiPlex:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:1E:4F:BC:84:A6


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.0.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.76.76
    DNS:             75.75.75.75


  IPv6 Settings:
    Address:         2601:4:4880:5f:7541:10f8:595b:85a4
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         2601:4:4880:5f:d923:6552:4b0c:ada3
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         2601:4:4880:5f:fe4e:1166:ed42:b006
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         2601:4:4880:5f:5caf:d24:20d5:c7d4
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         2601:4:4880:5f:21e:4fff:febc:84a6
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         fe80::21e:4fff:febc:84a6
    Prefix:          64
    Gateway:         fe80::c639:3aff:febf:7322


    Address:         2601:4:4880:5f:fe4e:1166:ed42:b006
    Prefix:          64
    Gateway:         ::


    DNS:             2001:558:feed::2
    DNS:             2001:558:feed::1

```

---

### Post by varunendra on 2014-03-04
> **ridgechris20 said:**
> ```
chris@OptiPlex:~$ lsusb
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
```

With the adapter plugged in and detected, what is the output of -
```
dmesg | grep rtl81
```
Any error messages? If it is blank, try -
```
sudo modprobe -v rtl8192cu
```
Any errors here? If not, post back the output of the above dmesg command after doing this.

If required, we may try either the proprietary driver from Realtek's official site, or a much newer backported one. The one on Realtek's official site is also from 2012, and may not compile well on your kernel version. But the backported one should.

---

### Post by ridgechris20 on 2014-03-04
Here is the output for [COLOR=#000000][FONT=Ubuntu Mono]dmesg[/FONT][/COLOR]

```
[    1.452717] usb usb5: Product: UHCI Host Controller
[    1.452719] usb usb5: Manufacturer: Linux 3.8.0-36-generic uhci_hcd
[    1.452721] usb usb5: SerialNumber: 0000:00:1d.0
[    1.452790] hub 5-0:1.0: USB hub found
[    1.452793] hub 5-0:1.0: 2 ports detected
[    1.452850] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.452853] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.452856] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.452875] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    1.452897] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.452898] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.452900] usb usb6: Product: UHCI Host Controller
[    1.452902] usb usb6: Manufacturer: Linux 3.8.0-36-generic uhci_hcd
[    1.452904] usb usb6: SerialNumber: 0000:00:1d.1
[    1.452967] hub 6-0:1.0: USB hub found
[    1.452970] hub 6-0:1.0: 2 ports detected
[    1.453028] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.453031] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.453034] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.453053] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.453076] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.453077] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.453079] usb usb7: Product: UHCI Host Controller
[    1.453081] usb usb7: Manufacturer: Linux 3.8.0-36-generic uhci_hcd
[    1.453083] usb usb7: SerialNumber: 0000:00:1d.2
[    1.453146] hub 7-0:1.0: USB hub found
[    1.453149] hub 7-0:1.0: 2 ports detected
[    1.453251] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.456082] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.456087] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.456171] mousedev: PS/2 mouse device common for all mice
[    1.456269] rtc_cmos 00:04: RTC can wake from S4
[    1.456362] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.456383] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.456457] device-mapper: uevent: version 1.0.3
[    1.456504] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.456517] EISA: Probing bus 0 at eisa.0
[    1.456519] EISA: Cannot allocate resource for mainboard
[    1.456520] Cannot allocate resource for EISA slot 1
[    1.456521] Cannot allocate resource for EISA slot 2
[    1.456522] Cannot allocate resource for EISA slot 3
[    1.456524] Cannot allocate resource for EISA slot 4
[    1.456525] Cannot allocate resource for EISA slot 5
[    1.456526] Cannot allocate resource for EISA slot 6
[    1.456527] Cannot allocate resource for EISA slot 7
[    1.456529] Cannot allocate resource for EISA slot 8
[    1.456530] EISA: Detected 0 cards.
[    1.456536] cpufreq-nforce2: No nForce2 chipset.
[    1.456538] cpuidle: using governor ladder
[    1.456539] cpuidle: using governor menu
[    1.456544] ledtrig-cpu: registered to indicate activity on CPUs
[    1.456545] EFI Variables Facility v0.08 2004-May-17
[    1.456671] ashmem: initialized
[    1.456772] TCP: cubic registered
[    1.456857] NET: Registered protocol family 10
[    1.457014] NET: Registered protocol family 17
[    1.457022] Key type dns_resolver registered
[    1.457146] Using IPI No-Shortcut mode
[    1.457214] Loading module verification certificates
[    1.460264] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e34b02eff47045b53890088da2689daa418f21cd'
[    1.460274] registered taskstats version 1
[    1.461972] Key type trusted registered
[    1.463347] Key type encrypted registered
[    1.464988] rtc_cmos 00:04: setting system clock to 2014-03-01 03:09:13 UTC (1393643353)
[    1.465267] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.465269] EDD information not available.
[    1.750528] ata3: SATA link down (SStatus 4 SControl 300)
[    1.750565] ata4: SATA link down (SStatus 4 SControl 300)
[    1.792013] tsc: Refined TSC clocksource calibration: 2992.481 MHz
[    1.792017] Switching to clocksource tsc
[    1.914613] ata2.00: SATA link down (SStatus 4 SControl 300)
[    1.914623] ata2.01: SATA link down (SStatus 4 SControl 300)
[    2.060055] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.060067] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.076301] ata1.00: ATA-8: WDC WD2500AAKX-00ERMA0, 15.01H15, max UDMA/133
[    2.076304] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.076545] ata1.01: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.076548] ata1.01: 5860533168 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.092298] ata1.00: configured for UDMA/133
[    2.108344] ata1.01: configured for UDMA/133
[    2.108455] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKX-0 15.0 PQ: 0 ANSI: 5
[    2.108568] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.108585] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.108614] sd 0:0:0:0: [sda] Write Protect is off
[    2.108616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.108633] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.108669] scsi 0:0:1:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.108743] sd 0:0:1:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.108745] sd 0:0:1:0: [sdb] 4096-byte physical blocks
[    2.108754] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    2.139455] sd 0:0:1:0: [sdb] Write Protect is off
[    2.139456]  sda: sda1 sda2 < sda5 >
[    2.139461] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.139500] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.157179] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.183547]  sdb: sdb1
[    2.183712] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.274228] Freeing unused kernel memory: 796k freed
[    2.274400] Write protecting the kernel text: 6368k
[    2.274452] Write protecting the kernel read-only data: 2548k
[    2.274453] NX-protecting the kernel data: 5920k
[    2.286210] udevd[110]: starting version 175
[    2.345638] Disabling lock debugging due to kernel taint
[    2.347428] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    2.347430] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    2.347467] e1000e 0000:00:19.0: setting latency timer to 64
[    2.347512] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.347539] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    2.616896] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.616899] EXT4-fs (sda1): write access will be enabled during recovery
[    2.645978] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1e:4f:bc:84:a6
[    2.645981] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.646002] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: 1051FF-0FF
[    4.310528] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.310536] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7081252
[    4.310600] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7081107
[    4.310613] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7081404
[    4.310624] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078943
[    4.310636] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7080886
[    4.310648] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078950
[    4.310659] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7080885
[    4.310670] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078930
[    4.310681] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078949
[    4.310692] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078802
[    4.310704] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078919
[    4.310716] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7078847
[    4.310728] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14942220
[    4.310735] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14942218
[    4.310742] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14942217
[    4.310748] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14942216
[    4.310753] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14942215
[    4.310759] EXT4-fs (sda1): 17 orphan inodes deleted
[    4.310760] EXT4-fs (sda1): recovery complete
[    4.589700] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.927582] init: ureadahead main process (254) terminated with status 5
[    7.128506] Adding 2051068k swap on /dev/sda5.  Priority:-1 extents:1 across:2051068k 
[    8.314214] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.543494] udevd[331]: starting version 175
[    9.942843] lp: driver loaded but no devices found
[   10.396458] parport_pc 00:05: reported by Plug and Play ACPI
[   10.396509] parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
[   10.492103] lp0: using parport0 (interrupt-driven).
[   10.525980] ppdev: user-space parallel port driver
[   10.856954] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.873081] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.025109] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \GLBC 1 (20121018/utaddress-251)
[   11.025115] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SACT 2 (20121018/utaddress-251)
[   11.025118] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SSTS 3 (20121018/utaddress-251)
[   11.025122] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.025125] ACPI Warning: 0x000008b0-0x000008bf SystemIO conflicts with Region \GIC2 1 (20121018/utaddress-251)
[   11.025128] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.025130] ACPI Warning: 0x00000880-0x000008af SystemIO conflicts with Region \GIC1 1 (20121018/utaddress-251)
[   11.025132] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.025134] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.031636] microcode: CPU0 sig=0x1067a, pf=0x1, revision=0xa0c
[   11.168546] mei 0000:00:03.0: setting latency timer to 64
[   11.168713] mei 0000:00:03.0: irq 43 for MSI/MSI-X
[   11.748363] microcode: CPU1 sig=0x1067a, pf=0x1, revision=0xa0c
[   11.749471] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.950810] [drm] Initialized drm 1.1.0 20060810
[   12.208257] kvm: disabled by bios
[   12.220774] kvm: disabled by bios
[   12.292271] i915 0000:00:02.0: setting latency timer to 64
[   12.292579] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   12.292588] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.292589] [drm] Driver supports precise vblank timestamp query.
[   12.292613] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.293828] [drm] initialized overlay support
[   12.324269] i915 0000:00:02.0: No connectors reported connected with modes
[   12.324273] [drm] Cannot find any crtc or sizes - going 1024x768
[   12.326650] fbcon: inteldrmfb (fb0) is primary device
[   12.367902] Console: switching to colour frame buffer device 128x48
[   12.370208] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.370210] i915 0000:00:02.0: registered panic notifier
[   12.370281] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.666704] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.824939] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   14.673850] init: failsafe main process (754) killed by TERM signal
[   16.176017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   19.643921] init: isc-dhcp-server main process (982) terminated with status 1
[   19.643942] init: isc-dhcp-server main process ended, respawning
[   20.211117] init: isc-dhcp-server main process (1002) terminated with status 1
[   20.211138] init: isc-dhcp-server main process ended, respawning
[   20.761533] init: isc-dhcp-server main process (1015) terminated with status 1
[   20.761554] init: isc-dhcp-server main process ended, respawning
[   21.379990] FS-Cache: Loaded
[   21.692669] init: isc-dhcp-server main process (1023) terminated with status 1
[   21.692689] init: isc-dhcp-server main process ended, respawning
[   21.762111] FS-Cache: Netfs 'cifs' registered for caching
[   21.762187] Key type cifs.spnego registered
[   21.762195] Key type cifs.idmap registered
[   22.188014] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   23.039825] Bluetooth: Core ver 2.16
[   23.039839] NET: Registered protocol family 31
[   23.039841] Bluetooth: HCI device and connection manager initialized
[   23.039849] Bluetooth: HCI socket layer initialized
[   23.039851] Bluetooth: L2CAP socket layer initialized
[   23.039856] Bluetooth: SCO socket layer initialized
[   23.054430] init: isc-dhcp-server main process (1058) terminated with status 1
[   23.054450] init: isc-dhcp-server main process ended, respawning
[   23.219289] Bluetooth: RFCOMM TTY layer initialized
[   23.219301] Bluetooth: RFCOMM socket layer initialized
[   23.219302] Bluetooth: RFCOMM ver 1.11
[   23.393135] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.393137] Bluetooth: BNEP filters: protocol multicast
[   23.393142] Bluetooth: BNEP socket layer initialized
[   23.621589] init: isc-dhcp-server main process (1079) terminated with status 1
[   23.621612] init: isc-dhcp-server main process ended, respawning
[   24.147310] init: isc-dhcp-server main process (1112) terminated with status 1
[   24.147331] init: isc-dhcp-server main process ended, respawning
[   24.464536] init: isc-dhcp-server main process (1182) terminated with status 1
[   24.464557] init: isc-dhcp-server main process ended, respawning
[   24.973289] init: isc-dhcp-server main process (1194) terminated with status 1
[   24.973311] init: isc-dhcp-server main process ended, respawning
[   25.290427] init: isc-dhcp-server main process (1209) terminated with status 1
[   25.290450] init: isc-dhcp-server main process ended, respawning
[   25.592226] init: isc-dhcp-server main process (1217) terminated with status 1
[   25.592246] init: isc-dhcp-server main process ended, respawning
[   26.150010] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   26.252064] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   26.252177] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.252675] init: isc-dhcp-server main process (1237) terminated with status 1
[   26.252695] init: isc-dhcp-server main process ended, respawning
[   26.253977] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.435288] init: isc-dhcp-server main process (1266) terminated with status 1
[   26.435310] init: isc-dhcp-server main process ended, respawning
[   26.627630] init: isc-dhcp-server main process (1274) terminated with status 1
[   26.627653] init: isc-dhcp-server main process ended, respawning
[   26.803015] init: isc-dhcp-server main process (1300) terminated with status 1
[   26.803038] init: isc-dhcp-server main process ended, respawning
[   26.903470] init: isc-dhcp-server main process (1307) terminated with status 1
[   26.903491] init: isc-dhcp-server main process ended, respawning
[   26.995544] init: isc-dhcp-server main process (1314) terminated with status 1
[   26.995566] init: isc-dhcp-server respawning too fast, stopped
[   28.136861] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   28.136893] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.200017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   29.442262] init: plymouth-upstart-bridge main process (1039) killed by TERM signal
[   34.212015] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   40.224024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   46.236024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   52.248020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   53.822312] init: plymouth-stop pre-start process (2341) terminated with status 1
[   58.260023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   64.272020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   70.284021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   76.296020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   82.308016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   88.320016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[   94.332025] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  100.344029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  106.356020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  112.368023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  118.380023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  124.392033] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  130.404023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  136.416024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  142.428025] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  148.440021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  154.452023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  160.464018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  166.476023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  172.488022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  178.500041] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  184.512848] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  190.524032] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  196.536028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  202.548034] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  208.560024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  214.572020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  220.584029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  226.596033] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  232.608018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  238.620020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  244.632016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  250.644018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  256.656017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  262.668020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  268.680048] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  274.692018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  280.704019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  286.716022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  292.728022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  298.740013] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  304.752030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  310.764029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  316.776023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  322.788022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  328.800102] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  334.812020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  340.824037] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  346.836019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  352.848030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  358.860028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  364.872023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  370.884026] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  376.896032] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  382.908033] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  388.920030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  394.932021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  400.944024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  406.956027] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  412.968023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  418.980019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  424.992016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  431.004097] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  437.016023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  443.028019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  449.040019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  455.052021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  461.064018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  467.076028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  473.088020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  479.100023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  485.112017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  491.124016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  497.136020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  503.148022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  509.160020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  515.172020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  521.184022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  527.196020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  533.208019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  539.220023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  545.232020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  551.244018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  557.256020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  563.268023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  569.280022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  575.292020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  581.304023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  587.316023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  593.328022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  599.340019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  605.352023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  611.364018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  617.376020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  623.388020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  629.400022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  635.412020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  641.424019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  647.436025] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  653.448025] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  659.460027] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  665.472023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  671.484015] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  677.496025] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  683.508023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  689.520022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  695.532021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  701.544028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  707.556020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  713.568015] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  719.580016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  725.592020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  731.604016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  737.616027] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  743.628017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  749.640017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  755.652018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  761.664158] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  767.676040] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  773.688022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  779.700028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  785.712017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  791.724018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  797.736021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  803.748029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  809.760044] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  815.772022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  821.784019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  827.796023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  833.808029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  839.820021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  845.832030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  851.844019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  857.856020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  863.868018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  869.880028] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  875.892018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  881.904030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  887.916048] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  893.928022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  899.940019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  905.952021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  911.964034] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  917.976022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  923.988026] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  930.000016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  936.012014] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  942.024031] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  948.036024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  954.048018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  960.060015] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  966.072017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  972.084052] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  978.096029] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  984.108020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  990.120021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[  996.132030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1002.144038] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1008.156018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1014.168021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1020.180018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1026.192024] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1032.204017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1038.216017] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1044.228021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1050.240020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1056.252023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1062.264020] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1068.276018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1074.288019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1080.300018] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1086.312013] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1092.324019] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1098.336023] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1104.348022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1110.360021] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1116.372016] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1122.384022] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1128.396026] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1134.408030] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[ 1140.420098] mei 0000:00:03.0: unexpected reset: dev_state = RESETING
[50211.056018] usb 1-3: new high-speed USB device number 2 using ehci-pci
[50211.189510] usb 1-3: New USB device found, idVendor=0bda, idProduct=8176
[50211.189514] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[50211.189517] usb 1-3: Product: 802.11n WLAN Adapter
[50211.189520] usb 1-3: Manufacturer: Realtek
[50211.189522] usb 1-3: SerialNumber: 00e04c000001
[59326.649696] usb 1-3: USB disconnect, device number 2
[247925.968017] usb 1-3: new high-speed USB device number 3 using ehci-pci
[247926.101470] usb 1-3: New USB device found, idVendor=0bda, idProduct=8176
[247926.101474] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[247926.101477] usb 1-3: Product: 802.11n WLAN Adapter
[247926.101480] usb 1-3: Manufacturer: Realtek
[247926.101482] usb 1-3: SerialNumber: 00e04c000001
[248154.896182] usb 1-3: USB disconnect, device number 3
[248180.188018] usb 1-2: new high-speed USB device number 4 using ehci-pci
[248180.321454] usb 1-2: New USB device found, idVendor=0bda, idProduct=8176
[248180.321458] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[248180.321461] usb 1-2: Product: 802.11n WLAN Adapter
[248180.321464] usb 1-2: Manufacturer: Realtek
[248180.321467] usb 1-2: SerialNumber: 00e04c000001

```

Here is the output for ```
[COLOR=#000000]sudo modprobe -v rtl8192cu
```  [/COLOR]Looks like[COLOR=#000000] [/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]grep rtl81
``` just came up as blank[/FONT][/COLOR][COLOR=#000000]
[/COLOR]
```
chris@OptiPlex:~$ sudo modprobe -v rtl8192cu
[sudo] password for chris: 
insmod /lib/modules/3.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko


```

---

### Post by ridgechris20 on 2014-03-04
Just check and it looks like its working! It is now picking up wireless connections! Thank you so much!!!

---

### Post by ridgechris20 on 2014-03-04
Okay so I may have jumped ahead of myself, I was able to connect to a wireless network but when I restarted the computer its acting like its not there again.

UPDATE: Its seems to be  connecting again after I put in the code [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rtl8192cu[/FONT][/COLOR] again, but just keeps disconnect and reconnecting every few minutes. Even when I am not doing anything on it.

---

### Post by varunendra on 2014-03-04
> **ridgechris20 said:**
> UPDATE: Its seems to be  connecting again after I put in the code sudo modprobe -v rtl8192cu again, but just keeps disconnect and reconnecting every few minutes.

Please remove the [SOLVED] prefix, as it is not really solved yet. The problem you described above is common with this card/driver and the fix may vary depending on many factors.

First of all, the driver not automatically loading indicates that it may be blacklisted. Please post the output of -
```
grep -R rtl8192 /etc/modprobe.d
```

As for the frequent disconnection issue, please try this in a terminal -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent. If it doesn't, we may try a newer driver.

Please try, and report back with the 'grep..' outputs asked above. We'll proceed as required.

---

### Post by ridgechris20 on 2014-03-04
Sorry, i have changed it.


Output of [COLOR=#000000][FONT=Ubuntu Mono]grep -R rtl8192 /etc/modprobe.d[/FONT][/COLOR]


```
chris@OptiPlex:~$ grep -R rtl8192 /etc/modprobe.d
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu

```
Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rv rtl8192cu[/FONT][/COLOR]

```
chris@OptiPlex:~$ sudo modprobe -rv rtl8192cu
[sudo] password for chris: 
rmmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
rmmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
rmmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko

```

Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v rtl8192cu swenc=Y[/FONT][/COLOR]

```
chris@OptiPlex:~$ sudo modprobe -v rtl8192cu swenc=Y
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko 
insmod /lib/modules/3.8.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko swenc=Y

```





Seems to still be disconnecting every few minutes.

---

### Post by varunendra on 2014-03-04
As suspected, you have blacklisted the driver, hence why it was not loading automatically, requiring you to manually load it with the 'modprobe' command. Please run the following in a terminal -
```
sudo sed -i '/^blacklist rtl8192cu/ d' /etc/modprobe.d/blacklist.conf
```
The above command will delete that line for you and it will load automatically from next boot.

However, if the driver is not performing well, I think we need to try a newer one. Please follow the instructions in this post : [http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)
You only need to follow the installation instructions. Some additional parameters suggested in that thread don't apply to your driver.

Please try and let us know how it performs.

---

### Post by ridgechris20 on 2014-03-05
Ok so I believe I followed everything you said here and the other thread. Now it is finding wireless networks and seems to stay connected but it is so slow. When I run a speed test I am not getting over 2mbps on a 50mbps network. When before I tried the speed test when it was disconnecting I was hitting close to 50mbps. I tried installing the driver you said in the other thread and the newer driver (13) but no change. Is there a output I should post to help or am I just doing something wrong here?


UPDATE:

I have been playing around on the computer and it does seem to be losing connection every once in awhile.

---

### Post by varunendra on 2014-03-06
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

