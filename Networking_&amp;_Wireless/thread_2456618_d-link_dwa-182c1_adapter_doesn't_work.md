---
title: "d-link dwa-182c1 adapter doesn't work"
date: 2021-01-15
forum: Networking &amp; Wireless
---

### Post by yxungquri on 2021-01-15
[FONT=arial]Good afternoon, I recently installed Ubuntu Budgie [COLOR=#000000]for my desktop, but my wireless adapter doesn't work. 
I've successfuly installed the rtl8812au driver by system software, but it still just can't find wi-fi networks.

Here's following commands' results: [/COLOR][/FONT]lspci -nnk | grep -iA2 net, lsusb, iwconfig, rfkill list all, lsmod, modinfo 8812au
```
yxungquri@quri:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:367d]
    Kernel driver in use: r8169
    Kernel modules: r8169


yxungquri@quri:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 2001:3315 D-Link Corp. DWA-182 Wireless AC Dualband Adapter(rev.C) [Realtek RTL8812AU]
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 12d1:108a Huawei Technologies Co., Ltd. POT-LX1
Bus 003 Device 003: ID 0c45:7633 Microdia USB DEVICE
Bus 003 Device 002: ID 09da:9066 A4Tech Co., Ltd. F3 V-Track Gaming Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


yxungquri@quri:~$ iwconfig
lo        no wireless extensions.


enp3s0    no wireless extensions.


usb0      no wireless extensions.


yxungquri@quri:~$ rfkill list all
yxungquri@quri:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
nvidia_uvm           1024000  0
nvidia_drm             57344  4
nvidia_modeset       1228800  8 nvidia_drm
nvidia              34045952  422 nvidia_uvm,nvidia_modeset
8812au               1290240  0
cfg80211              782336  1 8812au
drm_kms_helper        225280  1 nvidia_drm
cec                    53248  1 drm_kms_helper
rc_core                53248  1 cec
rndis_host             20480  0
cdc_ether              20480  1 rndis_host
intel_rapl_msr         20480  0
usbnet                 49152  2 rndis_host,cdc_ether
intel_rapl_common      28672  1 intel_rapl_msr
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
rtsx_usb_ms            24576  0
joydev                 28672  0
input_leds             16384  0
memstick               24576  1 rtsx_usb_ms
mii                    16384  1 usbnet
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
mei_hdcp               24576  0
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  4
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               118784  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
coretemp               20480  0
kvm_intel             282624  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
kvm                   724992  1 kvm_intel
mei_me                 40960  1
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei                   110592  3 mei_hdcp,mei_me
at24                   24576  0
mac_hid                16384  0
soundcore              16384  1 snd
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
aesni_intel           372736  0
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
rapl                   20480  0
intel_cstate           20480  0
serio_raw              20480  0
efi_pstore             16384  0
sch_fq_codel           20480  3
parport_pc             45056  0
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
drm                   565248  7 drm_kms_helper,nvidia_drm
ip_tables              32768  0
x_tables               45056  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   135168  2 usbhid,hid_generic
rtsx_usb_sdmmc         36864  0
rtsx_usb               28672  2 rtsx_usb_sdmmc,rtsx_usb_ms
i2c_i801               32768  0
i2c_smbus              20480  1 i2c_i801
lpc_ich                24576  0
crc32_pclmul           16384  0
ahci                   40960  2
libahci                36864  1 ahci
psmouse               159744  0
r8169                  94208  0
xhci_pci               20480  0
realtek                24576  1
xhci_pci_renesas       20480  1 xhci_pci
video                  49152  0


yxungquri@quri:~$ modinfo 8812au
filename:       /lib/modules/5.8.0-38-generic/updates/dkms/8812au.ko
version:        v4.3.8_12175.20140902
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     4F63DC5C780A34D13BF6D5A
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
vermagic:       5.8.0-38-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         ubuntu-budgie Secure Boot Module Signature key
sig_key:        63:16:B3:2B:F0:F8:1E:4A:EC:C8:5C:3D:D7:99:64:6B:7A:57:5A:CF
sig_hashalgo:   sha512
signature:      0F:5C:BC:30:E1:9C:F4:56:A5:04:B2:97:87:95:6A:04:9D:0A:F2:4E:
        E8:BB:59:CF:E6:2D:78:B9:6C:43:4A:A9:7C:03:D7:A0:DD:81:2B:2D:
        9C:D4:3D:60:5F:F8:08:47:41:02:AC:28:2D:9B:F6:62:17:FE:ED:FC:
        14:4B:84:47:62:FB:B8:05:64:67:61:AE:DF:6A:F4:B2:9E:EF:8B:BA:
        23:5C:35:D5:C6:07:27:79:67:2B:CF:22:73:19:B8:4B:F0:99:E8:BE:
        FA:54:B6:EC:DB:4A:41:2D:5B:10:99:7A:F6:CD:03:AB:E0:FF:41:AD:
        22:D3:26:42:E5:EF:37:1D:FE:50:B8:BC:15:AB:31:5D:1B:C0:96:D7:
        60:48:97:DD:84:79:56:EA:14:30:B5:F7:06:05:93:85:AF:A0:79:24:
        6E:E7:89:DF:67:FE:D4:5F:43:04:7F:C8:35:B8:92:44:AB:B8:76:06:
        11:89:FD:7B:80:EE:0F:84:DA:40:59:15:75:23:02:FE:AD:74:95:FA:
        8D:37:FD:F1:6A:D4:BB:7E:A2:B9:BD:84:70:88:52:DA:7E:FA:D3:C3:
        C1:66:E6:16:B4:35:67:98:07:8C:92:8F:D7:42:26:36:87:A4:33:AE:
        C9:C8:17:32:D4:25:91:6D:5C:5E:1B:47:DD:AA:32:8D
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

```[FONT=arial][COLOR=#000000]

In the Network Settings it says that no one Wi-Fi adapter is found.

I'm newbie in it, help me please[/COLOR][/FONT]

---

### Post by chili555 on 2021-01-15
Please check here: [https://askubuntu.com/questions/1299395/installed-rtl8812au-dkms-for-dwa-182-driver-but-driver-not-detected](https://askubuntu.com/questions/1299395/installed-rtl8812au-dkms-for-dwa-182-driver-but-driver-not-detected)

If you need further assistance or a step-by-step, please post back.

---

### Post by yxungquri on 2021-01-15
> **chili555 said:**
> Please check here: [https://askubuntu.com/questions/1299395/installed-rtl8812au-dkms-for-dwa-182-driver-but-driver-not-detected](https://askubuntu.com/questions/1299395/installed-rtl8812au-dkms-for-dwa-182-driver-but-driver-not-detected)

If you need further assistance or a step-by-step, please post back.
Thank you so much! It works for me! I can't believe I spent a couple dozen hours searching for this :)

---

### Post by morrownr on 2021-01-16
Additional information for those that are searching in the future: The rtl8812au driver package that is in the Ubuntu repository is very old. It is based on source code from 2014. In kernel years, it would be about 247 years old... okay, sort of kidding there but my point is that users with adapters based on the rtl8812au chipset have a far better driver available... one from source released in 2020 (Oct.)

[https://github.com/morrownr](https://github.com/morrownr)

For what it is worth, I filed a bug on the rtl8812au-dkms package offering to help the maintainer modernize the driver. I haven't heard anything.

---

