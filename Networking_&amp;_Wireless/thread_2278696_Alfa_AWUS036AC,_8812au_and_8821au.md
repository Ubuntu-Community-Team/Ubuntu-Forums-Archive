---
title: "Alfa AWUS036AC, 8812au and 8821au"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by andrea-cimatoribus on 2015-05-18
I am very confused and kind of annoyed from my Alfa AWUS036AC usb wi-fi card (sold as Linux-ready, so beware).
I downloaded the latest driver from [http://alfa.com.tw](http://alfa.com.tw), compiled and installed it without problem using the install.sh script provided.
While the card is detected and a wlan2 interface is created, the connection quality is very bad (actually, I usually cannot see any network with that card). Even more disappointing, on a Linux Mint 17 machine (kernel 3.13) the device was working fine (with a hiccup once in a while).

I don't understand if I'm using 8812au or 8821au, so here comes some info I guess it's useful for those who know. Note that I connected and disconnected the card a couple of times.

```
 uname -a
Linux 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
dmesg | grep -e wlan -e 8821au
[    2.472099] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.477293] systemd-udevd[2184]: renamed network interface wlan1 to wlan2
[   18.692850] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   18.693313] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   29.196755] wlan0: authenticate with 84:9c:a6:5b:1f:b8
[   29.203692] wlan0: send auth to 84:9c:a6:5b:1f:b8 (try 1/3)
[   29.206056] wlan0: authenticated
[   29.206160] wlan0: waiting for beacon from 84:9c:a6:5b:1f:b8
[   29.307807] wlan0: associate with 84:9c:a6:5b:1f:b8 (try 1/3)
[   29.339530] wlan0: associate with 84:9c:a6:5b:1f:b8 (try 2/3)
[   29.343524] wlan0: RX AssocResp from 84:9c:a6:5b:1f:b8 (capab=0x411 status=0 aid=1)
[   29.375149] wlan0: associated
[   29.375170] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  118.197483] systemd-udevd[2469]: renamed network interface wlan1 to wlan2
[  120.417958] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  120.962007] systemd-udevd[2469]: renamed network interface wlan1 to wlan2
[  123.174411] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  123.174916] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
```

```
dmesg | grep -e wlan -e 8812au
[    2.472099] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.450679] usbcore: registered new interface driver rtl8812au
[   16.477293] systemd-udevd[2184]: renamed network interface wlan1 to wlan2
[   18.692850] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   18.693313] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   29.196755] wlan0: authenticate with 84:9c:a6:5b:1f:b8
[   29.203692] wlan0: send auth to 84:9c:a6:5b:1f:b8 (try 1/3)
[   29.206056] wlan0: authenticated
[   29.206160] wlan0: waiting for beacon from 84:9c:a6:5b:1f:b8
[   29.307807] wlan0: associate with 84:9c:a6:5b:1f:b8 (try 1/3)
[   29.339530] wlan0: associate with 84:9c:a6:5b:1f:b8 (try 2/3)
[   29.343524] wlan0: RX AssocResp from 84:9c:a6:5b:1f:b8 (capab=0x411 status=0 aid=1)
[   29.375149] wlan0: associated
[   29.375170] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  106.666482] Modules linked in: ctr ccm 8812au(OE) msr acpi_call(OE) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media btusb arc4 iwldvm mac80211 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic iwlwifi cfg80211 bnep rfcomm bluetooth 6lowpan_iphc joydev intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel dm_multipath scsi_dh aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep thinkpad_acpi nvram snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich shpchp snd_seq i915 snd_seq_device mei_me mei snd_timer snd wmi drm_kms_helper drm i2c_algo_bit soundcore video parport_pc intel_smartconnect mac_hid ppdev soc_button_array lp parport xfs libcrc32c ahci psmouse libahci sdhci_pci sdhci dm_mirror dm_region_hash dm_log
[  106.666829]  [<ffffffffc0aa9d42>] rtw_usb_if1_deinit+0x45/0x99 [8812au]
[  106.666867]  [<ffffffffc0aa9ec7>] rtw_dev_remove+0x56/0x63 [8812au]
[  118.197483] systemd-udevd[2469]: renamed network interface wlan1 to wlan2
[  120.417958] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  120.962007] systemd-udevd[2469]: renamed network interface wlan1 to wlan2
[  123.174411] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  123.174916] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  123.197441] Modules linked in: ctr ccm 8812au(OE) msr acpi_call(OE) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media btusb arc4 iwldvm mac80211 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic iwlwifi cfg80211 bnep rfcomm bluetooth 6lowpan_iphc joydev intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel dm_multipath scsi_dh aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep thinkpad_acpi nvram snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi lpc_ich shpchp snd_seq i915 snd_seq_device mei_me mei snd_timer snd wmi drm_kms_helper drm i2c_algo_bit soundcore video parport_pc intel_smartconnect mac_hid ppdev soc_button_array lp parport xfs libcrc32c ahci psmouse libahci sdhci_pci sdhci dm_mirror dm_region_hash dm_log
[  123.197561]  [<ffffffffc0aa9d42>] rtw_usb_if1_deinit+0x45/0x99 [8812au]
[  123.197573]  [<ffffffffc0aa9ec7>] rtw_dev_remove+0x56/0x63 [8812au]
```

```
modinfo 8821au | grep -i version
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
srcversion:     FB70792EC4F779317A25A06
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int
```

```
modinfo 8812au | grep -i version
version:        v4.2.2_7502.20130517
srcversion:     1AC35E397F55F9D2E16846E
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int
```

After trying a few different versions of the driver available on-line, I recompiled and re-installed the Alfa version of the driver (version 4.3.14). Now, it works, detects the network and connects with good speed. Something must have changed (maybe the other drivers I tried changed something?) but I cannot tell what.
In any case, it now works, even if it's kind of disturbing not to know how...

For future reference: for some reason I could not identify, the drivers downloaded from alfa web-site are not always compiled correctly with the provided install.sh script. Only 8821au is compiled, while 8812au is the one which is loaded by the kernel. A solution is to modify the Makefile in the driver sources, changing the flag that triggers the compilation of 8812au driver too. The driver can then be compiled with make+make install.

A further important note: the card does not work with some notebooks which provide too little power to the card (which drains a substantial amount of power). A solution is to attach the card to an external usb hub, with separate power source. However, the card is not always working properly in this case!

---

### Post by chili555 on 2015-05-27
> **andrea-cimatoribus said:**
> A solution is to modify the Makefile in the driver sources, changing the flag that triggers the compilation of 8812au driver too. The driver can then be compiled with make+make install.For the benefit of the searchers, please show the change. I assume it is something like:```
########################## WIFI IC ############################
CONFIG_MULTIDRV = n
CONFIG_RTL8192C = n
CONFIG_RTL8192D = n
CONFIG_RTL8723A = n
CONFIG_RTL8188E = n
CONFIG_RTL8812A = [COLOR="#FF0000"]y[/COLOR]
CONFIG_RTL8821A = y
CONFIG_RTL8192E = n
CONFIG_RTL8723B = n

```Please confirm.

---

### Post by andrea-cimatoribus on 2015-06-06
Yes indeed, that's the change.
Still, the performance of the driver is less than perfect (difficult to get a stable connection, random disconnects, etc.). If you plan to buy an external wifi card and don't need the extra power of this one, get a better supported chip!

---

