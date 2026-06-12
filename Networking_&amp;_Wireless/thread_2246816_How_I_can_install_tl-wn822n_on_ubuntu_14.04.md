---
title: "How I can install tl-wn822n on ubuntu 14.04"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by john303 on 2014-10-03
Hi everyone,
Please help me to install driver wn822n on ubuntu 14.04 by using commandline. Thanks a lot!
I have install driver but I faced with many error as following.
> make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/3.8.13-bone49/build M=/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.13-bone49'
  CC [M]  /home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_elf32_bigarmOvgc
make[2]: *** [/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.13-bone49'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

---

### Post by praseodym on 2014-10-03
Hi,

what a kernel is that? Regularly, 14.04 ships kernel 3.13 instead of 3.8. Lets check
```

uname -a
lsb_release -a
dpkg -l linux-image-* | grep ii
```

---

### Post by john303 on 2014-10-04
Here is my results, thank you.

> root@arm:~# uname -a
Linux arm 3.8.13-bone49 #1 SMP Fri May 2 09:50:09 UTC 2014 armv7l armv7l armv7l GNU/Linux
root@arm:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty
root@arm:~# dpkg -l linux-image-* | grep ii
dpkg-query: no packages found matching linux-image-*
root@arm:~#



---

### Post by praseodym on 2014-10-04
Is it a Raspberry? Its arm-based. Lets try this one instead:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms 
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by john303 on 2014-10-04
No, I am using Bealgebone Black, is it right for BBB ?
Thank praseodym!

Have a error after I implement your help. Please help me to solve it, thank so much!
> Building for 3.8.13-bone63 and 3.16.0-armv7-lpae-x2
Building for architecture armhf
Building initial module for 3.8.13-bone63
Done.

8192cu:
Running module version sanity check.
Error! Module version v3.4.4_4749.20121105 for 8192cu.ko
is not newer than what is already found in kernel 3.8.13-bone63 (v4.0.2_9000.20130911).
You may override by specifying --force.

depmod.....

Backing up initrd.img-3.8.13-bone63 to /boot/initrd.img-3.8.13-bone63.old-dkms
Making new initrd.img-3.8.13-bone63
(If next boot fails, revert to initrd.img-3.8.13-bone63.old-dkms image)
update-initramfs....

DKMS: install completed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-armv7-lpae-x2

Here is my driver folder
```
root@arm:/home/ubuntu/822n_drv_wireless# ls
android_ref_codes_JB_4.1             install.sh
android_ref_codes_JB_4.2             readme.txt
android_reference_codes              ReleaseNotes.pdf
android_reference_codes_ICS_nl80211  rtl8192cu-tjp-dkms_1.6_all.deb
document                             WiFi_Direct_User_Interface
driver                               wireless_tools
hardware_wps_pbc                     wpa_supplicant_hostapd

```
Next, I install driver, but some error occured.
```
root@arm:/home/ubuntu/822n_drv_wireless# ./install.sh
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
make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/3.8.13-bone63/build M=/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.13-bone63'
Makefile:580: /usr/src/linux-headers-3.8.13-bone63/arch/armv7l/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-3.8.13-bone63/arch/armv7l/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.13-bone63'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```
After that, I renamed folder 'arm' in arch to 'armv7l', It's pass this error, but occurred a new error.
```
from /home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_l                                                                                inux_v4.0.2_9000.20130911/include/osdep_service.h:759,
                 from /home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_l                                                                                inux_v4.0.2_9000.20130911/core/rtw_cmd.c:23:
/usr/src/linux-headers-3.8.13-bone63/arch/armv7l/include/asm/timex.h:18:24: fata                                                                                l error: mach/timex.h: No such file or directory
 #include <mach/timex.h>
                        ^
compilation terminated.
make[2]: *** [/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_linux_v4.                                                                                0.2_9000.20130911/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/ubuntu/822n_drv_wireless/driver/rtl8188C_8192C_usb_l                                                                                inux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.13-bone63'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```
Please help me to solve my problem, Much appreciated!!

Thanks so much!

---

### Post by varunendra on 2014-10-05
We would like to see "all things" you have done. Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by john303 on 2014-10-05
Nothing in this file, please ask me more, thanks you

result is below
```
root@arm:/home/ubuntu# wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-08-13 16:52:50--  https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 107.21.240.145
Connecting to dl.dropbox.com (dl.dropbox.com)|107.21.240.145|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script [following]
--2014-08-13 16:52:51--  https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 107.22.231.12, 107.20.187.173, 23.21.244.13, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.22.231.12|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15618 (15K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-08-13 16:52:53--  https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script
Reusing existing connection to dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 15618 (15K) [text/plain]
Saving to: ‘wireless_script’

100%[======================================================================================================================>] 15,618      --.-K/s   in 0.001s

2014-08-13 16:52:53 (18.1 MB/s) - ‘wireless_script’ saved [15618/15618]

        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****

  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.

  (Type your Login Password when asked, then press 'Enter')

ubuntu
sed: -e expression #1, char 1: unknown command: `S'


    ########################################################################

    DONE! All results saved in -

                 File Name:     "wireless-info.txt"
                 Directory:     "/home/ubuntu"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################


```

---

### Post by john303 on 2014-10-05
Dear expert,
I'm a newbie in linux, I want to use this module as a access point for Beaglebone Black run on **ubuntu 14.04**, I have read many thread to install driver, but this module can not blink led (active) Although I have done step without error.
my bone is ```
root@arm:/home/ubuntu/822n_drv_wireless# uname -r
3.8.13-bone63
```

I hope someone help me.
I will show any code. Plz require me.
Thanks in advance!

---

### Post by Vladlenin5000 on 2014-10-05
Please don't open multiple thread for the same issue. It dilutes community effort.
Please upload the contents of wireless-info.txt or the file itself as an attachment. What you posted is useless.
Please don't bump your thread each hour and wait for the person already helping you. Varunendra, by the way, lives in India, probably several time zones distant from you.

---

### Post by howefield on 2014-10-05
Duplicate threads merged.

---

### Post by john303 on 2014-10-05
Thank you, Sorry for my impatience. I will wait. wireless-info.txt is empty file.

---

### Post by john303 on 2014-10-05
Sorry for my impatience, wireless-info.txt is empty file so I can not post in here. Please help me to find my error. Thanks!

---

### Post by praseodym on 2014-10-05
Please show the outputs of these commands:
```

lsusb
lsmod
dmesg | grep 8192
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by john303 on 2014-10-05
Here is my result:
```
root@arm:/home/ubuntu# lsusb
Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n W                                                                                LAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@arm:/home/ubuntu# lsusb
Bus 001 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n W                                                                                LAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@arm:/home/ubuntu# lsmod
Module                  Size  Used by
g_multi                51145  0
libcomposite           14931  1 g_multi
8192cu                423774  0
root@arm:/home/ubuntu# dmesg | grep 8192
[    0.000000] PERCPU: Embedded 9 pages/cpu @c0d36000 s14080 r8192 d14592 u36864
[    0.000000] pcpu-alloc: s14080 r8192 d14592 u36864 alloc=9*4096
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.216859] TCP bind hash table entries: 4096 (order: 4, 81920 bytes)
[    6.697461] rtl8192cu 1-1:1.0: usb_probe_interface
[    6.697490] rtl8192cu 1-1:1.0: usb_probe_interface - got id
[    8.555566] usbcore: registered new interface driver rtl8192cu
[ 1513.769621] rtl8192cu 1-1:1.0: usb_probe_interface
[ 1513.769668] rtl8192cu 1-1:1.0: usb_probe_interface - got id
root@arm:/home/ubuntu# iwconfig
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

root@arm:/home/ubuntu# rfkill list
bash: rfkill: command not found
root@arm:/home/ubuntu# iwlist chan
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

lo        no frequency information.

eth0      no frequency information.

usb0      no frequency information.

root@arm:/home/ubuntu# sudo iwlist scan
wlan0     No scan results

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

root@arm:/home/ubuntu# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
domain localdomain
search localdomain
nameserver 192.168.137.1
root@arm:/home/ubuntu# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.137.5
netmask 255.255.255.0
network 192.168.137.0
broadcast 192.168.137.255
gateway 192.168.137.1
# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE

# The secondary network interface
#auto eth1
#iface eth1 inet dhcp

# WiFi Example
#auto wlan0
#iface wlan0 inet dhcp
#    wpa-ssid "essid"
#    wpa-psk  "password"

# Ethernet/RNDIS gadget (g_ether)
# ... or on host side, usbnet and random hwaddr
# Note on some boards, usb0 is automaticly setup with an init script
iface usb0 inet static
    address 192.168.7.2
    netmask 255.255.255.0
    network 192.168.7.0
    gateway 192.168.7.1
root@arm:/home/ubuntu#


```
Thank you so much !

---

### Post by praseodym on 2014-10-05
The interface name is wlan0, not usb0, so change the "interfaces"

---

### Post by john303 on 2014-10-05
Thank you!

---

