---
title: "wifi lost after upgrade to version 6.2.0-26-generic #26~22.04.1"
date: 2023-08-24
forum: Networking &amp; Wireless
---

### Post by gerardrossen on 2023-08-24
Hi all,
I still have this serious problem, after upgrade UBUNTU already mentioned in #203140.3, but no reaction until now.

I have a dual boot HP PROBOOK 450 with this version of UBUNTU:
"Linux gerard-HP-ProBook-450-G5 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux", (which I use for 99,9%) and Windows11.

The PCI is :   Intel Corporation Wireless 8265 / 8275 (rev 78), 

When I boot in Windows11 there is no problem at all and I can use the 5G network.

However in UBUNTU the PCI is visable with "lspci", but I cannot use this.

In stead I, have to use a very old  USB-stick :"Realtek Semiconductor Corp. RTL8188ETV Wireless LAN 802.11n Network Adapter", but my access is limited to the old 2.4G network.

I searched whole internet, but could not find a solution.

I am very desperate now,

Can some body help me activating the internal PCI network ?

Please help !!

---

### Post by gerardrossen on 2023-09-05
Here some new info:
After upgrade to 6.2.0-31 nothing changed, still cannot enter my  
network controller: Intel Corporation Wireless 8265 / 8275 (rev 78) 
Is not accessible  !!

After the update to version  6.2.0-32 its still the same problem : Ubuntu cannot access this, but windows can !

There must be something not OK , I tried everything i could find on forums, without success.

Am I the only one with this problem ??

Is there someone here to help me ???

---

### Post by Rubi1200 on 2023-09-05
The only thing I can suggest is to run the wireless info script, which will gather the info needed to help troubleshoot the issue:
[https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)

Hopefully, someone can then come along and offer solutions.

---

### Post by gerardrossen on 2023-09-06
> **Rubi1200 said:**
> The only thing I can suggest is to run the wireless info script, which will gather the info needed to help troubleshoot the issue:
[https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)

Hopefully, someone can then come along and offer solutions.


Thanks Rubi1200,

I will add data.

---

### Post by gerardrossen on 2023-09-06
here it is...

---

### Post by gerardrossen on 2023-09-07
additional info for USB sticks:

Sitecom Europe B.V. 802.11n WLAN Adapter : NOT WORKING, But available when plugged in.

TP-Link Archer T1U 802.11a/n/ac Wireless Adapter [mediaTek MT610U] : SAME PROBLEM

 TP-Link TL-WN823N V2/V2 [realtek rtl8192EU] : SAME PROBLEM

Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter : SAME PROBLEM

 WORKING:
Realtek Semiconductor Corp. RTL8188ETV Wireless LAN 802.11n Network Adapter

With the last one plugged in, I can work with the 2.4 G network here (5G NOT).

Hope this will help a bit.

---

### Post by chili555 on 2023-09-07
Please unplug the USB wireless, open a terminal and do:

```
sudo modprobe iwlwifi
sudo dmesg | grep iwl
```

Plug the USB wireless back in and post the results.

**********************
Note to Chili: filename: /lib/modules/6.2.0-32-generic/ubuntu/iwlwifi/iwlwifi-compat.ko ???

---

### Post by Frogs Hair on 2023-09-07
Moved to ***Networking & Wireless***.

---

### Post by gerardrossen on 2023-09-08
[B]Thanks for your reply's , I really appreciate this.

sudo modprobe iwlwifi: modprobe: ERROR: could not insert 'iwlwifi'
[/B]
**sudo dmesg | grep iwl:**

[    8.278722] iwlwifi_compat: loading out-of-tree module taints kernel.
[    8.309073] Loading modules backported from iwlwifi
[    8.309095] iwlwifi-stack-public:master:9904:0e80336f
[    8.418084] Modules linked in: processor_thermal_mbox libarc4 ecc snd(+) i2c_algo_bit cfg80211(O+) processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch(+) mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal(+) int340x_thermal_zone hp_accel(+) int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci i2c_i801 r8169 ahci i2c_hid intel_lpss xhci_pci crc32_pclmul psmouse rtsx_pci i2c_smbus realtek libahci idma64 xhci_pci_renesas hid video wmi pinctrl_sunrisepoint
[   10.713874]  cec videobuf2_common btmtk intel_cstate sparse_keymap serio_raw snd_seq_device platform_profile joydev processor_thermal_device_pci_legacy rc_core wmi_bmof mc bluetooth input_leds processor_thermal_device snd_timer r8188eu(C) ee1004 drm_kms_helper processor_thermal_rfim ecdh_generic processor_thermal_mbox libarc4 ecc snd i2c_algo_bit processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal int340x_thermal_zone hp_accel int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci i2c_i801 r8169 ahci i2c_hid intel_lpss xhci_pci crc32_pclmul psmouse rtsx_pci i2c_smbus realtek libahci idma64 xhci_pci_renesas hid
[   11.363644]  snd_seq_midi_event btrtl crypto_simd videobuf2_v4l2 btbcm snd_rawmidi cryptd drm_display_helper videodev btintel hp_wmi rapl snd_seq cec videobuf2_common btmtk intel_cstate sparse_keymap serio_raw snd_seq_device platform_profile joydev processor_thermal_device_pci_legacy rc_core wmi_bmof mc bluetooth input_leds processor_thermal_device snd_timer r8188eu(C) ee1004 drm_kms_helper processor_thermal_rfim ecdh_generic processor_thermal_mbox libarc4 ecc snd i2c_algo_bit processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal int340x_thermal_zone hp_accel int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci
[   17.591226]  snd_seq_midi_event btrtl crypto_simd videobuf2_v4l2 btbcm snd_rawmidi cryptd drm_display_helper videodev btintel hp_wmi rapl snd_seq cec videobuf2_common btmtk intel_cstate sparse_keymap serio_raw snd_seq_device platform_profile joydev processor_thermal_device_pci_legacy rc_core wmi_bmof mc bluetooth input_leds processor_thermal_device snd_timer r8188eu(C) ee1004 drm_kms_helper processor_thermal_rfim ecdh_generic processor_thermal_mbox libarc4 ecc snd i2c_algo_bit processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal int340x_thermal_zone hp_accel int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci
[ 1346.642755]  snd_seq_midi_event btrtl crypto_simd videobuf2_v4l2 btbcm snd_rawmidi cryptd drm_display_helper videodev btintel hp_wmi rapl snd_seq cec videobuf2_common btmtk intel_cstate sparse_keymap serio_raw snd_seq_device platform_profile joydev processor_thermal_device_pci_legacy rc_core wmi_bmof mc bluetooth input_leds processor_thermal_device snd_timer r8188eu(C) ee1004 drm_kms_helper processor_thermal_rfim ecdh_generic processor_thermal_mbox libarc4 ecc snd i2c_algo_bit processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal int340x_thermal_zone hp_accel int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci
[ 1402.397349]  snd_seq_midi_event btrtl crypto_simd videobuf2_v4l2 btbcm snd_rawmidi cryptd drm_display_helper videodev btintel hp_wmi rapl snd_seq cec videobuf2_common btmtk intel_cstate sparse_keymap serio_raw snd_seq_device platform_profile joydev processor_thermal_device_pci_legacy rc_core wmi_bmof mc bluetooth input_leds processor_thermal_device snd_timer r8188eu(C) ee1004 drm_kms_helper processor_thermal_rfim ecdh_generic processor_thermal_mbox libarc4 ecc snd i2c_algo_bit processor_thermal_rapl syscopyarea soundcore intel_rapl_common sysfillrect mei_me iwlwifi_compat(O) sysimgblt hid_multitouch mei intel_soc_dts_iosf intel_xhci_usb_role_switch intel_pch_thermal int3403_thermal int340x_thermal_zone hp_accel int3400_thermal mac_hid lis3lv02d acpi_thermal_rel wireless_hotkey acpi_pad sch_fq_codel msr parport_pc ppdev lp ramoops pstore_blk parport drm pstore_zone reed_solomon efi_pstore ip_tables x_tables autofs4 usbhid mmc_block hid_generic i2c_hid_acpi rtsx_pci_sdmmc intel_lpss_pci

---

### Post by chili555 on 2023-09-08
Does this help? [https://askubuntu.com/questions/1466027/wi-fi-not-working-on-ubuntu-23-04-acer-swift-14](https://askubuntu.com/questions/1466027/wi-fi-not-working-on-ubuntu-23-04-acer-swift-14)

---

### Post by gerardrossen on 2023-09-08
Hello ,
I do not trust these errors,
and therefore i did not remove anything yet.


[ATTACH=CONFIG]292703[/ATTACH]

---

### Post by chili555 on 2023-09-08
iwlwifi-compat came from somewhere. What does this tell us?

```
dpkg-query -l '*iwlwifi*'
dpkg-query -l '*compat*'
history | grep compat

```The default driver is simply iwlwifi.

---

### Post by jeremy31 on 2023-09-08
linux-modules-iwlwifi would be my guess

---

### Post by gerardrossen on 2023-09-15
Hi All,

Just a question, do I have to do some tests, or is t still in analysis phase ?

Please keep me informed if possible.

---

### Post by chili555 on 2023-09-15
We are waiting for the response to my questions at post #12 above.

---

### Post by gerardrossen on 2023-09-15
Sorry, it was not obvious a question for me.

here they are:

---

### Post by chili555 on 2023-09-15
Please try:

```
sudo apt purge linux-modules-iwlwifi*
sudo apt install --reinstall linux-modules-extra-$(uname -r)

```
Reboot and show us:

```
sudo dmesg | grep iwl
```

---

### Post by gerardrossen on 2023-09-15
Jippy, its working again with the local WiFi !!!!!

Thanks a lot !!

---

### Post by chili555 on 2023-09-15
Jippy, indeed! I'm glad it's working. Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

