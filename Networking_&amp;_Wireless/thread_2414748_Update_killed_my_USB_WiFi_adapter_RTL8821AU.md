---
title: "Update killed my USB WiFi adapter RTL8821AU"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by richyg on 2019-03-14
Linux noob here. I had previously followed [this thread]("https://ubuntuforums.org/showthread.php?t=2339960") to get the drivers installed and working, I think possibly from this source [https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)

AFAIK I didn't have it set to update automatically after a new linux kernel update (through dkmks?) so after the update my WiFi is no longer recognised.

As per advice here is my wireless-info.txt [http://paste.ubuntu.com/p/7PYCBkPVB3/](http://paste.ubuntu.com/p/7PYCBkPVB3/)

Hoping this will be an easy fix and maybe to have the driver working after another such update without having to sort it manually.

Thanks in advance.

---

### Post by chili555 on 2019-03-14
Please run and post:```
sudo dkms status
```I suspect that the dkms rebuild process went wrong.

---

### Post by richyg on 2019-03-15
Thanks for your help.

result:
```
rtl8812AU, #MODULE_VERSION#: added
```

I know that looks wrong, probably as a result of me tinkering away trying to sort this myself rather than asking for help. :roll:

FYI the downloaded files for the driver (from github I presume) are located at /home/richard/rtl8812AU

Thanks

---

### Post by chili555 on 2019-03-15
Please run:```
sudo dkms remove rtl8812AU/#MODULE_VERSION#
```And, assuming there is no error, warning, etc., show me:```
sudo dkms status
```I hope it returns a blank.

If there *is* a warning, error, etc., please post it.

---

### Post by richyg on 2019-03-16
error returned:

```
richard@richard-pc:~$ sudo dkms remove rtl8812AU/#MODULE_VERSION#
Error! Invalid number of parameters passed.
Usage: remove <module>/<module-version> --all
   or: remove <module>/<module-version> -k <kernel-version>


```

---

### Post by jeremy31 on 2019-03-16
```
sudo dkms remove rtl8812AU/#MODULE_VERSION# --all
```

I normally change some of the dkms.conf so that dkms can be used normally
```
PACKAGE_NAME="rtl8812AU"
PACKAGE_VERSION=1.0
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' KVER=${kernelver}"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"
```

Then I just do the ```
sudo dkms add ./rtl8812AU
sudo dkms install rtl8812AU/1.0
```

The instructions on the github site show
```
DRV_NAME=rtl8812AU
 DRV_VERSION=4.3.20
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
git archive driver-${DRV_VERSION} | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
```

---

### Post by richyg on 2019-03-16
UPDATE: OK so I managed to delete the folders manually from /var/lib/dkms/ and /usr/src

I should have waited for further instructions but I tried following the install commands from the Readme (carefully) but the WiFi is still not working after a reboot. Here is the transcript:
```
 richard@richard-pc:~$ sudo dkms remove rtl8812AU/#MODULE_VERSION#

 [sudo] password for richard:  
 Error! Invalid number of parameters passed.

 Usage: remove <module>/<module-version> --all

    or: remove <module>/<module-version> -k <kernel-version>
 rrichard@richard-pc:~$ cd /var/lib/dkms
 richard@richard-pc:/var/lib/dkms$ dir
 dkms_dbversion  rtl8812AU
 richard@richard-pc:/var/lib/dkms$ sudo rm -R rtl8812AU
 richard@richard-pc:/var/lib/dkms$ sudo dkms status
 richard@richard-pc:/var/lib/dkms$ cd
 richard@richard-pc:~$ cd rtl8812AU
 richard@richard-pc:~/rtl8812AU$ DRV_NAME=rtl8812AU
 richard@richard-pc:~/rtl8812AU$ DRV_VERSION=4.3.20
 richard@richard-pc:~/rtl8812AU$ sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
 richard@richard-pc:~/rtl8812AU$ git archive driver-${DRV_VERSION} | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
 richard@richard-pc:~/rtl8812AU$ sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 Creating symlink /var/lib/dkms/rtl8812AU/4.3.20/source ->
                  /usr/src/rtl8812AU-4.3.20
 
 
 DKMS: add completed.
 richard@richard-pc:~/rtl8812AU$ sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 Kernel preparation unnecessary for this kernel.  Skipping...
 
 
 Building module:
 cleaning build area...
 'make' KVER=4.18.0-16-generic......................................................
 cleaning build area...
 
 
 DKMS: build completed.
 richard@richard-pc:~/rtl8812AU$ sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 8812au:
 Running module version sanity check.
 
 
 Good news! Module version v4.3.20_16317.20160108 for 8812au.ko
 exactly matches what is already found in kernel 4.18.0-16-generic.
 DKMS will not replace this module.
 You may override by specifying --force.
 
 
 depmod......
 
 
 DKMS: install completed.
 richard@richard-pc:~/rtl8812AU$ sudo /sbin/depmod -a
  
```

dkms status now shows:
```
richard@richard-pc:~$ dkms status
rtl8812AU, 4.3.20, 4.18.0-16-generic, i686: installed (WARNING! Diff between built and installed module!)

```

sorry @jeremy31 I didn't see your post before trying the above

---

### Post by jeremy31 on 2019-03-16
> **richyg said:**
> UPDATE: OK so I managed to delete the folders manually from /var/lib/dkms/ and /usr/src

I should have waited for further instructions but I tried following the install commands from the Readme (carefully) but the WiFi is still not working after a reboot. Here is the transcript:
```
 richard@richard-pc:~$ sudo dkms remove rtl8812AU/#MODULE_VERSION#

 [sudo] password for richard:  
 Error! Invalid number of parameters passed.

 Usage: remove <module>/<module-version> --all

    or: remove <module>/<module-version> -k <kernel-version>
 rrichard@richard-pc:~$ cd /var/lib/dkms
 richard@richard-pc:/var/lib/dkms$ dir
 dkms_dbversion  rtl8812AU
 richard@richard-pc:/var/lib/dkms$ sudo rm -R rtl8812AU
 richard@richard-pc:/var/lib/dkms$ sudo dkms status
 richard@richard-pc:/var/lib/dkms$ cd
 richard@richard-pc:~$ cd rtl8812AU
 richard@richard-pc:~/rtl8812AU$ DRV_NAME=rtl8812AU
 richard@richard-pc:~/rtl8812AU$ DRV_VERSION=4.3.20
 richard@richard-pc:~/rtl8812AU$ sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
 richard@richard-pc:~/rtl8812AU$ git archive driver-${DRV_VERSION} | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
 richard@richard-pc:~/rtl8812AU$ sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 Creating symlink /var/lib/dkms/rtl8812AU/4.3.20/source ->
                  /usr/src/rtl8812AU-4.3.20
 
 
 DKMS: add completed.
 richard@richard-pc:~/rtl8812AU$ sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 Kernel preparation unnecessary for this kernel.  Skipping...
 
 
 Building module:
 cleaning build area...
 'make' KVER=4.18.0-16-generic......................................................
 cleaning build area...
 
 
 DKMS: build completed.
 richard@richard-pc:~/rtl8812AU$ sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
 
 
 8812au:
 Running module version sanity check.
 
 
 Good news! Module version v4.3.20_16317.20160108 for 8812au.ko
 exactly matches what is already found in kernel 4.18.0-16-generic.
 DKMS will not replace this module.
 You may override by specifying --force.
 
 
 depmod......
 
 
 DKMS: install completed.
 richard@richard-pc:~/rtl8812AU$ sudo /sbin/depmod -a
  
```

dkms status now shows:
```
richard@richard-pc:~$ dkms status
rtl8812AU, 4.3.20, 4.18.0-16-generic, i686: installed (WARNING! Diff between built and installed module!)

```

sorry @jeremy31 I didn't see your post before trying the above
That looks good, so reboot and post results for ```
modinfo 8812au
```
Hopefully it works

---

### Post by chili555 on 2019-03-16
Please post:```
lsusb
```And also:```
modinfo rtl8812au | grep alias
```

---

### Post by richyg on 2019-03-18
Okay here are results from the commands in the two posts above. The last result doesn't look too good.

```
richard@richard-pc:~$ modinfo 8812au
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/8812au.ko
version:        v4.3.20_16317.20160108
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     A8D21A7CF2BB805A2609818
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       4.18.0-16-generic SMP mod_unload 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_rfkfree_enable:int
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_vht_enable:int
parm:           rtw_beamform_cap:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_dml:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_dc_backoff:DC backoff for Adaptivity (uint)
parm:           rtw_adaptivity_th_l2h_ini:TH_L2H_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:TH_EDCCA_HL_diff for Adaptivity (int)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_kfree:default kfree config value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
richard@richard-pc:~$ lsusb
Bus 001 Device 005: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
richard@richard-pc:~$ modinfo rtl8812au | grep alias
modinfo: ERROR: Module rtl8812au not found.
```

Still not picking up my WiFi

---

### Post by jeremy31 on 2019-03-18
I think you need ```
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
Reboot

---

### Post by richyg on 2019-03-18
Thank you so much, WiFi is now working!

Will I have to do anything like this after a similar update in future?

---

### Post by jeremy31 on 2019-03-18
It will work until Ubuntu 18.10 becomes EOL in August as the dkms will keep the module working with new kernels, at least 4.18 kernels

---

