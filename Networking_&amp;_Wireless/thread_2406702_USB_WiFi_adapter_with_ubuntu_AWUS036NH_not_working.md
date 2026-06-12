---
title: "USB WiFi adapter with ubuntu AWUS036NH not working"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by wnocton on 2018-11-24
Hello, I've tried to read the previous threads on this and haven't had any luck. When I run lsusb it shows my new wireless card at Bus 002, Device 008

When I try to run the other commands it says I already have a newer driver etc. Apologize for my lacking of Linux skills

apt-get install build-essential linux-headers-`uname -r`
result is

  build-essential is already the newest version (12.4ubuntu1).linux-headers-4.15.0-39-generic is already the newest version (4.15.0-39.42).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Thanks!
Wayne

---

### Post by chili555 on 2018-11-24
> 
When I run lsusb it shows my new wireless card at Bus 002, Device 008
May we see the exact result?> 
 I've tried to read the previous threads on this and haven't had any luck. 
Which are you following? May we have the link?

---

### Post by wnocton on 2018-11-24
lsusb
Bus 002 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 008: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:301a Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Followed many of the threads but already closed the pages. They all seem to have the same end, I can't download their suggested drivers when mine are already newer, and can't try the cd or the make since I can't download older drivers. Most were several years old which made that even more likely.

---

### Post by chili555 on 2018-11-24
> 
148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Your device uses the built-in driver rt2800usb. To fix whatever problem you are having, it will do no good to try to install an older, less well-developed driver.

Please tell us about your problem. Include the result of this terminal command:```
dmesg | grep -e rt2 -e wlx
```

---

### Post by wnocton on 2018-11-24
Here are the results, the card doesn't appear to work at all, doesn't show up when I run ifconfig, please excuse my lack of Ununtu skiils in this area, and thank you for your quick replies.

dmesg | grep -e rt2 -e wlx
```
[   44.359008]  (null): rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   44.387206]  (null): rt2x00_set_rf: Info - RF chipset 0005 detected
[   44.387489] Modules linked in: crct10dif_pclmul rt2800usb(+) rt2x00usb rt2800lib rt2x00lib joydev input_leds mac80211(OE) snd_hda_codec_realtek snd_hda_codec_generic cfg80211(OE) crc32_pclmul compat(OE) snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core pcbc snd_hwdep snd_pcm aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 crypto_simd snd_rawmidi glue_helper snd_seq cryptd snd_seq_device snd_timer snd gpio_ich soundcore intel_cstate mei_me lpc_ich shpchp mei mac_hid hp_wmi sparse_keymap serio_raw tpm_infineon intel_rapl_perf wmi_bmof ipmi_si ipmi_devintf ipmi_msghandler sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 video i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops e1000e psmouse drm ahci libahci i2c_i801
[   44.387571]  rt2x00lib_probe_hw+0x39c/0x420 [rt2x00lib]
[   44.387573]  rt2x00lib_probe_dev+0x2e3/0x370 [rt2x00lib]
[   44.387574]  rt2x00usb_probe+0x1c2/0xc70 [rt2x00usb]
[   44.387578]  rt2800usb_probe+0x15/0x20 [rt2800usb]
[   44.387595]  rt2800usb_driver_init+0x23/0x1000 [rt2800usb]
[   44.387640]  (null): rt2x00lib_probe_dev: Error - Failed to initialize hw
[   44.387660] rt2800usb: probe of 2-1.8:1.0 failed with error -22
[   44.387678] usbcore: registered new interface driver rt2800usb
[  222.743175]  (null): rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  222.771856]  (null): rt2x00_set_rf: Info - RF chipset 0005 detected
[  222.772175] Modules linked in: nls_utf8 udf crc_itu_t pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass snd_hda_codec_hdmi crct10dif_pclmul rt2800usb rt2x00usb rt2800lib rt2x00lib joydev input_leds mac80211(OE) snd_hda_codec_realtek snd_hda_codec_generic cfg80211(OE) crc32_pclmul compat(OE) snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core pcbc snd_hwdep snd_pcm aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 crypto_simd snd_rawmidi glue_helper snd_seq cryptd snd_seq_device snd_timer snd gpio_ich soundcore intel_cstate mei_me lpc_ich shpchp mei mac_hid hp_wmi sparse_keymap serio_raw tpm_infineon intel_rapl_perf wmi_bmof ipmi_si ipmi_devintf ipmi_msghandler sch_fq_codel parport_pc
[  222.772350]  rt2x00lib_probe_hw+0x39c/0x420 [rt2x00lib]
[  222.772354]  rt2x00lib_probe_dev+0x2e3/0x370 [rt2x00lib]
[  222.772358]  rt2x00usb_probe+0x1c2/0xc70 [rt2x00usb]
[  222.772362]  rt2800usb_probe+0x15/0x20 [rt2800usb]
[  222.772520]  (null): rt2x00lib_probe_dev: Error - Failed to initialize hw
[  222.772542] rt2800usb: probe of 2-1.7:1.0 failed with error -22
[  233.750461]  (null): rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  233.779023]  (null): rt2x00_set_rf: Info - RF chipset 0005 detected
[  233.779323] Modules linked in: nls_utf8 udf crc_itu_t pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass snd_hda_codec_hdmi crct10dif_pclmul rt2800usb rt2x00usb rt2800lib rt2x00lib joydev input_leds mac80211(OE) snd_hda_codec_realtek snd_hda_codec_generic cfg80211(OE) crc32_pclmul compat(OE) snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core pcbc snd_hwdep snd_pcm aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 crypto_simd snd_rawmidi glue_helper snd_seq cryptd snd_seq_device snd_timer snd gpio_ich soundcore intel_cstate mei_me lpc_ich shpchp mei mac_hid hp_wmi sparse_keymap serio_raw tpm_infineon intel_rapl_perf wmi_bmof ipmi_si ipmi_devintf ipmi_msghandler sch_fq_codel parport_pc
[  233.779498]  rt2x00lib_probe_hw+0x39c/0x420 [rt2x00lib]
[  233.779503]  rt2x00lib_probe_dev+0x2e3/0x370 [rt2x00lib]
[  233.779507]  rt2x00usb_probe+0x1c2/0xc70 [rt2x00usb]
[  233.779510]  rt2800usb_probe+0x15/0x20 [rt2800usb]
[  233.779690]  (null): rt2x00lib_probe_dev: Error - Failed to initialize hw
[  233.779716] rt2800usb: probe of 2-1.8:1.0 failed with error -22
[  242.454122]  (null): rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  242.482331]  (null): rt2x00_set_rf: Info - RF chipset 0005 detected
[  242.482634] Modules linked in: nls_utf8 udf crc_itu_t pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass snd_hda_codec_hdmi crct10dif_pclmul rt2800usb rt2x00usb rt2800lib rt2x00lib joydev input_leds mac80211(OE) snd_hda_codec_realtek snd_hda_codec_generic cfg80211(OE) crc32_pclmul compat(OE) snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core pcbc snd_hwdep snd_pcm aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 crypto_simd snd_rawmidi glue_helper snd_seq cryptd snd_seq_device snd_timer snd gpio_ich soundcore intel_cstate mei_me lpc_ich shpchp mei mac_hid hp_wmi sparse_keymap serio_raw tpm_infineon intel_rapl_perf wmi_bmof ipmi_si ipmi_devintf ipmi_msghandler sch_fq_codel parport_pc
[  242.482811]  rt2x00lib_probe_hw+0x39c/0x420 [rt2x00lib]
[  242.482815]  rt2x00lib_probe_dev+0x2e3/0x370 [rt2x00lib]
[  242.482819]  rt2x00usb_probe+0x1c2/0xc70 [rt2x00usb]
[  242.482822]  rt2800usb_probe+0x15/0x20 [rt2800usb]
[  242.482983]  (null): rt2x00lib_probe_dev: Error - Failed to initialize hw
[  242.483005] rt2800usb: probe of 2-1.5:1.0 failed with error -22
[35147.019974]  (null): rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[35147.048655]  (null): rt2x00_set_rf: Info - RF chipset 0005 detected
[35147.048959] Modules linked in: nls_utf8 udf crc_itu_t pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass snd_hda_codec_hdmi crct10dif_pclmul rt2800usb rt2x00usb rt2800lib rt2x00lib joydev input_leds mac80211(OE) snd_hda_codec_realtek snd_hda_codec_generic cfg80211(OE) crc32_pclmul compat(OE) snd_hda_intel snd_hda_codec ghash_clmulni_intel snd_hda_core pcbc snd_hwdep snd_pcm aesni_intel snd_seq_midi snd_seq_midi_event aes_x86_64 crypto_simd snd_rawmidi glue_helper snd_seq cryptd snd_seq_device snd_timer snd gpio_ich soundcore intel_cstate mei_me lpc_ich shpchp mei mac_hid hp_wmi sparse_keymap serio_raw tpm_infineon intel_rapl_perf wmi_bmof ipmi_si ipmi_devintf ipmi_msghandler sch_fq_codel parport_pc
[35147.049140]  rt2x00lib_probe_hw+0x39c/0x420 [rt2x00lib]
[35147.049144]  rt2x00lib_probe_dev+0x2e3/0x370 [rt2x00lib]
[35147.049148]  rt2x00usb_probe+0x1c2/0xc70 [rt2x00usb]
[35147.049152]  rt2800usb_probe+0x15/0x20 [rt2800usb]
[35147.049326]  (null): rt2x00lib_probe_dev: Error - Failed to initialize hw
[35147.049354] rt2800usb: probe of 2-1.5:1.0 failed with error -22
```

---

### Post by jeremy31 on 2018-11-24
Post results for ```
modinfo cfg80211
```

---

### Post by wnocton on 2018-11-24
Resuslts from

```
modinfo cfg80211
filename:       /lib/modules/4.15.0-39-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:master:7299:2c6dbf84
alias:          net-pf-16-proto-16-family-nl80211
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E44E0187B00EA3749FD374F
depends:        compat
retpoline:      Y
name:           cfg80211
vermagic:       4.15.0-39-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
```

---

### Post by jeremy31 on 2018-11-24
Try ```
cd backport-iwlwifi
sudo make uninstall
```
Reboot

---

### Post by wnocton on 2018-11-24
make uninstall
  uninstall /lib/modules/4.15.0-39-generic/updates/net/wireless/cfg80211.ko
  uninstall /lib/modules/4.15.0-39-generic/updates/net/mac80211/mac80211.ko
  uninstall /lib/modules/4.15.0-39-generic/updates/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
  uninstall /lib/modules/4.15.0-39-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
  uninstall /lib/modules/4.15.0-39-generic/updates/drivers/net/wireless/intel/iwlwifi/xvt/iwlxvt.ko
  uninstall /lib/modules/4.15.0-39-generic/updates/compat/compat.ko
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.


Your backported driver modules should be uninstalled now.
Reboot.

Will reboot and check back, thank you.

---

### Post by wnocton on 2018-11-24
It works! Thanks a bunch, I still don't understand why it works but it works.

---

