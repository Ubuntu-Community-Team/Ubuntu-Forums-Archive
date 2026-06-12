---
title: "No Wifi Adapter Found in Ubuntu 18.04?"
date: 2020-10-21
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-10-21
Hello, I am running ubuntu 18.04, kernel 5.4.0-42-generic. Last week,  the internet randomly stopped working. Turns out the network manager  somehow disappeared, so I downloaded the debians on another computer,  transferred via USB, and then installed. Now my ethernet works, but my  wifi is still not working. When I go to settings and click on wifi, it  lists "no wifi adapter found". I figure this must be a software issue,  because the wifi was working two weeks ago. I have tried updating the  computer, both from command line and software center, but this has not  solved the problem.

```
sudo lshw -C network
``` produces:
```
*-network UNCLAIMED       
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:6c:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:dc500000-dc501fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: enx106530d24185
       serial: 10:65:30:d2:41:85
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152  driverversion=v1.10.11 duplex=full ip=192.168.1.113 link=yes  multicast=yes port=MII speed=1Gbit/s
```

Based on that output, I found this driver here: [https://linux-hardware.org/index.php?id=pci:8086-24fd-8086-9010](https://linux-hardware.org/index.php?id=pci:8086-24fd-8086-9010)  that I think is the right one for my wifi adapter. Unfortunately, I'm  not sure how to install it. I downloaded the file, and went into  software and updates-->additional drivers. Here, I can see listed:

```
Intel Corporation: Wireless 8265/8275
This device is not working.
(option 1) Using iwlwifi driver backport in DKMS format from backport-iwlwifi-dkms (open source)
(option 2) Continue using a manually installed driver
(option 3) Do not use the device
```

Option 3 is selected, and the other two are greyed out. The "revert" and  "apply changes" buttons at the bottom are also greyed out.

```
sudo modprobe iwlwifi
```
produces:
```
modprobe: ERROR: could not insert 'iwlwifi': Operation not permitted
```

 I tried running in su prompt as well, with the same result.

```
uname -r
```
produces: ```
5.4.0-42-generic
```
```
modinfo iwlwifi | grep filename
```
produces: ```
filename:       /lib/modules/5.4.0-42-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
```

Finally, I tried booting from the previous kernel, but encountered the same problem there as well--"no wifi adapter found".dr

Any suggestions? Help would be greatly appreciated!

---

### Post by morrownr on 2020-10-22
Some laptops have a switch that will turn wifi off. Have you checked that?

---

### Post by chili555 on 2020-10-22
Please try:

```
sudo apt purge backport-iwlwifi-dkms
```

Reboot and show us:

```
sudo modprobe iwlwifi
dmesg | grep iwl
```

---

### Post by mysteriousmonkey29 on 2020-10-22
```
sudo apt purge backport-iwlwifi-dkms
```

produces:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'backport-iwlwifi-dkms' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libllvm9 libpkcs11-helper1 linux-hwe-5.4-headers-5.4.0-42 linux-hwe-5.4-headers-5.4.0-45
  linux-hwe-5.4-headers-5.4.0-47 linux-hwe-5.4-headers-5.4.0-48 openvpn
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.
```

After reboot,
```
sudo modprobe iwlwifi
```
still returns:
```
modprobe: ERROR: could not insert 'iwlwifi': Operation not permitted
```
(even when I try it within su)

Finally,
```
dmesg | grep iwl
```
returns nothing

---

### Post by chili555 on 2020-10-22
Will you please try again with Secure Boot disabled in the BIOS/EFI and try again?

---

### Post by mysteriousmonkey29 on 2020-10-22
Ah, awesome! Got a response now:

```
sudo modprobe iwlwifi
```
then
```
dmesg | grep iwl
```
produces:
```
[    3.312635] Loading modules backported from iwlwifi
[    3.312636] iwlwifi-stack-public:master:8613:3ae69204
[    3.382165] iwlwifi 0000:6c:00.0: enabling device (0000 -> 0002)
[    3.399383] iwlwifi 0000:6c:00.0: loaded firmware version 36.9f0a2d68.0 8265-36.ucode op_mode iwlmvm
[    3.589837] iwlwifi 0000:6c:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[    3.596193] iwlwifi 0000:6c:00.0: reporting RF_KILL (radio disabled)
[    3.660939] iwlwifi 0000:6c:00.0: base HW address: 7c:2a:31:11:03:46
[    3.674861] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.918748] iwlwifi 0000:6c:00.0 wlp108s0: renamed from wlan0
[    4.121710] iwlwifi 0000:6c:00.0: RF_KILL bit toggled to enable radio.
[    4.121711] iwlwifi 0000:6c:00.0: reporting RF_KILL (radio enabled)
[    6.646626] iwlwifi 0000:6c:00.0: RF_KILL bit toggled to disable radio.
[    6.646627] iwlwifi 0000:6c:00.0: reporting RF_KILL (radio disabled)
[    6.925963] WARNING: CPU: 7 PID: 128 at /var/lib/dkms/backport-iwlwifi/git/build/drivers/net/wireless/intel/iwlwifi/pcie/trans.c:2111 iwl_trans_pcie_grab_nic_access+0x14a/0x1e0 [iwlwifi]
[    6.925964] Modules linked in: aufs overlay ftdi_sio usbserial wacom binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_generic mei_hdcp cdc_ether usbnet r8152 mii dell_rbtn intel_rapl_msr dell_laptop ledtrig_audio dell_smm_hwmon snd_hda_intel snd_intel_dspcfg x86_pkg_temp_thermal snd_hda_codec intel_powerclamp snd_hda_core coretemp snd_hwdep snd_pcm kvm_intel snd_seq_midi snd_seq_midi_event kvm crct10dif_pclmul iwlmvm(OE) crc32_pclmul joydev snd_rawmidi ghash_clmulni_intel mac80211(OE) aesni_intel snd_seq libarc4 crypto_simd cryptd glue_helper dell_wmi dell_smbios snd_seq_device snd_timer dcdbas rapl intel_cstate snd iwlwifi(OE) input_leds serio_raw rtsx_pci_ms soundcore wmi_bmof intel_wmi_thunderbolt dell_wmi_descriptor cfg80211(OE) memstick hid_multitouch hid_sensor_gyro_3d hid_sensor_accel_3d hid_sensor_magn_3d hid_sensor_als compat(OE) hid_sensor_rotation hid_sensor_incl_3d hid_sensor_trigger industrialio_triggered_buffer
[    6.926024] RIP: 0010:iwl_trans_pcie_grab_nic_access+0x14a/0x1e0 [iwlwifi]
[    6.926038]  iwl_write_prph+0x3d/0x90 [iwlwifi]
[    6.926044]  iwl_fw_dbg_stop_restart_recording+0x150/0x240 [iwlwifi]
[    6.926054]  ? iwl_mvm_rm_sta_common+0x54/0xb0 [iwlmvm]
[    6.926059]  iwl_fw_dbg_stop_sync+0x3a/0x40 [iwlwifi]
[    6.926064]  ? iwl_fw_dbg_stop_sync+0x3a/0x40 [iwlwifi]
[    6.926069]  __iwl_mvm_mac_stop+0x83/0x160 [iwlmvm]
[    6.926073]  iwl_mvm_mac_stop+0x6e/0x90 [iwlmvm]
[    6.926166] iwlwifi 0000:6c:00.0: iwlwifi transaction failed, dumping registers
[    6.926168] iwlwifi 0000:6c:00.0: iwlwifi device config registers:
[    6.926634] iwlwifi 0000:6c:00.0: 00000000: 24fd8086 00100406 02800078 00000000 dc500004 00000000 00000000 00000000
[    6.926636] iwlwifi 0000:6c:00.0: 00000020: 00000000 00000000 00000000 01508086 00000000 000000c8 00000000 000001ff
[    6.926637] iwlwifi 0000:6c:00.0: 00000040: 00020010 10008ec0 00190c10 0045e811 10110142 00000000 00000000 00000000
[    6.926639] iwlwifi 0000:6c:00.0: 00000060: 00000000 00080812 00000405 00000000 00010001 00000000 00000000 00000000
[    6.926640] iwlwifi 0000:6c:00.0: 00000080: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.926641] iwlwifi 0000:6c:00.0: 000000a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.926642] iwlwifi 0000:6c:00.0: 000000c0: 00000000 00000000 c823d001 0d000000 00814005 fee00478 00000000 00000000
[    6.926643] iwlwifi 0000:6c:00.0: 000000e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.926644] iwlwifi 0000:6c:00.0: 00000100: 14010001 00000000 00000000 00462031 00000000 00002000 00000000 00000000
[    6.926645] iwlwifi 0000:6c:00.0: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.926647] iwlwifi 0000:6c:00.0: 00000140: 14c10003 ff110346 7c2a31ff 15410018 10031003 0001001e 00481e1f 40a0000f
[    6.926648] iwlwifi 0000:6c:00.0: iwlwifi device memory mapped registers:
[    6.926963] iwlwifi 0000:6c:00.0: 00000000: 00080000 00000000 00000000 00000000 00000000 00000000 00000010 00000000
[    6.926964] iwlwifi 0000:6c:00.0: 00000020: 00000011 00000008 00000230 d55555d5 d55555d5 d55555d5 80008040 001f0042
[    6.927016] iwlwifi 0000:6c:00.0: iwlwifi device AER capability structure:
[    6.927039] iwlwifi 0000:6c:00.0: 00000000: 14010001 00000000 00000000 00462031 00000000 00002000 00000000 00000000
[    6.927040] iwlwifi 0000:6c:00.0: 00000020: 00000000 00000000 00000000
[    6.927041] iwlwifi 0000:6c:00.0: iwlwifi parent port (0000:00:1c.7) config registers:
[    6.927145] iwlwifi 0000:00:1c.7: 00000000: 9d178086 00100407 060400f1 00810000 00000000 00000000 006c6c00 200000f0
[    6.927147] iwlwifi 0000:00:1c.7: 00000020: dc50dc50 0001fff1 00000000 00000000 00000000 00000040 00000000 001204ff
[    6.927148] iwlwifi 0000:00:1c.7: 00000040: 01428010 00008001 00100000 08724813 70110042 005cb200 01480000 00000000
[    6.927150] iwlwifi 0000:00:1c.7: 00000060: 00000000 00000837 00000400 0000000e 00010003 00000000 00000000 00000000
[    6.927151] iwlwifi 0000:00:1c.7: 00000080: 00019005 fee00298 00000000 00000000 0000a00d 081d1028 00000000 00000000
[    6.927152] iwlwifi 0000:00:1c.7: 000000a0: c8030001 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927154] iwlwifi 0000:00:1c.7: 000000c0: 00000000 00000000 00000000 00000000 07001001 00001842 899e0008 00000000
[    6.927155] iwlwifi 0000:00:1c.7: 000000e0: 00630300 00000000 00100016 00000000 00000150 4c000000 08410fb3 04000004
[    6.927157] iwlwifi 0000:00:1c.7: 00000100: 14010001 00000000 00010000 00060011 00000000 00002000 00000000 00000000
[    6.927158] iwlwifi 0000:00:1c.7: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927160] iwlwifi 0000:00:1c.7: 00000140: 2001000d 0000000f 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927161] iwlwifi 0000:00:1c.7: 00000160: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927162] iwlwifi 0000:00:1c.7: 00000180: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927164] iwlwifi 0000:00:1c.7: 000001a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927165] iwlwifi 0000:00:1c.7: 000001c0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927166] iwlwifi 0000:00:1c.7: 000001e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    6.927167] iwlwifi 0000:00:1c.7: 00000200: 2201001e 00b0281f 40a0280f
[    6.927171] iwlwifi 0000:6c:00.0: iwlwifi root port (0000:00:1c.7) AER cap structure:
[    6.927180] iwlwifi 0000:00:1c.7: 00000000: 14010001 00000000 00010000 00060011 00000000 00002000 00000000 00000000
[    6.927181] iwlwifi 0000:00:1c.7: 00000020: 00000000 00000000 00000000 00000000 00000000 00000000
[    7.219542] WARNING: CPU: 7 PID: 128 at /var/lib/dkms/backport-iwlwifi/git/build/drivers/net/wireless/intel/iwlwifi/mvm/mac80211.c:1331 __iwl_mvm_mac_stop+0x15b/0x160 [iwlmvm]
[    7.219542] Modules linked in: aufs overlay ftdi_sio usbserial wacom binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_generic mei_hdcp cdc_ether usbnet r8152 mii dell_rbtn intel_rapl_msr dell_laptop ledtrig_audio dell_smm_hwmon snd_hda_intel snd_intel_dspcfg x86_pkg_temp_thermal snd_hda_codec intel_powerclamp snd_hda_core coretemp snd_hwdep snd_pcm kvm_intel snd_seq_midi snd_seq_midi_event kvm crct10dif_pclmul iwlmvm(OE) crc32_pclmul joydev snd_rawmidi ghash_clmulni_intel mac80211(OE) aesni_intel snd_seq libarc4 crypto_simd cryptd glue_helper dell_wmi dell_smbios snd_seq_device snd_timer dcdbas rapl intel_cstate snd iwlwifi(OE) input_leds serio_raw rtsx_pci_ms soundcore wmi_bmof intel_wmi_thunderbolt dell_wmi_descriptor cfg80211(OE) memstick hid_multitouch hid_sensor_gyro_3d hid_sensor_accel_3d hid_sensor_magn_3d hid_sensor_als compat(OE) hid_sensor_rotation hid_sensor_incl_3d hid_sensor_trigger industrialio_triggered_buffer
[    7.219631] RIP: 0010:__iwl_mvm_mac_stop+0x15b/0x160 [iwlmvm]
[    7.219648]  iwl_mvm_mac_stop+0x6e/0x90 [iwlmvm]
```

---

### Post by mysteriousmonkey29 on 2020-10-22
I'm sorry, morrownr, I didn't see your response at first. There is an airplane mode switch on my laptop. It was off, but I tried turning it on, and then off, and that appears to have fixed the problem! My wifi is working now!

Thank you both for your help!

---

