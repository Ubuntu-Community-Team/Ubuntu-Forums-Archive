---
title: "WiFi keeps disconnecting, with diagnose file, dmesg | grep wl shows Wrong Mac address"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by AInoob on 2015-11-13
The computer is Lenovo Yoga 3 Pro, the driver is BCM4352. So sometimes the WiFi sign shows that it's still connected, but it is actually not, so I need to disable WiFi and the enable it.

dmesg | grep gives the following

[    2.232206] wl: module license 'MIXED/Proprietary' taints kernel.
[    2.234794] wl: module verification failed: signature and/or required key missing - tainting kernel
[    2.437565] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    2.441536] wl 0000:01:00.0 wlp1s0: renamed from wlan0
[    3.515093] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   44.825775] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[   44.825812] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[   45.038635] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[   45.038669] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[   51.048597] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[   51.048630] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:70   profile =00:24:97:88:9a:50
[  110.411325] ERROR @wl_dev_intvar_get : error (-1)
[  110.411331] ERROR @wl_cfg80211_get_tx_power : error (-1)


And here is the diagnose file by running the script

---

### Post by chili555 on 2015-11-13
It is seeing a different MAC address because the wireless is attempting to roam from among some half-dozen access points named Knox-Wireless! You have a profile stored for one and it's seeing an identical name with a different MAC address.> Knox-Wireless  <MAC 'Knox-Wireless' [AC6]>  Infra  40    5200 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2 802.1X  no        
Knox-Wireless  <MAC 'Knox-Wireless' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 802.1X  no        
--             <MAC '--' [AN22]>  Infra  11    2462 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2              no        
Knox-Wireless  <MAC 'Knox-Wireless' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2 802.1X  no        
<snip>
Knox-Wireless  <MAC 'Knox-Wireless' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA1 WPA2 802.1X  yes     * 
Knox-Wireless  <MAC 'Knox-Wireless' [AC7]>  Infra  149   5745 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2 802.1X  no        In fact, you are currently connected to one with lesser signal strength when a much stronger one is nearby.

You might try the technique I described here: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by AInoob on 2015-11-14
Thank you chili555, But WiFi still having some trouble. Here is the new output
[ 8092.988655] CPU: 0 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[ 8092.988804]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8092.988870]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[ 8092.988933]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[ 8097.053470] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d6:60   profile =00:24:97:88:d4:1f
[ 8097.053557] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d6:60   profile =00:24:97:88:d4:1f
[ 8103.051512] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d6:60   profile =00:24:97:88:d4:1f
[ 8103.051566] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d6:60   profile =00:24:97:88:d4:1f
[ 8143.445682] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8143.445739] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8145.078863] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8145.078919] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8151.087170] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8151.087248] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:1f   profile =00:24:97:88:d4:10
[ 8194.339052] ERROR @wl_notify_scan_status : wlp1s0 Scan_results error (-22)
[10032.234167] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d2:9f   profile =00:24:97:88:d2:90
[10032.234257] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d2:9f   profile =00:24:97:88:d2:90
[21070.909857] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd_hda_core snd_hwdep serio_raw snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer mei_me mei lpc_ich snd shpchp processor_thermal_device intel_soc_dts_iosf iosf_mbi soundcore int3403_thermal dw_dmac dw_dmac_core
[21070.909936] CPU: 0 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[21070.910031]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[21070.910072]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[21070.910111]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[21071.008459] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21071.008524] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21077.011680] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21077.011719] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21083.015743] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21083.015783] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21089.019803] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21089.019843] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21094.858590] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21094.858631] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21095.017666] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21095.017731] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21101.026777] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21101.026818] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21107.030984] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21107.031048] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21113.034079] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21113.034120] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21119.035860] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21119.035900] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21129.740600] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21129.740621] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21131.040927] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[21131.040967] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:24:97:88:d4:10   profile =00:24:97:88:d6:60
[43781.677570] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd_hda_core snd_hwdep serio_raw snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer mei_me mei lpc_ich snd shpchp processor_thermal_device intel_soc_dts_iosf iosf_mbi soundcore int3403_thermal dw_dmac dw_dmac_core
[43781.677649] CPU: 1 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[43781.677742]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[43781.677783]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[43781.677822]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[43844.696064] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd_hda_core snd_hwdep serio_raw snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer mei_me mei lpc_ich snd shpchp processor_thermal_device intel_soc_dts_iosf iosf_mbi soundcore int3403_thermal dw_dmac dw_dmac_core
[43844.696159] CPU: 1 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[43844.696257]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[43844.696297]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[43844.696334]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[43944.713517] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd_hda_core snd_hwdep serio_raw snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer mei_me mei lpc_ich snd shpchp processor_thermal_device intel_soc_dts_iosf iosf_mbi soundcore int3403_thermal dw_dmac dw_dmac_core
[43944.713692] CPU: 3 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[43944.713892]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[43944.713930]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[43944.713966]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[44039.507616] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd_hda_core snd_hwdep serio_raw snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer mei_me mei lpc_ich snd shpchp processor_thermal_device intel_soc_dts_iosf iosf_mbi soundcore int3403_thermal dw_dmac dw_dmac_core
[44039.507742] CPU: 0 PID: 531 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-18-generic #22-Ubuntu
[44039.507898]  [<ffffffffc0688965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[44039.507969]  [<ffffffffc0687fa4>] wl_event_handler+0x64/0x1e0 [wl]
[44039.508036]  [<ffffffffc0687f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[44134.301631] Modules linked in: rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) btusb btrtl btbcm btintel bluetooth vboxdrv(OE) joydev hid_multitouch hid_rmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw gf128mul snd_hda_codec_realtek glue_helper snd_hda_codec_generic ablk_helper cryptd snd_hda_intel snd_hda_codec input_leds snd

---

