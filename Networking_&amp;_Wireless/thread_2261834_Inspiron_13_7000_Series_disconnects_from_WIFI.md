---
title: "Inspiron 13 7000 Series disconnects from WIFI"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2015-01-21
My wife's Dell has recently started diconnecting from WIFI. Every time she has either simply reconnect (as it asks for password again) or turn off/on wireless. I tried to follow some recommendations from this forum but it did not help. I am attaching the results of the wireless script and our router's setup in case someone could take a look.

---

### Post by chili555 on 2015-01-21
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

If these changes are ineffective, reboot and let us see:```
dmesg | grep iwl
```

---

### Post by foxy123 on 2015-01-21
> **chili555 said:**
> First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

If these changes are ineffective, reboot and let us see:```
dmesg | grep iwl
```

It is already set to WPA2-AES (as far as I can see from the router settings). I have set the channel width to 20MHz. Just in case I have run dmesg, see below.

```
$ dmesg | grep iwl
[    6.775743] iwlwifi 0000:01:00.0: irq 59 for MSI/MSI-X
[    6.785405] iwlwifi 0000:01:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    7.090068] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x184
[    7.090120] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[    7.090276] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[    7.125572] Modules linked in: intel_rapl(+) x86_pkg_temp_thermal hid_sensor_gyro_3d hid_sensor_accel_3d hid_sensor_als i915(+) intel_powerclamp iwlmvm(+) hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer mac80211 kfifo_buf coretemp industrialio dell_wmi sparse_keymap hid_sensor_iio_common snd_hda_codec_realtek kvm_intel nls_iso8859_1 drm_kms_helper uvcvideo videobuf2_vmalloc snd_hda_intel drm snd_hda_codec dell_laptop dcdbas kvm snd_hwdep snd_pcm iwlwifi videobuf2_memops crct10dif_pclmul snd_page_alloc crc32_pclmul ghash_clmulni_intel videobuf2_core aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 lrw gf128mul snd_rawmidi glue_helper hid_multitouch ablk_helper hid_sensor_hub cryptd videodev btusb joydev snd_seq mei_me cfg80211 wmi i2c_algo_bit snd_seq_device bluetooth mei serio_raw parport_pc ppdev snd_timer lpc_ich snd lp i2c_designware_platform soundcore i2c_designware_core video mac_hid parport hid_generic usbhid hid psmouse ahci libahci
[    7.152710] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.476372] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[    9.476533] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[ 4353.702212] iwlwifi 0000:01:00.0: Time Event end notification failure

```

---

### Post by chili555 on 2015-01-21
Still looks pretty normal until the last line. May we also see: ```
dmesg | grep 80211
```This is the first Intel 7265 device I've seen, so I am anxious to learn its peculiarities.

I do note that the -8 version of the firmware loads, but modinfo suggests -7. > [iwlwifi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
firmware:       iwlwifi-7265-[COLOR="#FF0000"]7[/COLOR].ucode
<snip>> iwlwifi 0000:01:00.0: loaded firmware version 22.24.[COLOR="#FF0000"]8[/COLOR].0 op_mode iwlmvmThat was an interesting quirk in the iwlwifi driver that took us a while to discover! The version of iwlwifi in Ubuntu 14.10 uses the -9 firmware; a possible solution may be to install the backported driver suite from kernel version 3.16+, but let's see if we can fix what we have before we throw it out and try something newer.

---

### Post by foxy123 on 2015-01-21
> **chili555 said:**
> Still looks pretty normal until the last line. May we also see: ```
dmesg | grep 80211
```This is the first Intel 7265 device I've seen, so I am anxious to learn its peculiarities.

I do note that the -8 version of the firmware loads, but modinfo suggests -7. That was an interesting quirk in the iwlwifi driver that took us a while to discover! The version of iwlwifi in Ubuntu 14.10 uses the -9 firmware; a possible solution may be to install the backported driver suite from kernel version 3.16+, but let's see if we can fix what we have before we throw it out and try something newer.

here you are:

```
~$ dmesg | grep 80211
[    7.069610] cfg80211: Calling CRDA to update world regulatory domain
[    7.491606] cfg80211: World regulatory domain updated:
[    7.491610] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.491613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.491615] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.491617] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.491619] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.491621] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.562409] Modules linked in: snd_hwdep x86_pkg_temp_thermal snd_pcm snd_page_alloc snd_seq_midi intel_powerclamp snd_seq_midi_event i915(+) coretemp hid_sensor_iio_common kvm_intel dell_wmi sparse_keymap kvm snd_rawmidi snd_seq crct10dif_pclmul crc32_pclmul ghash_clmulni_intel drm_kms_helper videobuf2_core aesni_intel parport_pc aes_x86_64 mac80211 hid_sensor_hub lrw gf128mul hid_multitouch glue_helper drm dell_laptop ablk_helper dcdbas i2c_algo_bit iwlwifi ppdev snd_seq_device snd_timer serio_raw lp snd cryptd videodev mei_me joydev wmi parport mei soundcore mac_hid i2c_designware_platform btusb lpc_ich i2c_designware_core video cfg80211 bluetooth hid_generic usbhid hid psmouse ahci libahci
[    7.672068] cfg80211: Calling CRDA for country: GB
[    7.673923] cfg80211: Regulatory domain changed to country: GB
[    7.673923] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.673924] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    7.673925] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    7.673926] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    7.673926] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[    7.673927] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[    7.750747] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.703913] cfg80211: Calling CRDA for country: GB
[   12.705972] cfg80211: Regulatory domain changed to country: GB
[   12.705975] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.705976] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   12.705977] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   12.705978] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   12.705979] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   12.705980] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   81.022255] cfg80211: Calling CRDA to update world regulatory domain
[   81.028047] cfg80211: World regulatory domain updated:
[   81.028054] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   81.028059] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.028063] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.028066] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   81.028069] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.028072] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.028098] cfg80211: Calling CRDA for country: GB
[   81.033741] cfg80211: Regulatory domain changed to country: GB
[   81.033749] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   81.033753] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   81.033757] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   81.033760] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   81.033762] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   81.033766] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
```

---

### Post by chili555 on 2015-01-22
Once again, we see nothing remarkable that suggests a fault we can fix. I suggest we try the iwlwifi driver from kernel version 3.18. Please download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)

Right-click and select 'Extract Here.' Now, in the terminal:
```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.18.1-1
make defconfig-iwlwifi
make
sudo make install
```
We also need the firmware. In fact, the driver you just built suggests -9 but the official iwlwifi site suggests that for kernels 3.17 and above, -10 is used. Let's install both. Please get the 7265 files here: [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware) Downloads usually go to your Downloads folder. Right-click each and select 'Extract Here.' Now, in the terminal:```
cd ~/Downloads/iwlwifi-7265-ucode-23.11.10.0
sudo mv iwlwifi*  /lib/firmware
cd ~/Downloads/iwlwifi-7265-ucode-25.228.9.0
sudo mv iwlwifi-7265-9.ucode  /lib/firmware
sudo chmod 644 /lib/firmware/iwl*

```Reboot and let us hear your report. We will probably have one additional step.

---

### Post by foxy123 on 2015-01-22
> **chili555 said:**
> Once again, we see nothing remarkable that suggests a fault we can fix. I suggest we try the iwlwifi driver from kernel version 3.18. Please download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)

Right-click and select 'Extract Here.' Now, in the terminal:
```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.18.1-1
make defconfig-iwlwifi
make
sudo make install
```
We also need the firmware. In fact, the driver you just built suggests -9 but the official iwlwifi site suggests that for kernels 3.17 and above, -10 is used. Let's install both. Please get the 7265 files here: [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware) Downloads usually go to your Downloads folder. Right-click each and select 'Extract Here.' Now, in the terminal:```
cd ~/Downloads/iwlwifi-7265-ucode-23.11.10.0
sudo mv iwlwifi*  /lib/firmware
cd ~/Downloads/iwlwifi-7265-ucode-25.228.9.0
sudo mv iwlwifi-7265-9.ucode  /lib/firmware
sudo chmod 644 /lib/firmware/iwl*

```Reboot and let us hear your report. We will probably have one additional step.

Thanks a lot. I have followed all the steps. It works fine so far. Will report if there are still issues.

---

### Post by foxy123 on 2015-01-22
shall I check if all the changes took effect?

---

### Post by chili555 on 2015-01-22
> **foxy123 said:**
> shall I check if all the changes took effect?If it is working as expected, I doubt you need to; if you are curious, see what the version of the driver is:```
modinfo iwlwifi
```It should be something like:> version:        backported from Linux (v[COLOR="#FF0000"]3.18.1[/COLOR]-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4cAnd please tell us what firmware got loaded:```
dmesg | grep iwl
```Glad it's working!

---

### Post by foxy123 on 2015-01-23
So far so good...

```
:~$ modinfo iwlwifi
filename:       /lib/modules/3.13.0-44-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:d
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3165-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     3F79E6B9DBC4489492CABD9
alias:          pci:v00008086d000024F4sv*sd00000030bc*sc*i*
alias:          pci:v00008086d000024F3sv*sd00000004bc*sc*i*
alias:          pci:v00008086d000024F3sv*sd00000010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00009200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000900Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005102bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005412bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d00003165sv*sd00004210bc*sc*i*
alias:          pci:v00008086d00003165sv*sd00004010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00001170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00001070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008370bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000CC60bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000CC70bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004C70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004C60bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        compat,cfg80211
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

```
```
dmesg | grep iwl
[   10.814621] iwlwifi 0000:01:00.0: irq 59 for MSI/MSI-X
[   10.968451] Modules linked in: crc32_pclmul(+) ghash_clmulni_intel snd_seq aesni_intel aes_x86_64 lrw snd_seq_device gf128mul glue_helper ablk_helper cryptd snd_timer joydev btusb serio_raw i915(+) bluetooth snd mei_me lpc_ich drm_kms_helper iwlwifi(OX) drm mei cfg80211(OX) compat(OX) i2c_algo_bit soundcore wmi i2c_designware_platform video i2c_designware_core mac_hid parport_pc ppdev lp parport hid_generic usbhid hid ahci psmouse libahci
[   11.113422] iwlwifi 0000:01:00.0: loaded firmware version 23.11.10.0 op_mode iwlmvm
[   11.144209] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x184
[   11.145839] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[   11.146005] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[   11.240133] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.208651] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[   17.208809] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[ 1061.484505] iwlwifi 0000:01:00.0: fail to flush all tx fifo queues Q 0
[ 1061.484517] iwlwifi 0000:01:00.0: Current SW read_ptr 111 write_ptr 112
[ 1061.484544] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 80 00 00 00 00 00 00  ................
[ 1061.484561] iwlwifi 0000:01:00.0: FH TRBs(0) = 0x00000000
[ 1061.484576] iwlwifi 0000:01:00.0: FH TRBs(1) = 0x8010204e
[ 1061.484590] iwlwifi 0000:01:00.0: FH TRBs(2) = 0x00000000
[ 1061.484605] iwlwifi 0000:01:00.0: FH TRBs(3) = 0x8030006f
[ 1061.484619] iwlwifi 0000:01:00.0: FH TRBs(4) = 0x00000000
[ 1061.484633] iwlwifi 0000:01:00.0: FH TRBs(5) = 0x00000000
[ 1061.484647] iwlwifi 0000:01:00.0: FH TRBs(6) = 0x00000000
[ 1061.484662] iwlwifi 0000:01:00.0: FH TRBs(7) = 0x00709075
[ 1061.484717] iwlwifi 0000:01:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [111,112]
[ 1061.484771] iwlwifi 0000:01:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1061.484825] iwlwifi 0000:01:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [79,79]
[ 1061.484879] iwlwifi 0000:01:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.484932] iwlwifi 0000:01:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.484986] iwlwifi 0000:01:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485039] iwlwifi 0000:01:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485093] iwlwifi 0000:01:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485146] iwlwifi 0000:01:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485200] iwlwifi 0000:01:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [118,118]
[ 1061.485254] iwlwifi 0000:01:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485307] iwlwifi 0000:01:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485361] iwlwifi 0000:01:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485414] iwlwifi 0000:01:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485468] iwlwifi 0000:01:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485522] iwlwifi 0000:01:00.0: Q 15 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1061.485576] iwlwifi 0000:01:00.0: Q 16 is inactive and mapped to fifo 1 ra_tid 0x0000 [103,103]
[ 1061.485630] iwlwifi 0000:01:00.0: Q 17 is inactive and mapped to fifo 3 ra_tid 0x0006 [26,26]
[ 1061.485683] iwlwifi 0000:01:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1061.485736] iwlwifi 0000:01:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.260631] iwlwifi 0000:01:00.0: fail to flush all tx fifo queues Q 0
[ 1902.260648] iwlwifi 0000:01:00.0: Current SW read_ptr 186 write_ptr 187
[ 1902.260679] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 00 00 04 00 00 00 00  ................
[ 1902.260699] iwlwifi 0000:01:00.0: FH TRBs(0) = 0x00000000
[ 1902.260718] iwlwifi 0000:01:00.0: FH TRBs(1) = 0xc01100d0
[ 1902.260736] iwlwifi 0000:01:00.0: FH TRBs(2) = 0x00000000
[ 1902.260754] iwlwifi 0000:01:00.0: FH TRBs(3) = 0x803000ba
[ 1902.260772] iwlwifi 0000:01:00.0: FH TRBs(4) = 0x00000000
[ 1902.260790] iwlwifi 0000:01:00.0: FH TRBs(5) = 0x00000000
[ 1902.260808] iwlwifi 0000:01:00.0: FH TRBs(6) = 0x00000000
[ 1902.260826] iwlwifi 0000:01:00.0: FH TRBs(7) = 0x00709020
[ 1902.260887] iwlwifi 0000:01:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [186,187]
[ 1902.260946] iwlwifi 0000:01:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1902.261005] iwlwifi 0000:01:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [127,127]
[ 1902.261064] iwlwifi 0000:01:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261123] iwlwifi 0000:01:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261182] iwlwifi 0000:01:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261241] iwlwifi 0000:01:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261300] iwlwifi 0000:01:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261358] iwlwifi 0000:01:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261418] iwlwifi 0000:01:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [33,33]
[ 1902.261477] iwlwifi 0000:01:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261535] iwlwifi 0000:01:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261594] iwlwifi 0000:01:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261652] iwlwifi 0000:01:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261711] iwlwifi 0000:01:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.261769] iwlwifi 0000:01:00.0: Q 15 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1902.261828] iwlwifi 0000:01:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [209,209]
[ 1902.261891] iwlwifi 0000:01:00.0: Q 17 is inactive and mapped to fifo 3 ra_tid 0x0006 [49,49]
[ 1902.261950] iwlwifi 0000:01:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1902.262008] iwlwifi 0000:01:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

```

---

### Post by foxy123 on 2015-01-24
Well, still keeps disconnecting :(

---

### Post by chili555 on 2015-01-24
> **foxy123 said:**
> Well, still keeps disconnecting :(I suspected as much:> iwlwifi 0000:01:00.0: [COLOR="#FF0000"]fail to flush all tx fifo queues [/COLOR]Q 0We have tried many of the usual fixes; from here on, it's all trial and error. Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Add the following line at the end:```
options iwlwifi 11n_disable=8
```Proofread carefully, save and close the text editor. Reboot.

If this is ineffective, use the same process and change the last line to:```
options iwlwifi 11n_disable=1
```Reboot and let us hear your results.

---

### Post by foxy123 on 2015-01-24
> **chili555 said:**
> I suspected as much:We have tried many of the usual fixes; from here on, it's all trial and error. Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Add the following line at the end:```
options iwlwifi 11n_disable=8
```Proofread carefully, save and close the text editor. Reboot.

If this is ineffective, use the same process and change the last line to:```
options iwlwifi 11n_disable=1
```Reboot and let us hear your results.

Thanks a lot. It was actually ```
options iwlwifi 11n_disable=8
```, so I've changed it to ```
options iwlwifi 11n_disable=1
```. Lte's how it will work.

---

### Post by jeremy31 on 2015-01-24
Someone claimed they could fix the flush queues problem by deleting the MAC address from the Network Manager connection info like in the pic
[IMG]http://ubuntuforums.org/images/attach/png.gif[/IMG]

---

### Post by chili555 on 2015-01-24
Color me skeptical, but please try it and let us know.

---

### Post by jeremy31 on 2015-01-24
> **chili555 said:**
> Color me skeptical, but please try it and let us know.

I am skeptical also but can confirm it does no harm on my Intel 7260 or 6250 after deleting the address from Network Manager and rebooting but I would like it tried by someone with the errors

---

### Post by drBouvierLeduc on 2015-06-18
Just wanted to say, for reference, that adding the following line to **/etc/modprobe.d/iwlwifi.conf** worked for me :
> 
options iwlwifi 11n_disable=8

So thanks, chili555 !

---

