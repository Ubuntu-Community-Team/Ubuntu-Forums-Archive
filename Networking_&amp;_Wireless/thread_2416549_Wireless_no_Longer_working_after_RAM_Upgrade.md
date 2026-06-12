---
title: "Wireless no Longer working after RAM Upgrade"
date: 2019-04-11
forum: Networking &amp; Wireless
---

### Post by takeawaydave on 2019-04-11
Dell Precision 7510 with Ubuntu 18.04

I upgraded from 32 to 64 GB RAM and the wireless card is no longer working.

The following can be seen but I am not sure how to fix:

```
david@precision:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network UNCLAIMED       
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:dd300000-dd301fff

```

Anyone able to help?

---

### Post by takeawaydave on 2019-04-12
Any one ?

---

### Post by takeawaydave on 2019-04-12
Tried the following post :

[URL="https://askubuntu.com/questions/994944/fresh-ubuntu-install-no-wifi-networks-discoverable"]https://askubuntu.com/questions/994944/fresh-ubuntu-install-no-wifi-networks-discoverable
[/URL]
However the wireless adapter still is UNCLAIMED following the reboot.
Actually all of the other steps in this post completed as described in the post however just no change following reboot.

---

### Post by takeawaydave on 2019-04-12
Some further output based on the referenced post:

```
david@precision:~$ lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Wireless 8260 [8086:0050]
	Kernel modules: iwlwifi
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader [10ec:525a] (rev 01)
```

```
david@precision:~$ sudo modprobe iwlwifi && dmesg | grep iwl
[   10.480177] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   10.481021] iwlwifi 0000:02:00.0: hwdev DMA mask = 0x0000000fffffffff, dev_addr = 0x0000000064a9b000
[   10.481022] iwlwifi 0000:02:00.0: swiotlb: coherent allocation failed, size=4096
[   10.481047]  iwl_pcie_alloc_ict+0x96/0x120 [iwlwifi]
[   10.481055]  iwl_trans_pcie_alloc+0x7f7/0xcb0 [iwlwifi]
[   10.481062]  iwl_pci_probe+0x1d/0x1d0 [iwlwifi]
[   10.481104]  iwl_pci_register_driver+0x24/0x40 [iwlwifi]
[   10.481112]  iwl_drv_init+0x89/0x8b [iwlwifi]
[   10.481250] iwlwifi: probe of 0000:02:00.0 failed with error -12
[   10.783243] Modules linked in: intel_rapl nvidia_uvm(POE) x86_pkg_temp_thermal intel_powerclamp coretemp dell_wmi wmi_bmof sparse_keymap mxm_wmi intel_wmi_thunderbolt kvm_intel kvm irqbypass intel_cstate dell_laptop(+) dell_smm_hwmon dell_smbios dcdbas dell_wmi_descriptor iwlwifi snd_hda_codec_realtek(+) snd_hda_codec_generic intel_rapl_perf snd_hda_intel snd_usb_audio snd_hda_codec joydev input_leds snd_hda_core snd_usbmidi_lib serio_raw snd_hwdep snd_pcm snd_seq_midi cfg80211 rtsx_pci_ms snd_seq_midi_event memstick uvcvideo snd_rawmidi videobuf2_vmalloc snd_seq videobuf2_memops snd_seq_device videobuf2_v4l2 snd_timer btusb btrtl btbcm videobuf2_common btintel snd bluetooth videodev processor_thermal_device mei_me soundcore media ecdh_generic intel_soc_dts_iosf mei shpchp intel_pch_thermal ie31200_edac
```


```
david@precision:~$ ls /lib/firmware | grep 8000
iwlwifi-8000C-13.ucode
iwlwifi-8000C-16.ucode
iwlwifi-8000C-21.ucode
iwlwifi-8000C-22.ucode
iwlwifi-8000C-27.ucode
iwlwifi-8000C-31.ucode
iwlwifi-8000C-34.ucode
iwlwifi-8000C-36.ucode
```

---

### Post by takeawaydave on 2019-04-12
The error:

```
[   10.481022] iwlwifi 0000:02:00.0: swiotlb: coherent allocation failed, size=4096

```

Seems to a match on:

[https://bugs.archlinux.org/task/58288](https://bugs.archlinux.org/task/58288)

I recently upgraded the kernel to:

```
david@precision:~$ uname -r
4.16.0-041600-generic
```

---

