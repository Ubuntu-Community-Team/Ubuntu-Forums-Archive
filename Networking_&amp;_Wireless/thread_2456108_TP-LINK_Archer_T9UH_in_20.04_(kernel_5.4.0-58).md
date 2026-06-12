---
title: "TP-LINK Archer T9UH in 20.04 (kernel 5.4.0-58)"
date: 2021-01-04
forum: Networking &amp; Wireless
---

### Post by en1i on 2021-01-04
[FONT=arial]Hey to all! 

I have 2 OS on my desktop, so I have tested TP-LINK Archer T9UH wifi adapter in the Windows 10 and it works fine. 

However in the Ubuntu I don't able even to see it via **lsusb**: I received empty response. After reboot,  **lsusb** works, but it freezes after the adapter inserted into any of USB slots.
I have tried to use [/FONT]https://github.com/aircrack-ng/rtl8812au and [https://github.com/aircrack-ng/rtl8814au](https://github.com/aircrack-ng/rtl8814au) but it seems like there is no effect.

What should I do, any ideas? Mb I need to clean old drivers in some way. I could even install the another Ubuntu version if I was sure that this would help.

PS: my previous wi-fi adapter was TP-LINK TL-WN727N and it worked as expected.

System info: Linux version 5.4.0-58-generic (buildd@lcy01-amd64-004) (gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04))

---

### Post by en1i on 2021-01-04
modinfo 8812au:

```

filename:       /lib/modules/5.4.0-58-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     A1B4B8FF70567B29CF1C971
alias:          usb:v056Ep4007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0953d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0820d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p025Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9097d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           8812au
vermagic:       5.4.0-58-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         alex-pc Secure Boot Module Signature key
sig_key:        40:D1:86:70:0C:3B:FA:48:61:F6:7A:29:C5:99:E9:97:80:97:23:B9
sig_hashalgo:   sha512
signature:      86:65:3D:01:18:72:75:CA:36:2E:3C:F2:78:29:08:1A:33:62:36:BF:
		FD:09:F3:58:02:ED:F7:54:FF:A1:D6:75:96:BE:BB:B8:C6:43:A9:68:
		DD:79:F7:A9:C1:A5:AE:F0:D8:B3:85:16:26:8A:D4:FD:81:1A:99:FC:
		E5:EC:58:75:11:63:26:82:5D:CD:21:41:71:A9:EF:81:18:0E:1E:FA:
		D8:54:B5:46:2F:2D:02:AE:A0:1D:14:E9:01:E6:F7:14:80:48:8F:97:
		27:06:55:34:28:DB:BB:B7:EB:8B:B5:E3:0B:7E:F8:4C:16:A5:DA:DD:
		59:01:57:2F:FF:43:5A:60:71:88:31:09:43:7E:72:53:F7:4B:18:B6:
		1C:93:00:25:4E:71:C0:8E:DA:5D:99:FF:80:B7:17:6A:70:00:74:E4:
		1F:C7:36:E2:C0:A7:46:80:48:2F:DA:C1:64:DD:00:6D:F4:F8:E1:34:
		DD:84:56:11:32:81:CD:FB:8A:59:DB:40:F0:F1:F6:C3:6B:C7:4A:BB:
		6D:B0:AE:08:8B:15:58:E5:29:F0:E7:52:96:19:0C:58:88:61:23:83:
		DB:DD:A4:62:97:92:7C:B4:25:D6:85:2B:F9:DA:72:E7:6C:D3:99:55:
		F4:3F:03:C1:10:7E:08:D3:B6:17:47:30:1B:CC:9E:EE
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
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
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_nhm_en:0:disable, 1:enable (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_RFE_type:default init value:64 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

```

---

### Post by wildmanne39 on 2021-01-04
Hello and welcome to the forum en1i.

*Thread moved to **Networking & Wireless for a more appropriate fit**.* 

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by en1i on 2021-01-04
sure, thanks

Okay, by some reason lsusb started to work. What I have done: reboot -> mount old wifi adapter -> unmount it -> mount Archer T9UH
for now the lsusb is:
```

Bus 002 Device 002: ID 0bc2:61b6 Seagate RSS LLC Maxtor HX-M101TCB/GM [M3 Portable 1TB]
Bus 002 Device 003: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 1c4f:0026 SiGma Micro Keyboard
Bus 001 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 003: ID 041e:3256 Creative Technology, Ltd Sound BlasterX G6
Bus 001 Device 004: ID 2357:0106 TP-Link Archer T9UH v1 [Realtek RTL8814AU]
Bus 001 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 008: ID 12d1:4321 Huawei Technologies Co., Ltd. UVC Camera
Bus 001 Device 006: ID 09da:9090 A4Tech Co., Ltd. XL-730K / XL-750BK / XL-755BK Mice
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But still no Wi-fi icon. And the interesting thing: u can see that it detects T9UH - under the version 1. However, the adapter has label in the back side with a version 2

---

### Post by en1i on 2021-01-04
dkms status:

```

nvidia, 450.80.02, 5.4.0-56-generic, x86_64: installed
nvidia, 450.80.02, 5.4.0-58-generic, x86_64: installed
realtek-rtl88xxau, 5.6.4.2~20201019: added
rtl8812au, 4.3.8.12175.20140902+dfsg, 5.4.0-58-generic, x86_64: installed
rtl8814au, 4.3.21, 5.4.0-58-generic, x86_64: built

```

so I have 3 different wireless drivers in the system. I think I should leave only one

---

### Post by en1i on 2021-01-04
Okay, I moved to  "/lib/modules/5.4.0-58-generic/updates/dkms" , checked that I have "8812au.ko" folder inside.

Than I run
```
sudo dkms uninstall rtl8812au/4.3.8.12175.20140902+dfsg
```
checked that "8812au.ko" no longer exists
and "rtl8812au" no longer installed:
"dkms status"
```

nvidia, 450.80.02, 5.4.0-56-generic, x86_64: installed
nvidia, 450.80.02, 5.4.0-58-generic, x86_64: installed
realtek-rtl88xxau, 5.6.4.2~20201019: added
rtl8812au, 4.3.8.12175.20140902+dfsg, 5.4.0-58-generic, x86_64: built
rtl8814au, 4.3.21, 5.4.0-58-generic, x86_64: built

```

Then install rtl8814:
```
sudo dkms install rtl8814au/4.3.21
```

But it is not working. After the reboot "lsusb" didn't respond again. So I think rtl8812au is the correct version, but by some reason it doesn't work

---

### Post by en1i on 2021-01-04
Seems like TP-LINK adapters in not working with the latest kernel versions (from 5.3.42)
[https://github.com/aircrack-ng/rtl8812au/issues/645](https://github.com/aircrack-ng/rtl8812au/issues/645)
How to downgrade to another version?)

---

### Post by jeremy31 on 2021-01-04
You actually need the rtl8814au version from the aircrack-ng repo on github.  They took that one out of rtl8812au recently

[https://github.com/aircrack-ng/rtl8814au](https://github.com/aircrack-ng/rtl8814au)

---

### Post by en1i on 2021-01-04
Kicked it working.
What I have done: downgraded kernel version, reboot in it and reinstall drivers for adapter

Working kernel:
[[COLOR=#1155CC][FONT=Arial]https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2.21/[/FONT][/COLOR]]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2.21/")
Instruction how to install another kernel: [https://ubuntuhandbook.org/index.php/2019/07/install-linux-kernel-5-2-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2019/07/install-linux-kernel-5-2-ubuntu-linux-mint/)
Reboot after installation
Select in grub loader "Additional", then select chosen kernel version
Then u need to reinstall drivers for wifi adapter. In my case, working repository is [https://github.com/aircrack-ng/rtl8814au](https://github.com/aircrack-ng/rtl8814au)
```

cd ~/Downloads
git clone https://github.com/aircrack-ng/rtl8814au.git
sudo dkms add  ~/Downloads/rtl8814au
sudo dkms install rtl8814au/4.3.21

```

---

### Post by jeremy31 on 2021-01-04
I see this in the source code {code]	{USB_DEVICE(0x2357, 0x0106), .driver_info = RTL8814A}, /* TP-LINK Archer T9UH */[/code]
The aircrack-ng/rtl8812au repo doesn't support the rtl8814au any more, but if your download in /Downloads is old enough it might work.  Post URL from terminal for ```
cat /Downloads/rtl8812au/Makefile | nc termbin.com 9999
```

---

### Post by en1i on 2021-01-04
> **jeremy31 said:**
> I see this in the source code {code]    {USB_DEVICE(0x2357, 0x0106), .driver_info = RTL8814A}, /* TP-LINK Archer T9UH */[/code]
The aircrack-ng/rtl8812au repo doesn't support the rtl8814au any more, but if your download in /Downloads is old enough it might work.  Post URL from terminal for ```
cat /Downloads/rtl8812au/Makefile | nc termbin.com 9999
```

[https://termbin.com/j2ia](https://termbin.com/j2ia)

---

### Post by jeremy31 on 2021-01-04
Not sure how it could have worked when I see ```
CONFIG_RTL8814A = n
```
I would imagine new results from ```
dkms status; lsmod | grep cfg
```
Might explain what happened

---

### Post by en1i on 2021-01-04
> **jeremy31 said:**
> Might explain what happened
Im on 5.2.21 kernel now, are u expecting logs from 5.4.0?
```

nvidia, 450.80.02, 5.2.21-050221-generic, x86_64: installed
nvidia, 450.80.02, 5.4.0-56-generic, x86_64: installed
nvidia, 450.80.02, 5.4.0-58-generic, x86_64: installed
nvidia, 450.80.02, 5.4.0-59-generic, x86_64: installed
rtl8814au, 4.3.21, 5.2.21-050221-generic, x86_64: installed
rtl8814au, 4.3.21, 5.4.0-59-generic, x86_64: built
cfg80211              708608  1 8814au

```

I have taken snapshot one more time
[https://termbin.com/wyif](https://termbin.com/wyif)

Im using the old repo, not rtl8812au but rtl8814au

---

### Post by jeremy31 on 2021-01-04
Try ```
sudo dkms install rtl8814au/4.3.21 -k 5.4.0-59-generic
```
Then reboot into the 5.4.0-59 kernel

---

### Post by en1i on 2021-01-04
> **jeremy31 said:**
> Try ```
sudo dkms install rtl8814au/4.3.21 -k 5.4.0-59-generic
```
Then reboot into the 5.4.0-59 kernel
Not working. No wifi icon, cant get lsusb, cant reboot because usb is sealed, only by click manually on "power". Actually I have checked all the combinations of kernel/drivers. Seems like this drivers really not working on new kernels

---

### Post by morrownr on 2021-01-05
[https://github.com/morrownr](https://github.com/morrownr)

Give this site a try.

---

### Post by en1i on 2021-01-05
> **morrownr said:**
> [https://github.com/morrownr](https://github.com/morrownr)

Give this site a try.

Thanks, I have tried recently. Before that I had deleted via dkms another drivers for wifi

What I receive when trying to install this package:
```

Installing rtl8814au-5.8.5.1
Copying source files to: /usr/src/rtl8814au-5.8.5.1
Copying 8814au.conf to: /etc/modprobe.d


Creating symlink /var/lib/dkms/rtl8814au/5.8.5.1/source ->
                 /usr/src/rtl8814au-5.8.5.1


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...
'make' -j12 KVER=5.4.0-59-generic KSRC=/lib/modules/5.4.0-59-generic/build...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8814au: 5.8.5.1 not found
Error! Bad return status for module build on kernel: 5.4.0-59-generic (x86_64)
Consult /var/lib/dkms/rtl8814au/5.8.5.1/build/make.log for more information.
An error occurred while running: dkms build : 10

```

And the log from /var/lib/dkms/rtl8814au/5.8.5.1/build/make.log:
```

DKMS make.log for rtl8814au-5.8.5.1 for kernel 5.4.0-59-generic (x86_64)
&#1074;&#1110;&#1074;&#1090;&#1086;&#1088;&#1086;&#1082;, 5 &#1089;&#1110;&#1095;&#1085;&#1103; 2021 11:53:05 +0200
make ARCH=arm64 CROSS_COMPILE= -C /lib/modules/5.4.0-59-generic/build M=/var/lib/dkms/rtl8814au/5.8.5.1/>
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-59-generic'
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ieee80211.o
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:273: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_cmd.o] Error 1
make[2]: *** Waiting for unfinished jobs....
gcc: error: unrecognized command line option ‘-mlittle-endian’
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_mlme.o
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_security.o] Err>
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_debug.o] Error 1
  CC [M]  /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_mlme_ext.o
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_io.o] Error 1
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ioctl_query.o] >
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ioctl_set.o] Er>
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_mlme.o] Error 1
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_ieee80211.o] Er>
gcc: error: unrecognized command line option ‘-mlittle-endian’
make[2]: *** [scripts/Makefile.build:275: /var/lib/dkms/rtl8814au/5.8.5.1/build/core/rtw_mlme_ext.o] Err>
make[1]: *** [Makefile:1757: /var/lib/dkms/rtl8814au/5.8.5.1/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-59-generic'
make: *** [Makefile:2376: modules] Error 2

```

---

### Post by jeremy31 on 2021-01-05
Post results for ```
uname -a; arch
```

---

### Post by en1i on 2021-01-05
> **jeremy31 said:**
> ```
uname -a; arch
```

```

Linux alex-pc 5.2.21-050221-generic #201910111731 SMP Fri Oct 11 17:34:34 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
x86_64

```

---

### Post by jeremy31 on 2021-01-05
Your kernel and arch both show x86_64 but the line from the build log shows make ARCH=arm64

---

### Post by morrownr on 2021-01-05
That is interesting. I'd like to see what these 3 lines look like in your Makefile:

CONFIG_PLATFORM_I386_PC = y
CONFIG_PLATFORM_ARM_RPI = n
CONFIG_PLATFORM_ARM64_RPI = n

---

### Post by en1i on 2021-04-23
Today I have reinstalled Ubuntu, completely with files deletion, and the driver from this repo [https://github.com/morrownr](https://github.com/morrownr) works!
Thanks 2 all for responses

---

### Post by morrownr on 2021-04-24
You are welcome.

As a guy that tries to maintain Realtek drivers ( [https://github.com/morrownr](https://github.com/morrownr) ) I can tell you that the single most important thing a Linux user can do to stay happy with the USB WiFi capability is to move away from Realtek based adapters. More info available here...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Many Linux users do not know that there are many USB adapters that are supported with good, Linux Wireless standards-compliant drivers that are available. Need AC1200 capability? Check Need AC600 capability? Check. Need WPA3 support? Check. Need interface combinations support? Check. No need to find and compile drivers? Check. Support master and monitor modes? Check.

---

### Post by en1i on 2021-05-07
> **morrownr said:**
> You are welcome.

As a guy that tries to maintain Realtek drivers ( [https://github.com/morrownr](https://github.com/morrownr) ) I can tell you that the single most important thing a Linux user can do to stay happy with the USB WiFi capability is to move away from Realtek based adapters. More info available here...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Many Linux users do not know that there are many USB adapters that are supported with good, Linux Wireless standards-compliant drivers that are available. Need AC1200 capability? Check Need AC600 capability? Check. Need WPA3 support? Check. Need interface combinations support? Check. No need to find and compile drivers? Check. Support master and monitor modes? Check.

Thanks man for all the hard work u have done and all the efforts, ur amazing

---

