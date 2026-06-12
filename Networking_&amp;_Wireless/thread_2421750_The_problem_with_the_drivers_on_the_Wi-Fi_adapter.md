---
title: "The problem with the drivers on the Wi-Fi adapter"
date: 2019-06-26
forum: Networking &amp; Wireless
---

### Post by d68088328 on 2019-06-26
I used these codes. But it all works before rebooting.Can you help with a problem?
lsusb show this >  

Bus 001 Device 002: ID 0bda:f179 Realtek Semiconductor Corp. 
Couldn't open device, some information will be missing
Device Descriptor:




> 
sudo apt-get install git build-essential
git clone git://github.com/ulli-kroll/rtl8188fu
cd rtl8188fu
make
sudo make installfw
sudo modprobe cfg80211
sudo insmod rtl8188fu.ko
> 
sudo depmod -a
sudo update-initramfs -u

---

### Post by chili555 on 2019-06-26
That's a slightly flawed process. Please try this:```
cd rtl8188fu
make clean
git pull
sudo make installfw
**sudo make install**
sudo **modprobe** rtl8188fu
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by d68088328 on 2019-06-27
shows an error at this place
**sudo make install**> 
install -p -m 644 .ko  /lib/modules/4.15.0-52-generic/kernel/drivers/net/wireless/
install: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; '.ko': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
Makefile:445: recipe for target 'install' failed
make: *** [install] Error 1




---

### Post by chili555 on 2019-06-27
Oops! I made a mistake. I apologize for my mis-step. Please try:

```
cd rtl8188fu
make clean
git pull
**make**
sudo make installfw
sudo make install
sudo modprobe rtl8188fu
sudo depmod -a
sudo update-initramfs -u
```Please try again.

---

### Post by d68088328 on 2019-06-27
same mistake on that spot

> 

zhaksidos@AOD257:~/rtl8188fu$ sudo make install
install -p -m 644 .ko  /lib/mo dules/4.15.0-52-generic/kernel/drivers/net/wireless/
install: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; '.ko': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
Makefile:445: recipe for target 'install' failed
make: *** [install] Error 1





---

### Post by chili555 on 2019-06-27
Please show me the exact result of:```
make clean
git pull
make
```Thanks.

---

### Post by d68088328 on 2019-06-27
here is the result```


zhaksidos@AOD257:~/rtl8188fu$ make clean
cd hal/phydm/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/phydm/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
zhaksidos@AOD257:~/rtl8188fu$ git pull
&#1059;&#1078;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
zhaksidos@AOD257:~/rtl8188fu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-52-generic/build M=/home/zhaksidos/rtl8188fu  modules
make[1]: &#1074;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; «/usr/src/linux-headers-4.15.0-52-generic»
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_cmd.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_security.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_debug.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_io.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_ioctl_query.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_ioctl_set.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_ieee80211.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_mlme.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_mlme_ext.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_wlan_util.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_vht.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_pwrctrl.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_rf.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_recv.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_sta_mgt.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_ap.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_xmit.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_p2p.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_tdls.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_br_ext.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_iol.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_sreset.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_beamforming.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_odm.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/efuse/rtw_efuse.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/osdep_service.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/os_intfs.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/usb_intf.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/ioctl_linux.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/xmit_linux.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/mlme_linux.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/recv_linux.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/zhaksidos/rtl8188fu/os_dep/linux/wifi_regd.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_intf.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_com.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_com_phycfg.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_phy.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_dm.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_mp.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/hal_hci/hal_usb.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/led/hal_usb_led.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/HalPwrSeqCmd.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/Hal8188FPwrSeq.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_sreset.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_hal_init.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_phycfg.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_rf6052.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_dm.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_rxdesc.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/rtl8188f_cmd.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/usb/usb_halinit.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/usb/rtl8188fu_led.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/usb/rtl8188fu_xmit.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/usb/rtl8188fu_recv.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/rtl8188f/usb/usb_ops.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/efuse/rtl8188f/HalEfuseMask8188F_USB.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_debug.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_antdiv.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_antdect.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_interface.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_hwconfig.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/halphyrf_ce.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_edcaturbocheck.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_dig.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_pathdiv.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_rainfo.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_dynamicbbpowersaving.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_powertracking_ce.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_dynamictxpower.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_adaptivity.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_cfotracking.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_noisemonitor.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_acs.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/phydm_beamforming.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/txbf/halcomtxbf.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/txbf/haltxbfinterface.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/halhwimg8188f_bb.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/halhwimg8188f_mac.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/halhwimg8188f_rf.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/halhwimg8188f_fw.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/phydm_regconfig8188f.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/halphyrf_8188f.o
  CC [M]  /home/zhaksidos/rtl8188fu/hal/phydm/rtl8188f/phydm_rtl8188f.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_mp.o
  CC [M]  /home/zhaksidos/rtl8188fu/core/rtw_mp_ioctl.o
  LD [M]  /home/zhaksidos/rtl8188fu/rtl8188fu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/zhaksidos/rtl8188fu/rtl8188fu.mod.o
  LD [M]  /home/zhaksidos/rtl8188fu/rtl8188fu.ko
make[1]: &#1074;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; «/usr/src/linux-headers-4.15.0-52-generic»



```

---

### Post by chili555 on 2019-06-27
The previous error was (Google translate):> 
failed to execute stat for '.ko': No such file or directory
The .ko file exists now: > 
MODPOST 1 modules
CC /home/zhaksidos/rtl8188fu/rtl8188fu.mod.o
LD [M] /home/zhaksidos/rtl8188fu/[COLOR="#FF0000"]rtl8188fu.ko[/COLOR]
Now does:```
sudo make install
```...succeed or fail?

For your information and that of the searchers, the Makefile has an 'install' section:> 
install:
	install -p -m 644 $(MODULE_NAME).ko  $(MODDESTDIR)
	/sbin/depmod -a ${KVER}

It appears correct to me.

---

### Post by chili555 on 2019-06-27
I don't understand completely why the Makefile is not working correctly. Please try this:

```
cd rtl8188fu
gedit Makefile
```gedit shows line numbers. Scroll down to line 445 and change this line:> 
install -p -m 644 $(MODULE_NAME).ko  $(MODDESTDIR)
To read:> 
install -p -m 644 rtl8188fu.ko  $(MODDESTDIR)
Please be very careful about spacing and indentation. It must be perfect. When you have proofread, save the change and exit gedit. Now run:```

sudo make install.
sudo modprobe rtl8188fu

```Please post any errors or warnings.

---

### Post by d68088328 on 2019-06-27
Problem solved!
that's what i do
> 
[COLOR=#000000][FONT=-apple-system]git clone git://[/FONT][/COLOR][github.com/ulli-kroll/rtl8188fu]("https://vk.com/away.php?to=http%3A%2F%2Fgithub.com%2Fulli-kroll%2Frtl8188fu&cc_key=")
[COLOR=#000000][FONT=-apple-system]cd rtl8188fu
[/FONT][/COLOR][COLOR=#000000][FONT=-apple-system]make 
[/FONT][/COLOR][COLOR=#000000][FONT=-apple-system]gedit Makefile
[/FONT][/COLOR][FONT=-apple-system][COLOR=#000000]*[/COLOR][/FONT]here 445 line changes to ''install -p -m 644 rtl8188fu.ko $(MODDESTDIR)''*
sudo make install
sudo modprobe rtl8188fu



thank you bro and have a nice day to you

---

### Post by chili555 on 2019-06-27
Awesome! I'm glad it's working.

Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

