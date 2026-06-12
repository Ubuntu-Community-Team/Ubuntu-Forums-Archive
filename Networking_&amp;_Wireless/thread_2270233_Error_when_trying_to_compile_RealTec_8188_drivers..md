---
title: "Error when trying to compile RealTec 8188 drivers..."
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by kananesgi on 2015-03-21
I am having some troubles here. I recently installed lubuntu on a Gateway 6456 that originally had Windows 7 Ultimate. The computer would not run with Win 7, so I made the decision to blank the HD and install lubuntu. After that, the Marvell TopDog wifi adapter would not work (made a thread about that with no responses). I went ahead and purchased a usb wifi adapter with native Linux support (Cnet CQU-906) yesterday and thought it fixed the problem. Plugged it in and immediately found my wifi signal, connected, went online, everything seemed to be working.

Last night, while trying to get a windows program to install, I kept running into problems. The internet would simply stop at random times. I don't mean it would disconnect from the network, it would simply stop sending or receiving anything. The data transfer rate would drop to zero. I thought it was my wifi, since I have a similar problem with my Windows machine from time to time (my wifi is provided by my cell phone's hotspot feature, and the phone is a piece of crap). However, I determined that was not the problem here because the Windows system is still working without a problem. The lubuntu system, on the other hand, has spotty at best internet access. It connects to the hotspot without issue, and works great for about a minute, then the data drops to zero. Most of the time it'll come back after a bit (30 sec - 3 or 4 min) and work again for maybe 30 seconds to a minute, then drop again. It might do this cycle 4 or 5 times before it finally "gives up the ghost" and won't come back at all, until I take out the adapter and put it back in again. That starts the whole cycle over again. It seems to be getting worse, too. At first, it would work for several minutes before dropping, and would only drop for a few seconds, then come back. Now, I'm lucky to get 20 or 30 seconds out of it before dropping and it's sometimes a question if it's ever going to come back.

Doing some research on my own, I've found others having problems with the wifi chip that is in this adapter (the Realtek rtl8188cus). Most say they a loosing internet or the internet continually "drops." I don't know if they mean it disconnects from the network or if they mean what I'm having - no data transfer. At any rate, I decided to try one of those fixes, which was to blacklist the native drivers and install those provided by RealTec specifically for this chip. However, I am running into a problem trying to compile the new drivers. I don't know what the problem is. I had several problems to start out that were a result of missing packages (things like make and gcc - I'm new to linux). I think I got all the required packages installed, but not sure.

Here is the output from the compiler after I got make and gcc installed:
```
##################################################Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/autoconf_rtl8712_usb_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/clean
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/config
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ifcfg-wlan0
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/autoconf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/basic_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/big_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/generic.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/little_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swab.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swabb.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/circ_buf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/cmd_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_conf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ethernet.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/farray.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/h2clbk.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/hal_init.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/if_ether.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ioctl_cfg80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ip.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mlme_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mp_custom_oid.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/nic_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_ce_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_intf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/recv_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_efuse.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/vssver.scc
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_byteorder.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_debug.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_eeprom.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ht.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_io.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_query.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_rtl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_set.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_led.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_phy_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_pwrctrl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_qos.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_security.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_sme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtw_android.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sta_info.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_vendor_req.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/version.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wlan_bssdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/xmit_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Kconfig
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Makefile
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/rtw_android.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/rtl871x_pwrctrl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl8712_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl871x_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl8712_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl871x_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/runwpa
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/rtl871x_sta_mgt.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wlan0dhcp
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wpa1.conf
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl8712_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl871x_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.16.0-30-generic/build M=/home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-30-generic'
  CC [M]  /home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from /home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:23:0:
/home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h:393:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
  daemonize("%s", "RTKTHREAD");
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/cdp/Desktop/rtl8188/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-30-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

I'm not much of a programmer. Any help would be appreciated.

---

### Post by kananesgi on 2015-03-21
OK, I just noticed on another post something about having a kernel that is too new for the driver...could that be the problem? I'm running lubuntu 14.04 LTS, and the driver is dated 5-15-2012 on Realtek's site.

---

### Post by jeremy31 on 2015-03-21
> **kananesgi said:**
> OK, I just noticed on another post something about having a kernel that is too new for the driver...could that be the problem? I'm running lubuntu 14.04 LTS, and the driver is dated 5-15-2012 on Realtek's site.

Can you post the results from ```
lshw -c net
```

---

### Post by kananesgi on 2015-03-21
```
  *-network                      description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:e0:b8:d3:ba:52
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8362e [TopDog] 802.11a/b/g/n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0310000-c031ffff memory:c0300000-c030ffff



```

There you go...

---

### Post by jeremy31 on 2015-03-21
The pvaret driver might work for that.  [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)
Instructions for install
```
sudo apt-get install linux-headers-generic build-essential dkms git
```
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
```
```
sudo dkms add ./rtl8192cu-fixes
```
```
sudo dkms install 8192cu/1.9
```
```
sudo depmod -a
```
```
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
```

Reboot

---

### Post by kananesgi on 2015-03-21
apt-git requires internet connection, doesn't it? I don't have a way to connect ethernet to it, so any downloading has to be done on the windows system and transferred to the linux box via a usb drive.

---

### Post by kananesgi on 2015-03-21
Actually, I'm at my brother's place so I might be able to get ethernet...

EDIT: WooHoo, I have ethernet access here, so that'll make this go a lot faster.

---

### Post by jeremy31 on 2015-03-21
You might just need ```
sudo apt-get install linux-firmware
``` to get it running without the pvaret fix

---

### Post by kananesgi on 2015-03-21
ok, managed to do everything you said. The last two commands did not return any output. I think the last one was redundent as I had already blacklisted the native drivers.

Seems to be working at the moment. Might take a while to see if it still has problems. Yesterday, it seemed to work for a while, then rather quickly started giving problems. We'll see. Fingers crossed.

Thanks for the help.

---

### Post by kananesgi on 2015-03-21
Well, after some time now, it seems to be working still. I think we fixed it :p. Thanks a lot.

---

### Post by jeremy31 on 2015-03-21
> **kananesgi said:**
> Well, after some time now, it seems to be working still. I think we fixed it :p. Thanks a lot.

Feel free to use forum tools or thread tools at the top of this page to mark as Solved

---

