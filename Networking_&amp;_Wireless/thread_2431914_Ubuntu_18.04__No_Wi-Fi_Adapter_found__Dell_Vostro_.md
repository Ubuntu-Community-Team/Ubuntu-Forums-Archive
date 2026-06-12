---
title: "Ubuntu 18.04 | No Wi-Fi Adapter found | Dell Vostro 5490"
date: 2019-11-23
forum: Networking &amp; Wireless
---

### Post by dperez646 on 2019-11-23
Ubuntu cannot detect the Wi-Fi adapter on my laptop, but bluetooth and ethernet connections work. Ethernet, Wi-Fi and bluetooth connections work using Win10. 

I disabled Secure Boot in BIOS (as mentioned in another thread), but that did not fix the issue. I confirmed WLAN setting is enabled in BIOS.

wireless-info.txt can be found at [https://pastebin.com/f5W08Bcc](https://pastebin.com/f5W08Bcc)

Any other suggestions to try to get wifi working?

==Laptop==
* Dell Vostro 5490
* Dual boot of Win10 & Ubuntu 18.04
* Intel Wireless AC 9462

---

### Post by gnusci on 2019-11-23
Did you try the steps from thisweb:

[https://www.dell.com/support/article/ca/en/cabsdt1/sln151759/how-to-troubleshoot-wireless-network-issues-in-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/ca/en/cabsdt1/sln151759/how-to-troubleshoot-wireless-network-issues-in-ubuntu-linux-on-your-dell-pc?lang=en)

---

### Post by dperez646 on 2019-11-23
I followed the steps in the dell support article mentioned in the previous post, here are my conclusions:
Regarding *Troubleshooting Hardware *steps, 1) I don't see the Wi-Fi adapter using the Ubuntu Live Media 2) I don't have another machine to try the wifi card with to confirm the status of it.
Regarding *Troubleshooting Software* steps, when I run the command [FONT=courier new]sudo lshw -c network[/FONT], I get the following output. It seems that the wi-fi hardware is found, but it's not recognized as a Wi-Fi adapter. I stopped at this point.
```

  *-network                 
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:c2318000-c231bfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: e4:54:e8:31:3d:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.7.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:c2204000-c2204fff memory:c2200000-c2203fff

```

---

### Post by praseodym on 2019-11-24
Please run
```

sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

### Post by dperez646 on 2019-11-24
Here is the output of the **[FONT=courier new]modprobe[/FONT]** & **[FONT=courier new]dmesg[/FONT]** commands from the previous comment. Still have status of "No Wi-Fi adapter found".

```

username@ubuntu:~$ sudo modprobe -rfv iwlwifi
[sudo] password for username: 
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod mac80211
rmmod cfg80211
username@ubuntu:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/5.0.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/5.0.0-36-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 
username@ubuntu:~$ dmesg | grep iwl
[    2.009039] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    2.049111] iwlwifi 0000:00:14.3: loaded firmware version 43.95eb4e97.0 op_mode iwlmvm
[    2.076080] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9462, REV=0x354
[    4.400434] Modules linked in: dell_laptop(+) snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915(+) snd_rawmidi kvmgt vfio_mdev iwlmvm(+) aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau(+) intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect sysimgblt intel_lpss_pci(+) ucsi_acpi intel_soc_dts_iosf typec_ucsi mac_hid intel_lpss
[    7.266461] iwlwifi 0000:00:14.3: Failed to load firmware chunk!
[    7.266464] iwlwifi 0000:00:14.3: iwlwifi transaction failed, dumping registers
[    7.266465] iwlwifi 0000:00:14.3: iwlwifi device config registers:
[    7.266544] iwlwifi 0000:00:14.3: 00000000: 02f08086 00100406 02800000 00800000 c2318004 00000000 00000000 00000000
[    7.266546] iwlwifi 0000:00:14.3: 00000020: 00000000 00000000 00000000 42a48086 00000000 000000c8 00000000 000001ff
[    7.266546] iwlwifi 0000:00:14.3: iwlwifi device memory mapped registers:
[    7.266574] iwlwifi 0000:00:14.3: 00000000: 00489004 00000040 00000000 00000000 00000000 00000000 00000000 00000000
[    7.266575] iwlwifi 0000:00:14.3: 00000020: 00000011 0c040005 00000351 d55555d5 d55555d5 d55555d5 80008040 001f0040
[    7.266622] iwlwifi 0000:00:14.3: Could not load the [0] uCode section
[    7.266625] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -110
[    7.266627] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.
[    7.485487] iwlwifi 0000:00:14.3: Failing on timeout while stopping DMA channel 8 [0x0bad1122]
[    7.497638] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
[   17.404238] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   19.577576] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   21.579249] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   23.580917] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   25.582753] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   27.584459] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   29.586056] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   31.587709] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   33.615826] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   35.617559] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   37.634149] Modules linked in: cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   46.027447] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   48.029229] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   50.031229] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   67.123704] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   69.408777] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   71.410587] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   73.412257] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   75.414017] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   77.423574] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   77.434750] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   77.445766] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[   79.447316] Modules linked in: rfcomm cmac bnep joydev snd_hda_codec_hdmi hid_multitouch snd_hda_codec_realtek snd_hda_codec_generic dell_laptop snd_hda_intel ledtrig_audio snd_hda_codec dell_smm_hwmon snd_hda_core intel_rapl x86_pkg_temp_thermal snd_hwdep intel_powerclamp coretemp kvm_intel nls_iso8859_1 snd_pcm snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915 snd_rawmidi kvmgt vfio_mdev iwlmvm aesni_intel mdev mac80211 aes_x86_64 crypto_simd cryptd vfio_iommu_type1 glue_helper vfio nouveau intel_cstate snd_seq intel_rapl_perf kvm snd_seq_device snd_timer btusb snd btrtl btbcm dell_wmi btintel uvcvideo irqbypass bluetooth mxm_wmi input_leds videobuf2_vmalloc ttm videobuf2_memops serio_raw videobuf2_v4l2 dell_smbios drm_kms_helper videobuf2_common iwlwifi videodev drm dcdbas idma64 virt_dma wmi_bmof intel_wmi_thunderbolt media cfg80211 soundcore ecdh_generic dell_wmi_descriptor i2c_algo_bit fb_sys_fops processor_thermal_device syscopyarea sysfillrect
[43923.745968] iwlwifi 0000:00:14.3: loaded firmware version 43.95eb4e97.0 op_mode iwlmvm
[43923.756443] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9462, REV=0x354
[43928.911105] iwlwifi 0000:00:14.3: Failed to load firmware chunk!
[43928.911115] iwlwifi 0000:00:14.3: iwlwifi transaction failed, dumping registers
[43928.911119] iwlwifi 0000:00:14.3: iwlwifi device config registers:
[43928.911177] iwlwifi 0000:00:14.3: 00000000: 02f08086 00100406 02800000 00800000 c2318004 00000000 00000000 00000000
[43928.911184] iwlwifi 0000:00:14.3: 00000020: 00000000 00000000 00000000 42a48086 00000000 000000c8 00000000 000001ff
[43928.911187] iwlwifi 0000:00:14.3: iwlwifi device memory mapped registers:
[43928.911232] iwlwifi 0000:00:14.3: 00000000: 18489004 00000040 00000000 00000000 00000000 00000000 00000000 00000000
[43928.911238] iwlwifi 0000:00:14.3: 00000020: 00000011 0c040005 00000351 d55555d5 d55555d5 d55555d5 80008040 001f0040
[43928.911266] iwlwifi 0000:00:14.3: Could not load the [0] uCode section
[43928.911295] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -110
[43928.911301] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.
[43929.136778] iwlwifi 0000:00:14.3: Failing on timeout while stopping DMA channel 8 [0x0bad1122]
[43929.149378] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110

```

---

### Post by praseodym on 2019-11-24
Install a mainline kernel as described here

[https://askubuntu.com/questions/1148383/no-wifi-networks-listed-on-19-04-with-intel-wifi-link-5350](https://askubuntu.com/questions/1148383/no-wifi-networks-listed-on-19-04-with-intel-wifi-link-5350)

---

### Post by dperez646 on 2019-11-24
I followed the instructions in the ***Answer*** from the [https://askubuntu.com/questions/1148383/no-wifi-networks-listed-on-19-04-with-intel-wifi-link-5350](https://askubuntu.com/questions/1148383/no-wifi-networks-listed-on-19-04-with-intel-wifi-link-5350). 

After installing the *.deb packages for the** mainline kernel**, I rebooted my laptop. On restart, I select Ubuntu in grub menu, but the** Ubuntu does not boot up successfully** and I see the following output below while the system hangs.  To exit out of the hung system, I need to force shutdown the machine by holding the power button on the laptop. I am able to boot into Ubuntu from grub using a previous image (before I installed the mainline kernel).

Here's the output from Ubuntu when boot up hangs:
```

/dev/nvme0n1p7: clean, 213683/2747136 files, 2386013/10986240 blocks
[      4.472299] nouveau 0000:01:00.0: DRM Pointer to TMDS table invalid

```


Here's the output from installing the  mainline kernel *.deb packages
```

username@ubuntu:~/Downloads/mainline_kernel$ ls -la
total 65316
drwxrwxr-x 2 username username     4096 Nov 24 14:38 .
drwxr-xr-x 3 username username     4096 Nov 24 14:37 ..
-rw-rw-r-- 1 username username 10747288 Nov 24 14:37 linux-headers-5.1.6-050106_5.1.6-050106.201905311031_all.deb
-rw-rw-r-- 1 username username  1141788 Nov 24 14:37 linux-headers-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb
-rw-rw-r-- 1 username username  8479088 Nov 24 14:37 linux-image-unsigned-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb
-rw-rw-r-- 1 username username 46500904 Nov 24 14:38 linux-modules-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb
username@ubuntu:~/Downloads/mainline_kernel$ sudo dpkg -i linux*.deb
[sudo] password for username: 
Selecting previously unselected package linux-headers-5.1.6-050106.
(Reading database ... 162205 files and directories currently installed.)
Preparing to unpack linux-headers-5.1.6-050106_5.1.6-050106.201905311031_all.deb ...
Unpacking linux-headers-5.1.6-050106 (5.1.6-050106.201905311031) ...
Selecting previously unselected package linux-headers-5.1.6-050106-generic.
Preparing to unpack linux-headers-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb ...
Unpacking linux-headers-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
Selecting previously unselected package linux-image-unsigned-5.1.6-050106-generic.
Preparing to unpack linux-image-unsigned-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb ...
Unpacking linux-image-unsigned-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
Selecting previously unselected package linux-modules-5.1.6-050106-generic.
Preparing to unpack linux-modules-5.1.6-050106-generic_5.1.6-050106.201905311031_amd64.deb ...
Unpacking linux-modules-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
Setting up linux-headers-5.1.6-050106 (5.1.6-050106.201905311031) ...
Setting up linux-headers-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
Setting up linux-modules-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
Setting up linux-image-unsigned-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-5.0.0-36-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-5.0.0-36-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-5.1.6-050106-generic
I: /initrd.img is now a symlink to boot/initrd.img-5.1.6-050106-generic
Processing triggers for linux-image-unsigned-5.1.6-050106-generic (5.1.6-050106.201905311031) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.1.6-050106-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.1.6-050106-generic
Found initrd image: /boot/initrd.img-5.1.6-050106-generic
Found linux image: /boot/vmlinuz-5.0.0-36-generic
Found initrd image: /boot/initrd.img-5.0.0-36-generic
Found linux image: /boot/vmlinuz-5.0.0-32-generic
Found initrd image: /boot/initrd.img-5.0.0-32-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done


```

---

### Post by dperez646 on 2019-11-25
I was able to get the Wi-Fi adapter **working successfully** on may laptop. I executed the commands in the ***Answer*** at [https://askubuntu.com/questions/1182722/intel-wireless-ac-9462-not-working-w-18-04-lts](https://askubuntu.com/questions/1182722/intel-wireless-ac-9462-not-working-w-18-04-lts).

Thank you for the help, **praseodym** and **gnusci**.

The commands executed from the ***Answer*** to get the wi-fi adapter (Intel(R) Dual Band Wireless AC 9462)  working were:
```

sudo apt update
sudo apt install git build-essential
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi/
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
sudo modprobe iwlwifi
```

---

