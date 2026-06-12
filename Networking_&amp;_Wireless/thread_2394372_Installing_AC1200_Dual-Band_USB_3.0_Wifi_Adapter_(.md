---
title: "Installing AC1200 Dual-Band USB 3.0 Wifi Adapter (not A6210)"
date: 2018-06-15
forum: Networking &amp; Wireless
---

### Post by robertcull1 on 2018-06-15
For Ubuntu 16.04 LTS

Apparently this is not the model A6210 (it doesn't look like it):

[https://www.walmart.com/ip/1200Mbps-Wireless-USB-Wifi-Adapter-TSV-USB-Wifi-Adapter-AC1200-Dual-Band-2-4GHz-300Mbps-5GHz-867Mbps-802-11-ac-a-b-g-n-High-Gain-Antenna-Network-Lan-/304880124?wmlspartner=wlpa&selectedSellerId=2961&adid=22222222227142567661&wl0=&wl1=g&wl2=c&wl3=253387422689&wl4=pla-418327731308&wl5=9029967&wl6=&wl7=&wl8=&wl9=pla&wl10=113509951&wl11=online&wl12=304880124&wl13=&veh=sem](https://www.walmart.com/ip/1200Mbps-Wireless-USB-Wifi-Adapter-TSV-USB-Wifi-Adapter-AC1200-Dual-Band-2-4GHz-300Mbps-5GHz-867Mbps-802-11-ac-a-b-g-n-High-Gain-Antenna-Network-Lan-/304880124?wmlspartner=wlpa&selectedSellerId=2961&adid=22222222227142567661&wl0=&wl1=g&wl2=c&wl3=253387422689&wl4=pla-418327731308&wl5=9029967&wl6=&wl7=&wl8=&wl9=pla&wl10=113509951&wl11=online&wl12=304880124&wl13=&veh=sem)

```
$ lsusb
Bus 002 Device 002: ID 17ef:1004 Lenovo Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Comes with a CD with the following file structure:

```
Ver_BU1804
   RTL88x2BU_WiFi_linux_v5.1.7_1906
      MacOS10.9_MacOS10.18_Driver
         ...
      Windows_driver
         ...
      RTL88x2BU_WiFi_linux_v5.1.7_19806
         android_ref_codes_JB_4.2
            linux-3.0.42_STATION_INFO_ASSOC_REQ_IES.diff
            realtek_wifi_SDK_for_android_JB_4.2_20130208.tar.gz
            Realtek_WiFi_SDK_for_Android_JB_4.pdf
         android_ref_codes_KK.4.4
            linux-3.0.42_STATION_INFO_ASSOC_REQ_IES.diff
            realtek_wifi_SDK_for_android_KK_4.4_20140117.tar.gz
            Realtek_Wi-Fi_SDK_for_Android_KK_4.4.pdf
         android_ref_codes_L_5.x
            linux-3.0.42_STATION_INFO_ASSOC_REQ_IES.diff
            realtek_wifi_SDK_for_android_L_5.x_20150811.tgz
            Realtek_Wi-Fi_SDK_for_Android_L_5.pdf
         android_ref_codes_M_6.x
            linux-3.0.42_STATION_INFO_ASSOC_REQ_IES.diff
            realtek_wifi_SDK_for_android_L_6.x_20151116.tgz
            Realtek_Wi-Fi_SDK_for_Android_M_6.pdf
         btcoex
            script
               btcoex_lnx.sh
               btcoex_win.bat
            HowTo_debug_BT_coexistence.pdf
         document
            Driver_Configuration_for_RF_Regulatory_Certification.pdf
            How_to_append_vendor_specific_ie_to_driver_management_frames.pdf
            HowTo_enable_and_verify_TDLS_function_in_Wi-Fi_driver.pdf
            HowTo_enable_driver_to_support_80211d.pdf
            HowTo_enable_driver_to_support_WIFI_certification_test.pdf
            HowTo_enable_the_power_saving_functionalitiy.pdf
            How_to_set_driver_debug_log_level.pdf
            HowTo_support_more_VidPids.pdf
            linux_dhcp_server_notes.txt
            Miracast_for_Realtek_WiFi.pdf
            Quick_Start_Guide_for_Adaptivity_and_Sensing_Test.pdf
            Quick_Start_Guide_for_Bridge.pdf
            Quick_Start_Guide_for_Driver_Compilation_and_Installation.pdf
            Quick_Start_Guide_for_SoftAP.pdf
            Quick_Start_Guide_for_Station_Mode.pdf
            Quick_Start_Guide_for_WOW.pdf
            Realtek_WiFi_concurrent_mode_Introduction.pdf
            RTK_P2P_WFD_Programming_guide.pdf
            SoftAP_Mode_features.pdf
            Wireless_tools_porting_guide.pdf
            wpa_cli_with_wpa_supplicant.pdf
         driver
            rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333.tar.gz
         mp_tools
            RF_MP_tools
              HowTo_read_external_TX_power_related_file.pdf
              iwpriv_mp_settings_for_different_data_rate.xls
              ReadMe-RtkWiFiTest.txt
              Realtek_RF_MP_Tool_Guidelines_V19.pdf
              RtkWiFiTest_V1.2_20160104.apk
              rtwpriv_v2_20151130.zip
              wireless_tools_android.tar.gz
         WiFi_Direct_User_Interface
            Android.mk
            install.sh
            p2p_api_test_linux.c
            p2p_test.h
            p2p_ui_test_linux.c
            Start_Guide_P2P_User_Interface_Linux.pdf
         wireless_tools
            wireless_tools.30.rtl.tar.gz
         wpa_supplicant_hostapd
            p2p_hostapd.conf
            rtl_hostapd_2G.conf
            rtl_hostapd_5G.conf
            wpa_0_8.conf
            wpa_supplicant_8_jb_4.2_rt2_r16451.20151224.tar.gz
            wpa_supplicant_8_kk_4.4_rtw_r16450.20151224.tar.gz
            wpa_supplicant_8_L_5.x_rtw_r16058.20151224.tar.gz
            wpa_supplicant_8_M_6.x_rtw_r17190.20160415.tar.gz
            wpa_supplicant_hostapd-0.8_rtw_r7475.20130812.tar.gz
         install.sh
         readme.txt
         ReleaseNotes.pdf
```

From RealeaseNotes.pdf
   Product:  RTL88x2B USB Software Package - Linux Driver
   Version:  v5.1.7_19806_20161025_BTCOEX20161014-3333

The advertisement says it has a Rtl8812 chip

---

### Post by robertcull1 on 2018-06-15
Some attachments.

---

### Post by jeremy31 on 2018-06-15
Moved to Network and Wireless

---

### Post by praseodym on 2018-06-16
RTL8812bu chipset

[https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613)

---

### Post by robertcull1 on 2018-06-16
Hi. Thanks for getting back to me.

Here's a newer version that I got from the page of that link:

[https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044)

I am a noob to github and I have no idea where to start. Can you give me a hint how to take it from there?

---

### Post by chili555 on 2018-06-16
> I am a noob to github and I have no idea where to start. Can you give me a hint how to take it from there?We were all noobs at one time, even Linus  Torvalds and even old Chili!

With a working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:

```
sudo apt-get update
sudo apt-get install build-essential git
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044.git
cd rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044
VER=$(cat ./version)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```You may safely copy and paste each command, one at a time,  from this reply right into the terminal.

You should be all set.

---

### Post by robertcull1 on 2018-06-16
Thanks for the encouragement.

There may have been some trouble with the last two commands:

robert@T61n2:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo dkms build -m rtl88x2bu -v ${VER}
Module rtl88x2bu/5.2.4.4 already built for kernel 4.4.0-128-generic/4
robert@T61n2:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo modprobe 88x2bu
modprobe: FATAL: Module 88x2bu not found in directory /lib/modules/4.4.0-128-generic

The adapter is still not presenting me with any networks to connect to.

---

### Post by robertcull1 on 2018-06-16
I tried the last two commands with the adapter plugged in:

```
robert@T61n2:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo dkms install -m rtl88x2bu -v ${VER}

88x2bu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-128-generic/updates/dkms/

depmod..........

DKMS: install completed.
robert@T61n2:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo modprobe 88x2bu
robert@T61n2:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ 
```

Still I am not presented with any networks to connect to.

---

### Post by robertcull1 on 2018-06-16
For some reason after about 5 minutes I was presented with networks to connect to. Now it works.

Thanks guys!

---

### Post by chili555 on 2018-06-16
Awesome! Glad it’s working. Have fun.

---

### Post by cmhk on 2018-10-23
pi@raspberrypi:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044 $ sudo dkms build -m rtl88x2bu -v ${VER}
Error! echo
Your kernel headers for kernel 4.14.71-v7+ cannot be found at
/lib/modules/4.14.71-v7+/build or /lib/modules/4.14.71-v7+/source.

pi@raspberrypi:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044 $ sudo dkms install -m rtl88x2bu -v ${VER}
Error! echo
Your kernel headers for kernel 4.14.71-v7+ cannot be found at
/lib/modules/4.14.71-v7+/build or /lib/modules/4.14.71-v7+/source.



Hi, i come to this part but i get that error. im new to this so i dont know what to do. can someone help?

---

### Post by chili555 on 2018-10-23
> **cmhk said:**
> pi@raspberrypi:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044 $ sudo dkms build -m rtl88x2bu -v ${VER}
Error! echo
Your kernel headers for kernel 4.14.71-v7+ cannot be found at
/lib/modules/4.14.71-v7+/build or /lib/modules/4.14.71-v7+/source.

pi@raspberrypi:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044 $ sudo dkms install -m rtl88x2bu -v ${VER}
Error! echo
Your kernel headers for kernel 4.14.71-v7+ cannot be found at
/lib/modules/4.14.71-v7+/build or /lib/modules/4.14.71-v7+/source.



Hi, i come to this part but i get that error. im new to this so i dont know what to do. can someone help?It appears that you are running Raspbian or some such, not a standard Ubuntu kernel. You should look for and install linux-headers for 4.14.71-v7 and try again. We are not familiar with Raspbian so we can&#8217;t advise you further.

---

### Post by him610 on 2018-10-23
Link to Raspberry Pi forums....[https://www.raspberrypi.org/forums/index.php]("https://www.raspberrypi.org/forums/index.php")

---

### Post by sdp123 on 2018-11-01
Very- very - much appreciated! Thank you. Worked perfectly :)

---

### Post by sdp123 on 2018-11-01
Thank you very -very - much! Worked great :)

---

### Post by cslice21 on 2018-12-20
Sorry for reviving the thread but as I proceeded with the instructions above I ran into this and can't get past it:


> Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.18.0-13-generic KVER=4.18.0-13-generic........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.2.4.4 not found
Error! Bad return status for module build on kernel: 4.18.0-13-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.



Any help? Thanks!

---

### Post by chili555 on 2018-12-22
> **cslice21 said:**
> Sorry for reviving the thread but as I proceeded with the instructions above I ran into this and can't get past it:




Any help? Thanks!I suggest that we do exactly what it suggests:> 
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.

Please run:```
cat  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log 
```Post the result and we'll likely see what went wrong.

---

### Post by williamvm on 2019-01-07
thank you very :KS much Chili555 these steps enabled wifi for my Eminent 4536 adapter on Ubuntu 18.04 on AMD Kabini server.
i did get dkms: command not found, so needed to install dkms first. thanks again

---

### Post by the-silence on 2019-01-12
> **chili555 said:**
> We were all noobs at one time, even Linus  Torvalds and even old Chili!

With a working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:

```
sudo apt-get update
sudo apt-get install build-essential git
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044.git
cd rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044
VER=$(cat ./version)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```You may safely copy and paste each command, one at a time,  from this reply right into the terminal.

You should be all set.

The above was super helpful!  Thank you!

---

### Post by muldengold on 2019-02-07
> **chili555 said:**
> I suggest that we do exactly what it suggests:Please run:```
cat  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log 
```Post the result and we'll likely see what went wrong.

I have the same error:

tyrion@tyrion-desktop:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo dkms build -m rtl88x2bu -v ${VER}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.18.0-14-generic KVER=4.18.0-14-generic..........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.2.4.4 not found
Error! Bad return status for module build on kernel: 4.18.0-14-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.


Here is my output:

DKMS make.log for rtl88x2bu-5.2.4.4 for kernel 4.18.0-14-generic (x86_64)
Do 7. Feb 19:54:26 CET 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-14-generic/build M=/var/lib/dkms/rtl88x2bu/5.2.4.4/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-14-generic'
Makefile:970: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mi.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/usb_intf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/usb_ops_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/wifi_regd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_android.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_proc.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_mp.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_intf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_com.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_com_phycfg.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_phy.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_dm.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_btcoex.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_mp.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_mcc.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/led/hal_usb_led.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_halmac.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/rtl8822b/rtl8822b_halinit.o
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c: In function ‘usb_init_recv_priv’:
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c:28:8: error: cast between incompatible function types from ‘void (*)(void *)’ to ‘void (*)(long unsigned int)’ [-Werror=cast-function-type]
        (void(*)(unsigned long))usb_recv_tasklet,
        ^
cc1: all warnings being treated as errors
make[2]: *** [scripts/Makefile.build:325: /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1534: _module_/var/lib/dkms/rtl88x2bu/5.2.4.4/build] Error 2


Thanks in advance!

---

### Post by chili555 on 2019-02-07
> **muldengold said:**
> I have the same error:

tyrion@tyrion-desktop:~/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044$ sudo dkms build -m rtl88x2bu -v ${VER}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=4.18.0-14-generic KVER=4.18.0-14-generic..........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.2.4.4 not found
Error! Bad return status for module build on kernel: 4.18.0-14-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.


Here is my output:

DKMS make.log for rtl88x2bu-5.2.4.4 for kernel 4.18.0-14-generic (x86_64)
Do 7. Feb 19:54:26 CET 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-14-generic/build M=/var/lib/dkms/rtl88x2bu/5.2.4.4/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-14-generic'
Makefile:970: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_security.o
      <snip>
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_halmac.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/rtl8822b/rtl8822b_halinit.o
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c: In function ‘usb_init_recv_priv’:
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c:28:8: error: cast between incompatible function types from ‘void (*)(void *)’ to ‘void (*)(long unsigned int)’ [-Werror=cast-function-type]
        (void(*)(unsigned long))usb_recv_tasklet,
        ^
cc1: all warnings being treated as errors
make[2]: *** [scripts/Makefile.build:325: /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1534: _module_/var/lib/dkms/rtl88x2bu/5.2.4.4/build] Error 2


Thanks in advance!Please try this package instead. It 'makes' on my 18.10 system with a few possibly harmless warnings.

[https://github.com/EntropicEffect/rtl8822bu](https://github.com/EntropicEffect/rtl8822bu)

If you need additional guidance or a step-by-step, post back.

---

### Post by muldengold on 2019-02-08
yes, a step-by-step guidance would be helpful.

Thanks, your help is much appreciated!

---

### Post by chili555 on 2019-02-08
> **muldengold said:**
> yes, a step-by-step guidance would be helpful.

Thanks, your help is much appreciated!From the terminal and with a temporary working internet connection, do:```
sudo apt update
sudo apt install -y git
git clone https://github.com/EntropicEffect/rtl8822bu.git
cd rtl8822bu
make
sudo make install
sudo modprobe 88x2bu
```
I will have an additional step, but first tell us how it goes so far.

---

### Post by muldengold on 2019-02-08
Thanks a thousand times -  you made my day! It works like charme. Great! 

P.S. and greetings to Dr.Cooper - she's right!

---

### Post by chili555 on 2019-02-08
> **muldengold said:**
> Thanks a thousand times -  you made my day! It works like charme. Great! 

P.S. and greetings to Dr.Cooper - she's right!One more thing; when Update Manager offers a newer kernel version, known as linux-image, you must recompile after the requested reboot:```

cd rtl8822bu
make clean
git pull
make
sudo make install
sudo modprobe 88x2bu

```Please retain the file and these instructions for that time.

Have fun!

---

### Post by muldengold on 2019-02-08
Cheers!

---

### Post by alexyaronyc2 on 2019-02-09
I am having a similar issue....

DKMS make.log for rtl88x2bu-5.2.4.4 for kernel 4.18.0-15-generic (x86_64)
Sat Feb  9 13:47:46 EST 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-15-generic/build M=/var/lib/dkms/rtl88x2bu/5.2.4.4/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-15-generic'
Makefile:970: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_mi.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/usb_intf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/usb_ops_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/wifi_regd.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_android.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/rtw_proc.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/os_dep/linux/ioctl_mp.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_intf.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_com.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_com_phycfg.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_phy.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_dm.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_btcoex_wifionly.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_btcoex.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_mp.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_mcc.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/led/hal_usb_led.o
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c: In function ‘usb_init_recv_priv’:
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c:28:8: error: cast between incompatible function types from ‘void (*)(void *)’ to ‘void (*)(long unsigned int)’ [-Werror=cast-function-type]
        (void(*)(unsigned long))usb_recv_tasklet,
        ^
cc1: all warnings being treated as errors
make[2]: *** [scripts/Makefile.build:325: /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1534: _module_/var/lib/dkms/rtl88x2bu/5.2.4.4/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-15-generic'
make: *** [Makefile:1794: modules] Error 2

---

### Post by chili555 on 2019-02-09
> **alexyaronyc2 said:**
> I am having a similar issue....

DKMS make.log for rtl88x2bu-5.2.4.4 for kernel 4.18.0-15-generic (x86_64)
Sat Feb  9 13:47:46 EST 2019
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-15-generic/build M=/var/lib/dkms/rtl88x2bu/5.2.4.4/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-15-generic'
Makefile:970: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl88x2bu/5.2.4.4/build/core/rtw_security.o
  <snip>
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c: In function ‘usb_init_recv_priv’:
/var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.c:28:8: error: cast between incompatible function types from ‘void (*)(void *)’ to ‘void (*)(long unsigned int)’ [-Werror=cast-function-type]
        (void(*)(unsigned long))usb_recv_tasklet,
        ^
cc1: all warnings being treated as errors
make[2]: *** [scripts/Makefile.build:325: /var/lib/dkms/rtl88x2bu/5.2.4.4/build/hal/hal_hci/hal_usb.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1534: _module_/var/lib/dkms/rtl88x2bu/5.2.4.4/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-15-generic'
make: *** [Makefile:1794: modules] Error 2Please try instead the procedure I outlined above in post #23.

---

### Post by gwevans22 on 2019-02-10
Joined the forum (noob) just to add my thanks to Chilli for his patience and persistence.  This thread FINALLY got my rtl88x2BU device running, (LinuxLite 4.15 kernel).  Albeit I have to (hardware switch) turn off the internal IBM 802.11b IBM chip in the old Sony VAIO I'm using - which also kills the internal Bluetooth device.   A small price to pay for much increased wireless speeds !
Thanks again, Chilli.

---

### Post by chili555 on 2019-02-10
> **gwevans22 said:**
> Joined the forum (noob) just to add my thanks to Chilli for his patience and persistence.  This thread FINALLY got my rtl88x2BU device running, (LinuxLite 4.15 kernel).  Albeit I have to (hardware switch) turn off the internal IBM 802.11b IBM chip in the old Sony VAIO I'm using - which also kills the internal Bluetooth device.   A small price to pay for much increased wireless speeds !
Thanks again, Chilli.You could certainly blacklist the driver for the internal and not have to use the switch.

---

### Post by praseodym on 2019-02-10
Or use an udev rule:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Add these lines

```

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

SUBSYSTEM=="net", KERNEL=="[COLOR="#FF0000"]wlan1[/COLOR]", RUN+="/sbin/modprobe -rf [COLOR="#00FF00"]ipw2200[/COLOR]"

GOTO="rules_end"

LABEL="onboard_load"

SUBSYSTEM=="net", KERNEL=="[COLOR="#FF0000"]wlan*[/COLOR]", RUN+="/sbin/modprobe [COLOR="#00FF00"]ipw2200[/COLOR]"

LABEL="rules_end"
```
Replace the red entries with your wireless interface name, and the greenish ones with your internal wifi card module name. Proofread carefully and reboot. This should unload the internal driver when the stick is plugged in

---

### Post by bohicaman on 2019-03-07
I tried the code above and got several errors. ie: couldn't find files
Bob

---

### Post by chili555 on 2019-03-07
> **bohicaman said:**
> I tried the code above and got several errors. ie: couldn't find files
Bob
Please start a new thread and include the exact errors. Also include the details of the device from the terminal command:

```
lsusb
```

---

### Post by joselitux on 2019-03-10
Hi

followed instructions on post #23 worked like a charm, but I must run it every time I reboot.
How to make it permanent?

(ubuntu cosmic cuttlefish)

---

### Post by jeremy31 on 2019-03-10
Are you trying Ubuntu without installing it to hard drive?

---

### Post by joselitux on 2019-03-11
Solved after connecting to a wireless signal and rebooting. Seems that is needed to connect to any wifi source to be permanent

---

### Post by jurito on 2019-06-18
I just reinstalled ubuntu after a long hyatus, wifi didn't work. Found this thread and still couldn't manage to make it work, with a dell laptop and an amazon decent wifi dongle. Seriously, in 2019 i thought linux, or at least the more popular distros, were consumer ready. Sadly, they're not. Back in another 10 yrs.

---

### Post by chili555 on 2019-06-18
> **jurito said:**
> I just reinstalled ubuntu after a long hyatus, wifi didn't work. Found this thread and still couldn't manage to make it work, with a dell laptop and an amazon decent wifi dongle. Seriously, in 2019 i thought linux, or at least the more popular distros, were consumer ready. Sadly, they're not. Back in another 10 yrs.I don't think you should necessarily blame Ubuntu. The manufacturers of wireless devices are in an arms race to develop faster, and yet cheaper devices. They produce a Windows driver and ship the devices to the retailers. Most do not provide any Linux driver. 

There are many USB wireless devices that work out of the box. Ubuntu is pretty consumer ready but is not yet all things to all people all the time.

---

### Post by jurito on 2019-06-18
Actually, I'm quite sad about it. I had expectations and even just posting in an year old thread marked as solved, while the latest ubuntu ISO still don't work makes me sad. I tried but it's embarrassing, even as a non computer illiterate this is far too much a time waste.

---

### Post by coffeecat on 2019-06-18
Old solved thread closed to prevent further hijack-necromancies.

If anyone needs help with a wireless device, please start your own fresh thread, not forgetting to post the output of the wireless script as described here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

A reminder - this is a support section of the forum, a place to get help, not for posting vague complaints.

---

