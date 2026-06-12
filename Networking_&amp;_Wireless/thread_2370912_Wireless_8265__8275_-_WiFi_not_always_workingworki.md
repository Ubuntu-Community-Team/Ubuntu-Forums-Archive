---
title: "Wireless 8265 / 8275 - WiFi not always working/working slowly"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by pbielak on 2017-09-08
Hi,
I have a fresh installation of Ubuntu 17.04. I have a problem with my wifi card, which speed is not consistent.
Sometimes the internet is working normally, but half of the time the speed is about 0 - 10kb/s. 

Here is the output of lshw -C network command:

  *-network                 
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 03
       serial: 1c:1b:0d:9b:cc:e4
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:f7100000-f711ffff ioport:e000(size=32) memory:f7120000-f7123fff
  *-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 78
       serial: 00:28:f8:3d:53:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-33-generic firmware=22.391740.0 ip=192.168.1.55 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:132 memory:f7000000-f7001fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: 1c:1b:0d:9b:cc:e6
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:133 memory:f7200000-f721ffff

I would really appreciate your help.

Thank you for help,
Przemek

---

### Post by BenginM on 2017-09-09
Hiya , I don't suppose you get the same behavior when you connect with the wired card ethernet cable ! if so, you may want to consult your ISP. Also, are you sharin' the wifi with others in the same place?

please share the output of the following commands under a CODE tag like so, Thanks.

[PHP]
```

$ dmesg | grep iwlwifi
$ ls -l /lib/firmware

```
[/PHP]

#
[URL="https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi"]https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)
[/URL][https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

---

### Post by pbielak on 2017-09-09
Hi,
Yes, the problems are visible while using the WiFi card. The local connection ins't the problem, because I have a thinkpad laptop with 17.04 and the internet is always working correctly.

Here is the output:

```

&#10140;  ~ dmesg | grep iwlwifi
[    2.157858] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    2.157874] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    2.158693] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    2.158884] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    2.164343] iwlwifi 0000:07:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[    2.180822] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    2.194675] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.196557] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.406397] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    2.693754] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.694003] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.809336] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.809588] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.866733] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.867358] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.982241] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.982490] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[ 4808.221110] WARNING: CPU: 0 PID: 10572 at /build/linux-nhaT8l/linux-4.10.0/drivers/net/wireless/intel/iwlwifi/mvm/sta.c:1523 iwl_mvm_rm_sta+0x3e3/0x460 [iwlmvm]
[ 4808.221112] Modules linked in: ccm rfcomm cmac bnep btusb btrtl snd_hda_codec_hdmi arc4 snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_pcm coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc iwlmvm snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd iwlwifi joydev snd input_leds serio_raw cfg80211 soundcore mei_me mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_acpi intel_lpss acpi_als kfifo_buf tpm_infineon industrialio acpi_pad mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 e1000e igb drm_kms_helper dca syscopyarea ptp sysfillrect pps_core sysimgblt
[13183.538357] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.538984] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.653542] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.653791] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.714137] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.714761] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.829480] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[13183.829741] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[15178.626245] WARNING: CPU: 3 PID: 24062 at /build/linux-nhaT8l/linux-4.10.0/drivers/net/wireless/intel/iwlwifi/mvm/sta.c:1523 iwl_mvm_rm_sta+0x3e3/0x460 [iwlmvm]
[15178.626247] Modules linked in: nls_iso8859_1 uas usb_storage ccm rfcomm cmac bnep btusb btrtl snd_hda_codec_hdmi arc4 snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_pcm coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc iwlmvm snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd iwlwifi joydev snd input_leds serio_raw cfg80211 soundcore mei_me mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_acpi intel_lpss acpi_als kfifo_buf tpm_infineon industrialio acpi_pad mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 e1000e igb drm_kms_helper dca syscopyarea
[30235.721148] WARNING: CPU: 1 PID: 2386 at /build/linux-nhaT8l/linux-4.10.0/drivers/net/wireless/intel/iwlwifi/mvm/sta.c:1523 iwl_mvm_rm_sta+0x3e3/0x460 [iwlmvm]
[30235.721149] Modules linked in: nls_iso8859_1 uas usb_storage ccm rfcomm cmac bnep btusb btrtl snd_hda_codec_hdmi arc4 snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_pcm coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc iwlmvm snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd iwlwifi joydev snd input_leds serio_raw cfg80211 soundcore mei_me mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_acpi intel_lpss acpi_als kfifo_buf tpm_infineon industrialio acpi_pad mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 e1000e igb drm_kms_helper dca syscopyarea
[30393.537516] WARNING: CPU: 1 PID: 2386 at /build/linux-nhaT8l/linux-4.10.0/drivers/net/wireless/intel/iwlwifi/mvm/sta.c:1523 iwl_mvm_rm_sta+0x3e3/0x460 [iwlmvm]
[30393.537518] Modules linked in: nls_iso8859_1 uas usb_storage ccm rfcomm cmac bnep btusb btrtl snd_hda_codec_hdmi arc4 snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_pcm coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc iwlmvm snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd iwlwifi joydev snd input_leds serio_raw cfg80211 soundcore mei_me mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_acpi intel_lpss acpi_als kfifo_buf tpm_infineon industrialio acpi_pad mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 e1000e igb drm_kms_helper dca syscopyarea
[32480.505656] WARNING: CPU: 2 PID: 551 at /build/linux-nhaT8l/linux-4.10.0/drivers/net/wireless/intel/iwlwifi/mvm/sta.c:1523 iwl_mvm_rm_sta+0x3e3/0x460 [iwlmvm]
[32480.505657] Modules linked in: nls_iso8859_1 uas usb_storage ccm rfcomm cmac bnep btusb btrtl snd_hda_codec_hdmi arc4 snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_pcm coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc iwlmvm snd_seq_midi snd_seq_midi_event mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer aesni_intel aes_x86_64 crypto_simd glue_helper cryptd iwlwifi joydev snd input_leds serio_raw cfg80211 soundcore mei_me mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_acpi intel_lpss acpi_als kfifo_buf tpm_infineon industrialio acpi_pad mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i915 e1000e igb drm_kms_helper dca syscopyarea
[32484.047793] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.048418] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.163875] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.164136] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.227157] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.227780] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.342747] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32484.342998] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.096725] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.097341] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.213346] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.213609] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.275508] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.276145] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.391901] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[32513.392164] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
&#10140;  ~ ls -l /lib/firmware
total 73096
drwxr-xr-x  2 root root    4096 wrz  2 10:08 3com
drwxr-xr-x 11 root root    4096 kwi 12 05:12 4.10.0-19-generic
drwxr-xr-x 11 root root    4096 wrz  2 10:08 4.10.0-33-generic
drwxr-xr-x  2 root root    4096 wrz  2 10:08 acenic
drwxr-xr-x  2 root root    4096 wrz  2 10:08 adaptec
drwxr-xr-x  2 root root    4096 wrz  2 10:08 advansys
-rw-r--r--  1 root root   50698 kwi 25  2016 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 kwi 25  2016 agere_sta_fw.bin
drwxr-xr-x  2 root root   16384 wrz  2 10:08 amdgpu
drwxr-xr-x  3 root root    4096 wrz  2 10:08 ar3k
-rw-r--r--  1 root root  153416 gru  1  2016 ar5523.bin
-rw-r--r--  1 root root   95500 gru  1  2016 as102_data1_st.hex
-rw-r--r--  1 root root   81820 gru  1  2016 as102_data2_st.hex
drwxr-xr-x  2 root root    4096 wrz  2 10:08 asihpi
drwxr-xr-x 10 root root    4096 kwi 12 05:12 ath10k
-rw-r--r--  1 root root  246804 kwi 21 18:36 ath3k-1.fw
drwxr-xr-x  4 root root    4096 kwi 12 05:12 ath6k
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ath9k_htc
drwxr-xr-x  2 root root    4096 wrz  2 10:08 atmel
-rw-r--r--  1 root root   35180 kwi 21 18:36 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 kwi 21 18:36 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root    9726 kwi 25  2016 atmsar11.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 atusb
drwxr-xr-x  2 root root    4096 wrz  2 10:08 av7110
drwxr-xr-x  2 root root    4096 wrz  2 10:08 bnx2x
drwxr-xr-x  2 root root    4096 wrz  2 10:08 brcm
-rw-r--r--  1 root root   13388 gru  1  2016 carl9170-1.fw
drwxr-xr-x  9 root root    4096 wrz  2 10:08 carl9170fw
-rw-r--r--  1 root root  412528 kwi 25  2016 cbfw-3.2.1.1.bin
-rw-r--r--  1 root root  414016 kwi 25  2016 cbfw-3.2.3.0.bin
-rw-r--r--  1 root root  414480 gru  1  2016 cbfw-3.2.5.1.bin
drwxr-xr-x  3 root root    4096 wrz  2 10:08 cis
-rw-r--r--  1 root root     107 gru  1  2016 configure
drwxr-xr-x  2 root root    4096 wrz  2 10:08 cpia2
-rw-r--r--  1 root root  582440 kwi 25  2016 ct2fw-3.2.1.1.bin
-rw-r--r--  1 root root  583688 kwi 25  2016 ct2fw-3.2.3.0.bin
-rw-r--r--  1 root root  584216 gru  1  2016 ct2fw-3.2.5.1.bin
-rw-r--r--  1 root root  655436 gru  1  2016 ctefx.bin
-rw-r--r--  1 root root  537160 kwi 25  2016 ctfw-3.2.1.1.bin
-rw-r--r--  1 root root  538712 kwi 25  2016 ctfw-3.2.3.0.bin
-rw-r--r--  1 root root  539144 gru  1  2016 ctfw-3.2.5.1.bin
-rw-r--r--  1 root root    4120 gru  1  2016 ctspeq.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 cxgb3
drwxr-xr-x  2 root root    4096 wrz  2 10:08 cxgb4
drwxr-xr-x  2 root root    4096 wrz  2 10:08 dsp56k
-rw-r--r--  1 root root   18643 gru  1  2016 dvb-fe-xc4000-1.4.1.fw
-rw-r--r--  1 root root   12401 kwi 25  2016 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   16497 gru  1  2016 dvb-fe-xc5000c-4.1.30.7.fw
-rw-r--r--  1 root root   33768 kwi 25  2016 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    8128 gru  1  2016 dvb-usb-it9135-01.fw
-rw-r--r--  1 root root    5834 gru  1  2016 dvb-usb-it9135-02.fw
-rw-r--r--  1 root root   50222 kwi 25  2016 dvb-usb-terratec-h5-drxk.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ea
drwxr-xr-x  2 root root    4096 wrz  2 10:08 edgeport
drwxr-xr-x  2 root root    4096 wrz  2 10:08 emi26
drwxr-xr-x  2 root root    4096 wrz  2 10:08 emi62
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ene-ub6250
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ess
-rw-r--r--  1 root root  180776 kwi 25  2016 f2255usb.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 go7007
-rw-r--r--  1 root root   32252 kwi 21 18:36 hfi1_dc8051.fw
-rw-r--r--  1 root root   16848 gru  1  2016 hfi1_fabric.fw
-rw-r--r--  1 root root   33296 kwi 21 18:36 hfi1_pcie.fw
-rw-r--r--  1 root root     532 kwi 21 18:36 hfi1_platform.dat
-rw-r--r--  1 root root    5360 gru  1  2016 hfi1_sbus.fw
drwxr-xr-x  2 root root    4096 pa&#378;  8  2016 hp
-rw-r--r--  1 root root   72684 gru  9  2016 htc_7010.fw
-rw-r--r--  1 root root   50980 gru  9  2016 htc_9271.fw
-rw-r--r--  1 root root 1251036 kwi 25  2016 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root 1334532 kwi 25  2016 i2400m-fw-usb-1.5.sbcf
-rw-r--r--  1 root root 1531932 kwi 25  2016 i6050-fw-usb-1.5.sbcf
drwxr-xr-x  2 root root    4096 wrz  2 10:08 i915
drwxr-xr-x  2 root root    4096 wrz  2 10:08 intel
drwxr-xr-x  2 root root    4096 wrz  2 10:08 intel-ucode
-rw-r--r--  1 root root  209190 kwi 21 18:36 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 kwi 21 18:36 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 kwi 21 18:36 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 kwi 21 18:36 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 kwi 21 18:36 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 kwi 21 18:36 ipw2200-sniffer.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 isci
-rw-r--r--  1 root root  337520 kwi 25  2016 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 kwi 25  2016 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  689680 kwi 25  2016 iwlwifi-105-6.ucode
-rw-r--r--  1 root root  701228 kwi 25  2016 iwlwifi-135-6.ucode
-rw-r--r--  1 root root  695876 kwi 25  2016 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root  707392 kwi 25  2016 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root  609892 gru  1  2016 iwlwifi-3160-10.ucode
-rw-r--r--  1 root root  683996 gru  1  2016 iwlwifi-3160-12.ucode
-rw-r--r--  1 root root  688616 gru  1  2016 iwlwifi-3160-13.ucode
-rw-r--r--  1 root root  918212 gru  1  2016 iwlwifi-3160-16.ucode
-rw-r--r--  1 root root  918268 kwi 19 20:27 iwlwifi-3160-17.ucode
-rw-r--r--  1 root root  670484 kwi 25  2016 iwlwifi-3160-7.ucode
-rw-r--r--  1 root root  667284 kwi 25  2016 iwlwifi-3160-8.ucode
-rw-r--r--  1 root root  669872 gru  1  2016 iwlwifi-3160-9.ucode
-rw-r--r--  1 root root 1384856 gru  9  2016 iwlwifi-3168-21.ucode
-rw-r--r--  1 root root 1028032 gru  9  2016 iwlwifi-3168-22.ucode
-rw-r--r--  1 root root  150100 kwi 25  2016 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 kwi 25  2016 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  340696 kwi 21 18:36 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 kwi 25  2016 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 kwi 25  2016 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 kwi 25  2016 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  677296 kwi 25  2016 iwlwifi-6000g2a-6.ucode
-rw-r--r--  1 root root  679436 kwi 25  2016 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root  469780 kwi 25  2016 iwlwifi-6050-5.ucode
-rw-r--r--  1 root root  672352 gru  1  2016 iwlwifi-7260-10.ucode
-rw-r--r--  1 root root  782300 gru  1  2016 iwlwifi-7260-12.ucode
-rw-r--r--  1 root root  786920 gru  1  2016 iwlwifi-7260-13.ucode
-rw-r--r--  1 root root 1049284 gru  1  2016 iwlwifi-7260-16.ucode
-rw-r--r--  1 root root 1049340 kwi 19 20:27 iwlwifi-7260-17.ucode
-rw-r--r--  1 root root  683236 kwi 25  2016 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 gru  1  2016 iwlwifi-7260-8.ucode
-rw-r--r--  1 root root  680508 gru  1  2016 iwlwifi-7260-9.ucode
-rw-r--r--  1 root root  736844 gru  1  2016 iwlwifi-7265-10.ucode
-rw-r--r--  1 root root  880604 gru  1  2016 iwlwifi-7265-12.ucode
-rw-r--r--  1 root root  885224 gru  1  2016 iwlwifi-7265-13.ucode
-rw-r--r--  1 root root 1180356 gru  1  2016 iwlwifi-7265-16.ucode
-rw-r--r--  1 root root 1180412 kwi 19 20:27 iwlwifi-7265-17.ucode
-rw-r--r--  1 root root  690452 kwi 25  2016 iwlwifi-7265-8.ucode
-rw-r--r--  1 root root  697828 gru  1  2016 iwlwifi-7265-9.ucode
lrwxrwxrwx  1 root root      21 gru  9  2016 iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r--  1 root root 1002800 gru  1  2016 iwlwifi-7265D-12.ucode
-rw-r--r--  1 root root 1008692 gru  1  2016 iwlwifi-7265D-13.ucode
-rw-r--r--  1 root root 1384500 gru  1  2016 iwlwifi-7265D-16.ucode
-rw-r--r--  1 root root 1383604 gru  9  2016 iwlwifi-7265D-17.ucode
-rw-r--r--  1 root root 1385368 gru  9  2016 iwlwifi-7265D-21.ucode
-rw-r--r--  1 root root 1028376 kwi 19 20:27 iwlwifi-7265D-22.ucode
-rw-r--r--  1 root root 1745176 gru  1  2016 iwlwifi-8000C-13.ucode
-rw-r--r--  1 root root 2351636 gru  1  2016 iwlwifi-8000C-16.ucode
-rw-r--r--  1 root root 2394060 gru  9  2016 iwlwifi-8000C-21.ucode
-rw-r--r--  1 root root 2389968 gru  9  2016 iwlwifi-8265-21.ucode
-rw-r--r--  1 root root 1811984 kwi 19 20:27 iwlwifi-8265-22.ucode
drwxr-xr-x  2 root root    4096 wrz  2 10:08 kaweth
drwxr-xr-x  2 root root    4096 wrz  2 10:08 keyspan
drwxr-xr-x  2 root root    4096 wrz  2 10:08 keyspan_pda
drwxr-xr-x  2 root root    4096 wrz  2 10:08 korg
-rw-r--r--  1 root root  118888 kwi 25  2016 lbtf_usb.bin
-rw-r--r--  1 root root     262 kwi 25  2016 lgs8g75.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 libertas
drwxr-xr-x  2 root root    4096 wrz  2 10:08 liquidio
drwxr-xr-x  2 root root    4096 wrz  2 10:08 matrox
drwxr-xr-x  2 root root    4096 wrz  2 10:08 moxa
drwxr-xr-x  2 root root    4096 wrz  2 10:08 mrvl
-rw-r--r--  1 root root   45412 gru  1  2016 mt7601u.bin
-rw-r--r--  1 root root  368220 gru  1  2016 mt7650.bin
-rw-r--r--  1 root root   13847 kwi 25  2016 mts_cdma.fw
-rw-r--r--  1 root root   14067 kwi 25  2016 mts_edge.fw
-rw-r--r--  1 root root   13847 kwi 25  2016 mts_gsm.fw
-rw-r--r--  1 root root   13769 kwi 25  2016 mts_mt9234mu.fw
-rw-r--r--  1 root root   13769 kwi 25  2016 mts_mt9234zba.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 mwl8k
drwxr-xr-x  2 root root    4096 wrz  2 10:08 mwlwifi
-rw-r--r--  1 root root  378832 gru  1  2016 myri10ge_eth_big_z8e.dat
-rw-r--r--  1 root root  389144 gru  1  2016 myri10ge_ethp_big_z8e.dat
-rw-r--r--  1 root root  389056 gru  1  2016 myri10ge_ethp_z8e.dat
-rw-r--r--  1 root root  378736 gru  1  2016 myri10ge_eth_z8e.dat
-rw-r--r--  1 root root  536192 gru  1  2016 myri10ge_rss_eth_big_z8e.dat
-rw-r--r--  1 root root  545936 gru  1  2016 myri10ge_rss_ethp_big_z8e.dat
-rw-r--r--  1 root root  545920 gru  1  2016 myri10ge_rss_ethp_z8e.dat
-rw-r--r--  1 root root  536176 gru  1  2016 myri10ge_rss_eth_z8e.dat
-rw-r--r--  1 root root   15664 kwi 21 18:36 NPE-B
-rw-r--r--  1 root root   15664 kwi 21 18:36 NPE-C
drwxr-xr-x 10 root root    4096 kwi 12 05:12 nvidia
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ositech
-rw-r--r--  1 root root 1845305 gru  1  2016 phanfw.bin
-rw-r--r--  1 root root  463612 gru  1  2016 qat_895xcc.bin
-rw-r--r--  1 root root  114176 gru  1  2016 qat_895xcc_mmp.bin
-rw-r--r--  1 root root  265444 gru  1  2016 qat_c3xxx.bin
-rw-r--r--  1 root root  114820 gru  1  2016 qat_c3xxx_mmp.bin
-rw-r--r--  1 root root  398144 gru  1  2016 qat_c62x.bin
-rw-r--r--  1 root root  114820 gru  1  2016 qat_c62x_mmp.bin
lrwxrwxrwx  1 root root      18 gru  1  2016 qat_mmp.bin -> qat_895xcc_mmp.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 qca
drwxr-xr-x  2 root root    4096 wrz  2 10:08 qed
-rw-r--r--  1 root root   76802 kwi 25  2016 ql2100_fw.bin
-rw-r--r--  1 root root   84566 kwi 25  2016 ql2200_fw.bin
-rw-r--r--  1 root root  125252 gru  1  2016 ql2300_fw.bin
-rw-r--r--  1 root root  136038 gru  1  2016 ql2322_fw.bin
-rw-r--r--  1 root root  265176 kwi 21 18:36 ql2400_fw.bin
-rw-r--r--  1 root root  274968 kwi 21 18:36 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 r128
-rw-r--r--  1 root root    9452 gru  1  2016 r8a779x_usb3_v1.dlmem
-rw-r--r--  1 root root    9416 mar 28 21:01 r8a779x_usb3_v2.dlmem
-rw-r--r--  1 root root    9416 mar 28 21:01 r8a779x_usb3_v3.dlmem
drwxr-xr-x  2 root root   36864 wrz  2 10:08 radeon
-rw-r--r--  1 root root    1684 kwi 21 18:36 README
drwxr-xr-x  2 root root    4096 wrz  2 10:08 rockchip
-rw-r--r--  1 root root      63 gru  1  2016 rp2.fw
-rw-r--r--  1 root root   94100 gru  1  2016 rsi_91x.fw
-rw-r--r--  1 root root    8192 kwi 25  2016 rt2561.bin
-rw-r--r--  1 root root    8192 kwi 25  2016 rt2561s.bin
-rw-r--r--  1 root root    8192 kwi 25  2016 rt2661.bin
-rw-r--r--  1 root root    8192 kwi 21 18:36 rt2860.bin
-rw-r--r--  1 root root    8192 kwi 21 18:36 rt2870.bin
lrwxrwxrwx  1 root root      10 kwi 25  2016 rt3070.bin -> rt2870.bin
lrwxrwxrwx  1 root root      10 kwi 25  2016 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    4096 kwi 21 18:36 rt3290.bin
-rw-r--r--  1 root root    2048 kwi 25  2016 rt73.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 RTL8192E
drwxr-xr-x  2 root root    4096 wrz  2 10:08 rtl_bt
drwxr-xr-x  2 root root    4096 wrz  2 10:08 rtl_nic
drwxr-xr-x  2 root root    4096 wrz  2 10:08 rtlwifi
lrwxrwxrwx  1 root root      17 gru  1  2016 s2250.fw -> go7007/s2250-2.fw
lrwxrwxrwx  1 root root      17 gru  1  2016 s2250_loader.fw -> go7007/s2250-1.fw
-rw-r--r--  1 root root  352652 gru  9  2016 s5p-mfc.fw
-rw-r--r--  1 root root  306312 gru  9  2016 s5p-mfc-v6.fw
-rw-r--r--  1 root root  343756 gru  9  2016 s5p-mfc-v6-v2.fw
-rw-r--r--  1 root root  382724 gru  9  2016 s5p-mfc-v7.fw
-rw-r--r--  1 root root  360576 gru  9  2016 s5p-mfc-v8.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 sb16
drwxr-xr-x  2 root root    4096 wrz  2 10:08 scripts
-rw-r--r--  1 root root     816 gru  1  2016 sdd_sagrad_1091_1098.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 slicoss
drwxr-xr-x  2 root root    4096 wrz  2 10:08 sun
drwxr-xr-x  2 root root    4096 wrz  2 10:08 tehuti
-rw-r--r--  1 root root   13765 kwi 25  2016 ti_3410.fw
-rw-r--r--  1 root root   13764 kwi 25  2016 ti_5052.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ti-connectivity
drwxr-xr-x  2 root root    4096 wrz  2 10:08 tigon
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ti-keystone
-rw-r--r--  1 root root   51972 kwi 25  2016 tlg2300_firmware.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ttusb-budget
drwxr-xr-x  2 root root    4096 wrz  2 10:08 ueagle-atm
drwxr-xr-x  2 root root    4096 wrz  2 10:08 usbdux
-rw-r--r--  1 root root     999 kwi 25  2016 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 kwi 25  2016 usbdux_firmware.bin
-rw-r--r--  1 root root    8192 sty  6  2017 usbduxsigma_firmware.bin
-rw-r--r--  1 root root   16382 kwi 25  2016 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 kwi 25  2016 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 kwi 25  2016 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 kwi 25  2016 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 kwi 21 18:36 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 kwi 21 18:36 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 kwi 21 18:36 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 kwi 25  2016 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 kwi 25  2016 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 kwi 21 18:36 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 kwi 21 18:36 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 vicam
-rw-r--r--  1 root root   11341 kwi 25  2016 vntwusb.fw
-rw-r--r--  1 root root 4082928 kwi 21 18:36 vpu_d.bin
-rw-r--r--  1 root root  131160 kwi 21 18:36 vpu_p.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 vxge
-rw-r--r--  1 root root    4685 kwi 21 18:36 WHENCE.ubuntu
-rw-r--r--  1 root root   23554 kwi 25  2016 whiteheat.fw
-rw-r--r--  1 root root    5626 kwi 25  2016 whiteheat_loader.fw
-rw-r--r--  1 root root   97824 gru  1  2016 wsm_22.bin
drwxr-xr-x  2 root root    4096 wrz  2 10:08 yam
drwxr-xr-x  2 root root    4096 wrz  2 10:08 yamaha
-rw-r--r--  1 root root   62484 kwi 21 18:36 zd1201-ap.fw
-rw-r--r--  1 root root   70612 kwi 21 18:36 zd1201.fw
drwxr-xr-x  2 root root    4096 wrz  2 10:08 zd1211
&#10140;  ~ 



```


Thanks a lot for a reply.

---

### Post by BenginM on 2017-09-09
As you can see from in the result of dmesg iwlwifi ..The kernel driver iwlwifi tries to find one of the supported versions, starting from highest and going down to the lowest .. but those are not present in the system. and the kernel currently loading 22-ucode but it might be broken!

So,try this, download and load a newer Intel micorcode firmware for the card ..

$ cd /lib/firmware
$ wget [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-31.ucode](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-31.ucode)

Reboot.
# is the card now stable with proper speed?

---

### Post by jeremy31 on 2017-09-09
From the dmesg output, I would think the highest firmware version that kernel would load is -26

The 4.4 source code contains
```
/* Highest firmware API version supported */
#define IWL8000_UCODE_API_MAX	19

/* Oldest version we won't warn about */
#define IWL8000_UCODE_API_OK	13

/* Lowest firmware API version supported */
#define IWL8000_UCODE_API_MIN	13
```
The IWL8000_UCODE_API_MAX must be 26 in 17.04

---

### Post by BenginM on 2017-09-09
I would've though the same , but their /lib/firmware directory shows only iwlwifi-8265-21,22.ucode are present , and only -27,31 are available on the web , at least [in here]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/") .

---

### Post by jeremy31 on 2017-09-09
The absence of those versions likely means Intel had issues with them and didn't release them to linux-firmware upstream.  I think it was possible at one point in time to rename a firmware version to fool the iwlmvm module, I am not sure if it still works

---

### Post by pbielak on 2017-09-10
Hi,
Adding driver version 31 does not help, it is not seen by ubuntu:
```

przemek@przemek-desktop:~$ dmesg | grep iwlwifi
[    2.215170] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    2.215189] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    2.216776] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    2.219577] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    2.224339] iwlwifi 0000:07:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[    2.248238] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    2.250269] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.250903] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.449602] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    3.142378] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.142634] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.257946] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.258195] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.318065] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.318674] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.433361] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.433610] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled

```

I tried to rename firmware 31 with 22 name and restarted my computer. The only result was that ubuntu couldn't launch any programs and was starting 15 minutes :) I manually restored 22 file in recovery mode, but the wifi is still the same.

Bests,
Przemek

---

### Post by BenginM on 2017-09-10
Does iwlwifi-8265-31.ucode , exist under /lib/firmware ? 
$ cd /lib/firmware
 remove it with 
$ rm -f iwlwifi-8265-31.ucode

get Core28 iwlwifi-8265-31 from [this source]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release") : make sure you have a network connection , Ethernet card is working i suppose !

cd /lib/firmware 
wget [https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8265-31.ucode](https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8265-31.ucode)

you can also get Core24 -27.ucode from the same source. but to use -27 when -31 exist, you need to rename iwlwifi-8265-31.ucode , to something like iwlwifi-8265-31.ucode.NEW , so it won't be picked, instead -27 will.

---

### Post by pbielak on 2017-09-10
Hi,
I downloaded both 27 and 31 version form your source, but in dmesg it still is not searching for those versions:

```

przemek@przemek-desktop:/lib/firmware$ ls | grep 8265
iwlwifi-8265-21.ucode
iwlwifi-8265-22.ucode
iwlwifi-8265-27.ucode
iwlwifi-8265-31.ucode
przemek@przemek-desktop:/lib/firmware$ dmesg | grep wifi
[    2.206678] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    2.206690] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    2.208717] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    2.209588] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    2.214934] iwlwifi 0000:07:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[    2.237180] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    2.241549] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.242162] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.397523] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    3.121179] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.121428] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.236922] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.237176] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.296659] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.297271] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.412730] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.413006] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled

```

I restarted the computer after copying those files.

---

### Post by BenginM on 2017-09-10
Rename 
iwlwifi-8265-22.ucode.BROKEN

reload the driver..

$ modprobe -r iwlwifi ; modprobe iwlwifi 
$ dmesg | grep iwlwifi
  
is 31 loaded now!

---

### Post by chili555 on 2017-09-10
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by pbielak on 2017-09-11
Hello Bengin,
Do I need also need to rename other, older files, such as 21? Because after typing those commands, 31 driver is not loaded, only 21:

```

przemek@przemek-desktop:~$ dmesg | grep iwlwifi
[    2.887461] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    2.887477] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    2.889763] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    2.891406] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    2.891418] iwlwifi 0000:07:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[    2.900324] iwlwifi 0000:07:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[    2.920700] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    2.921752] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.922367] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.158113] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    3.800952] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.801199] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.917451] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.917700] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.976980] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.977601] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    4.094661] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    4.094910] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled

```

---

### Post by BenginM on 2017-09-11
Hiya pbielak , yes try to rename -21.code.OLD , now see if -31 is loaded :
$ modprobe -r iwlwifi ; modprobe iwlwifi 
$ dmesg | grep iwlwifi

if -31 still doesn't load , rename it to -31.ucode.NEW , and try to load -27 .

if either -31 or -27 loads then test it for sometimes.

---

### Post by pbielak on 2017-09-11
Hi Bengin,
Unfortunately it did not help, after renaming these files, the system is not loading any drivers and wifi is not working at all.

---

### Post by BenginM on 2017-09-11
I'm not sure why -27, -31 refuse to load .. try to rename 8265-21.code.OLD back to 8265-21.code

$ modprobe -r iwlwifi ; modprobe iwlwifi 
$ dmesg | grep iwlwifi

test the connection stability and speed with -21 for awhile , see if it's better and without the -22 behavior! , and don't forget to follow chili's advice ... report back to us here. can you please show us what ls -l /lib/firmware looks like now, just to make sure the files are named correctly.[COLOR=#000000][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][/COLOR]

---

### Post by pbielak on 2017-09-12
Hi,
I will test it in a week and let you know.
Anyway, thank you very much for helping me!

---

