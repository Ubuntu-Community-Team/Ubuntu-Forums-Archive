---
title: "lubuntu 19.04 Bluetooth troubleshooting guide"
date: 2020-04-25
forum: Networking &amp; Wireless
---

### Post by sumebody on 2020-04-25
Hello guys,

Is there a troubleshooting guide based on cmdline for bluetooth issues? I have no clue where to start for my Latitude 7370. How do I know if the drivers are even loaded? Thanks.

---

### Post by jeremy31 on 2020-04-25
You should update to a supported Ubuntu version, 19.04 went end of support in january.  Post results for ```
lsusb; lspci -nnk | grep -iA3 net; dmesg | egrep -i 'blue|firm'
```

---

### Post by sumebody on 2020-04-25
1. Thanks for replying

2. Lubuntu is still at 19.04 and I dont see an beta-update yet.

3. lsusb
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:5768 Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 001 Device 003: ID 0a5c:5832 Broadcom Corp. 5880
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

4. lspci -nnk | grep -iA3 net
```

6c:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
        Subsystem: Intel Corporation Wireless 8260 [8086:0150]
        Kernel driver in use: iwlwifi
        Kernel modules: iwlwifi

```

5. dmesg | egrep -i 'blue|firm'
```

[    0.215893] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.372972] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.694342] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_27.bin (v1.27)
[    5.052681] iwlwifi 0000:6c:00.0: loaded firmware version 36.77d01142.0 op_mode iwlmvm
[    5.141717] iwlwifi 0000:6c:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    5.410880] Bluetooth: Core ver 2.22
[    5.410899] Bluetooth: HCI device and connection manager initialized
[    5.410902] Bluetooth: HCI socket layer initialized
[    5.410904] Bluetooth: L2CAP socket layer initialized
[    5.410907] Bluetooth: SCO socket layer initialized
[    6.759768] Bluetooth: hci0: Firmware revision 0.0 build 176 week 45 2017
[    6.820160] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.820162] Bluetooth: BNEP filters: protocol multicast
[    6.820166] Bluetooth: BNEP socket layer initialized
[    6.839181] Bluetooth: RFCOMM TTY layer initialized
[    6.839186] Bluetooth: RFCOMM socket layer initialized
[    6.839190] Bluetooth: RFCOMM ver 1.11
[   10.270737] iwlwifi 0000:6c:00.0: Loaded firmware version: 36.77d01142.0
[   10.898679] Modules linked in: cmac rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common videodev btusb btrtl btbcm btintel mc snd_soc_skl snd_soc_hdac_hda snd_hda_ext_core snd_soc_skl_ipc snd_soc_sst_ipc snd_soc_sst_dsp snd_hda_codec_hdmi snd_soc_acpi_intel_match snd_soc_acpi mei_hdcp snd_soc_core intel_rapl_msr snd_hda_codec_realtek snd_hda_codec_generic snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm bluetooth ecdh_generic ecc snd_seq_midi snd_seq_midi_event iwlmvm snd_rawmidi mac80211 libarc4 x86_pkg_temp_thermal iwlwifi intel_powerclamp dell_laptop ledtrig_audio coretemp dell_smm_hwmon kvm_intel snd_seq kvm dell_wmi irqbypass intel_cstate intel_rapl_perf joydev dell_smbios dcdbas input_leds snd_seq_device snd_timer rtsx_pci_ms wmi_bmof sparse_keymap serio_raw dell_wmi_descriptor intel_wmi_thunderbolt cfg80211 snd memstick soundcore mei_me processor_thermal_device intel_xhci_usb_role_switch
[   14.463445] iwlwifi 0000:6c:00.0: Loaded firmware version: 36.77d01142.0
[   14.992418] Modules linked in: cmac rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common videodev btusb btrtl btbcm btintel mc snd_soc_skl snd_soc_hdac_hda snd_hda_ext_core snd_soc_skl_ipc snd_soc_sst_ipc snd_soc_sst_dsp snd_hda_codec_hdmi snd_soc_acpi_intel_match snd_soc_acpi mei_hdcp snd_soc_core intel_rapl_msr snd_hda_codec_realtek snd_hda_codec_generic snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm bluetooth ecdh_generic ecc snd_seq_midi snd_seq_midi_event iwlmvm snd_rawmidi mac80211 libarc4 x86_pkg_temp_thermal iwlwifi intel_powerclamp dell_laptop ledtrig_audio coretemp dell_smm_hwmon kvm_intel snd_seq kvm dell_wmi irqbypass intel_cstate intel_rapl_perf joydev dell_smbios dcdbas input_leds snd_seq_device snd_timer rtsx_pci_ms wmi_bmof sparse_keymap serio_raw dell_wmi_descriptor intel_wmi_thunderbolt cfg80211 snd memstick soundcore mei_me processor_thermal_device intel_xhci_usb_role_switch
[   27.803464] iwlwifi 0000:6c:00.0: Loaded firmware version: 36.77d01142.0
[   32.590499] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[   32.595504] Bluetooth: hci0: Device revision is 5
[   32.595506] Bluetooth: hci0: Secure boot is enabled
[   32.595507] Bluetooth: hci0: OTP lock is enabled
[   32.595508] Bluetooth: hci0: API lock is enabled
[   32.595508] Bluetooth: hci0: Debug lock is disabled
[   32.595510] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   32.597587] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   33.326852] Bluetooth: hci0: Failed to send firmware data (-38)
[   37.207292] iwlwifi 0000:6c:00.0: Loaded firmware version: 36.77d01142.0
[   37.209660] Modules linked in: ccm cmac rfcomm bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common videodev btusb btrtl btbcm btintel mc snd_soc_skl snd_soc_hdac_hda snd_hda_ext_core snd_soc_skl_ipc snd_soc_sst_ipc snd_soc_sst_dsp snd_hda_codec_hdmi snd_soc_acpi_intel_match snd_soc_acpi mei_hdcp snd_soc_core intel_rapl_msr snd_hda_codec_realtek snd_hda_codec_generic snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm bluetooth ecdh_generic ecc snd_seq_midi snd_seq_midi_event iwlmvm snd_rawmidi mac80211 libarc4 x86_pkg_temp_thermal iwlwifi intel_powerclamp dell_laptop ledtrig_audio coretemp dell_smm_hwmon kvm_intel snd_seq kvm dell_wmi irqbypass intel_cstate intel_rapl_perf joydev dell_smbios dcdbas input_leds snd_seq_device snd_timer rtsx_pci_ms wmi_bmof sparse_keymap serio_raw dell_wmi_descriptor intel_wmi_thunderbolt cfg80211 snd memstick soundcore mei_me processor_thermal_device intel_xhci_usb_role_switch
[   54.433069] iwlwifi 0000:6c:00.0: Loaded firmware version: 36.77d01142.0
[   91.090506] audit: type=1107 audit(1587824826.378:35): pid=630 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2198 label="snap.p3x-onenote.p3x-onenote" peer_pid=914 peer_label="unconfined"
[   96.633156] audit: type=1107 audit(1587824831.922:43): pid=630 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2645 label="snap.p3x-onenote.p3x-onenote" peer_pid=914 peer_label="unconfined"

```

---

### Post by jeremy31 on 2020-04-25
Looks like 20.04 is out [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by sumebody on 2020-04-25
Its interesting that there is a separate page for lubuntu.
And I have given it a try on the upgrade page:
```
zzzz@zubuntu:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.

```

I have checked that the setting "Show new distribution releases" is set to "Normal Releases."

What can I do now?

---

### Post by mörgæs on 2020-04-25
Upgrading is risky.
Upgrading from an unsupported version is highly risky.

A clean install of Lubuntu 20.04 will take less than half an hour.

---

### Post by sumebody on 2020-04-25
I'll give the upgrade a try. Now, how can I force it to detect this new release?

---

### Post by sumebody on 2020-04-25
Fixed. I tried 20.04 and it works now, sadly now I have to spend a couple of unproductive hours setting this whole monster up again. Why isnt the LTS support for Lubuntu 5 years as well?

---

### Post by DuckHook on 2020-04-25
> **sumebody said:**
> &#8230;Lubuntu is still at 19.04 and I dont see an beta-update yet&#8230;
You probably visited the wrong Lubuntu site. If you visited Lubuntu.net, this is the wrong site. The proper Lubuntu site is Lubuntu.me.

There was some very unfortunate falling out between members of the Lubuntu team a while back. As a result, the Lubuntu site was forked. Just as unfortunately, Lubuntu.net ceased to be maintained after 19.04, so 19.10 and 20.04 does not even appear. If you use the proper Lubuntu.me site, the flavour is maintained and kept up to date.

It's a shame that the Lubuntu.net site continues to be up and running despite being obsolete. It misleads and confuses many people. You are in good company.
> **sumebody said:**
> &#8230;Why isnt the LTS support for Lubuntu 5 years as well?
As corollary to above, maintenance is always a challenge. The Lubuntu devs/maintainers have their hands full and are practically always short staffed (most 'buntu flavours are community projects) so they can only manage three years, not five. They are always looking for help. If you care to give them a hand, they would be grateful.

---

### Post by guiverc on 2020-04-25
> **sumebody said:**
> Why isnt the LTS support for Lubuntu 5 years as well?

All flavors have 3 years of support, which is normal (*exception exist, eg. Ubuntu Kylin for the 16.04 cycle did you 5 years, and Ubuntu Studio in 18.04 was a normal release (not LTS though extended support is available via PPA bring it to 3 years), but 3 years is the norm*).


> [COLOR=#333333]Maintenance updates will be provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud and Ubuntu Core. All the remaining flavours will be supported for 3 years. [/COLOR]

[http://fridge.ubuntu.com/2020/04/23/ubuntu-20-04-lts-focal-fossa-released/](http://fridge.ubuntu.com/2020/04/23/ubuntu-20-04-lts-focal-fossa-released/)

It's best to read the release notes for whatever you use :)

---

