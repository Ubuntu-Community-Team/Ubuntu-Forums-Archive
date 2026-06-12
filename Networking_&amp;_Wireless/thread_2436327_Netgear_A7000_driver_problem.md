---
title: "Netgear A7000 driver problem"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by zeberusarcane on 2020-02-04
Hello everyone. I am having massive trouble getting my network adapter ( Netgear A7000 ) to work.
I'm running on Ubuntu 18.04
Kernel [5.3.0-28-generic]

I've installed the drivers rtl8812a and rtl8814a + rtl8814a kernel 5.3 patch branch

lsusb outputs:
```

julian@Dedsec01:~$ lsusb

Bus 003 Device 002: ID 046d:c083 Logitech, Inc.
Bus 001 Device 002: ID 0846:9054 NetGear, Inc.

```

dksm status output:
```

8812au, 4.2.2, 5.3.0-28-generic, x86_64: installed
nvidia, 440.48.02, 5.3.0-28-generic, x86_64: installed
rtl8814au, 4.3.21, 5.3.0-28-generic, x86_64: installed

```


Any help would be appreciated

---

### Post by chili555 on 2020-02-04
Please run and post the results of:```
modinfo 8814au | grep 9054
dmesg | grep -e rtl -e 8814
```Thanks.

---

### Post by zeberusarcane on 2020-02-05
modinfo 8814au | grep 9054
```
alias:          usb:v0846p9054d*dc*dsc*dp*ic*isc*ip*in*
```

dmesg | grep -e rtl -e 8814
```

[    0.188147] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    6.048023] usbcore: registered new interface driver rtl8812au
[    6.379946] RTL871X: rtl8814au v4.3.21_17997.20160531
[   14.553768] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.553891]  ? _rtw_malloc+0x2d/0x2f [8814au]
[   14.553940]  ? _rtw_malloc+0x2d/0x2f [8814au]
[   14.553984]  rtw_wiphy_register+0x1a/0x1d [8814au]
[   14.554025]  ? rtw_wiphy_register+0x1a/0x1d [8814au]
[   14.554066]  rtw_cfg80211_ndev_res_register+0x15/0x1c [8814au]
[   14.554105]  rtw_os_ndev_register+0x22/0x98 [8814au]
[   14.554142]  rtw_os_ndevs_register+0x98/0x154 [8814au]
[   14.554180]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.554217]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.554273]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.554367] WARNING: CPU: 10 PID: 563 at /var/lib/dkms/rtl8814au/4.3.21/build/os_dep/linux/os_intfs.c:1089 rtw_os_ndev_register+0x72/0x98 [8814au]
[   14.554368] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.554435] RIP: 0010:rtw_os_ndev_register+0x72/0x98 [8814au]
[   14.554485]  rtw_os_ndevs_register+0x98/0x154 [8814au]
[   14.554522]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.554559]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.554611]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.554698] WARNING: CPU: 10 PID: 563 at /var/lib/dkms/rtl8814au/4.3.21/build/os_dep/linux/os_intfs.c:2453 rtw_os_ndevs_register+0xf6/0x154 [8814au]
[   14.554698] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.554763] RIP: 0010:rtw_os_ndevs_register+0xf6/0x154 [8814au]
[   14.554813]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.554849]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.554900]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.554951] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.555037]  rtw_os_ndev_unregister+0x39/0x53 [8814au]
[   14.555074]  rtw_os_ndevs_register+0x134/0x154 [8814au]
[   14.555110]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.555147]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.555197]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.557410] rtl8192cu: Chip version 0x10
[   14.572104]  rtw_os_ndev_unregister+0x39/0x53 [8814au]
[   14.572146]  rtw_os_ndevs_register+0x134/0x154 [8814au]
[   14.572186]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.572225]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.572280]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.572332] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.572463]  rtw_wiphy_unregister+0x1a/0x1d [8814au]
[   14.572501]  rtw_os_ndev_unregister+0x45/0x53 [8814au]
[   14.572539]  rtw_os_ndevs_register+0x134/0x154 [8814au]
[   14.572577]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.572614]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.572665]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.572716] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   14.572833]  rtw_wiphy_unregister+0x1a/0x1d [8814au]
[   14.572870]  rtw_os_ndev_unregister+0x45/0x53 [8814au]
[   14.572907]  rtw_os_ndevs_register+0x134/0x154 [8814au]
[   14.572945]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.572981]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.573032]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.573172]  rtw_wiphy_unregister+0x1a/0x1d [8814au]
[   14.573210]  rtw_os_ndev_unregister+0x45/0x53 [8814au]
[   14.573247]  rtw_os_ndevs_register+0x134/0x154 [8814au]
[   14.573284]  rtw_os_ndevs_init+0x29/0x3f [8814au]
[   14.573321]  rtw_drv_init+0x2a0/0x341 [8814au]
[   14.573380]  rtw_drv_entry+0x65/0x1000 [8814au]
[   14.573427] Modules linked in: snd_hda_codec_hdmi edac_mce_amd kvm_amd kvm irqbypass snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep snd_pcm rtl8192cu(+) snd_seq_midi snd_seq_midi_event rtl_usb eeepc_wmi aesni_intel rtl8192c_common ucsi_ccg typec_ucsi rtlwifi asus_wmi aes_x86_64 snd_rawmidi sparse_keymap crypto_simd cryptd glue_helper mac80211 video wmi_bmof typec mxm_wmi 8814au(OE+) input_leds snd_seq joydev snd_seq_device snd_timer cfg80211 libarc4 k10temp snd soundcore ccp mac_hid nvidia_uvm(OE) sch_fq_codel 8812au(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm igb nvme ipmi_devintf i2c_piix4 i2c_nvidia_gpu ipmi_msghandler dca nvme_core ahci i2c_algo_bit libahci gpio_amdpt wmi gpio_generic
[   17.761808] rtl8192cu: Board Type 0
[   17.770802] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   17.770869] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   17.771100] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   17.771606] usbcore: registered new interface driver rtl8192cu
[   17.779261] usbcore: registered new interface driver rtl8xxxu
[   17.782119] rtl8192cu 1-3:1.0 wlx00f140410c8e: renamed from wlan0
[   17.851808] rtl8192cu: MAC auto ON okay!
[   19.442008] rtl8192cu: Tx queue select: 0x05
[   29.824241] rtl_usb: reg 0x82, usbctrl_vendorreq TimeOut! status:0xffffff92 value=0xa200
[   40.064219] rtl_usb: reg 0x82, usbctrl_vendorreq TimeOut! status:0xffffff92 value=0xa300
[   50.304259] rtl_usb: reg 0x82, usbctrl_vendorreq TimeOut! status:0xffffff92 value=0xa400
[   60.544220] rtl_usb: reg 0x80, usbctrl_vendorreq TimeOut! status:0xffffff92 value=0xa500

```

---

### Post by jeremy31 on 2020-02-05
```
sudo dkms remove 8812au/4.2.2 --all
sudo dkms remove rtl8814au/4.3.21 --all
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
Reboot

---

