---
title: "Issues with ndiswrapper"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by adfbbbtx on 2018-07-26
There's just way too many issues with ubuntu.

I'm following [https://ubuntuforums.org/showthread.php?t=1964173&page=2](https://ubuntuforums.org/showthread.php?t=1964173&page=2)
from years ago to get my wifi wnda3100 working but I've hit a brickwall.

Then I look at this forum and it's very dead. LOL 1 view average for these post.


EDIT: Btw here's my 
dmesg | grep ndis

[    3.759934] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[    4.045317] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[    4.045491] Modules linked in: ndiswrapper(OE+) nls_iso8859_1 snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_realtek kvm_intel snd_hda_codec_generic kvm snd_hda_intel irqbypass snd_hda_codec crct10dif_pclmul crc32_pclmul eeepc_wmi snd_hda_core asus_wmi wmi_bmof sparse_keymap snd_hwdep intel_wmi_thunderbolt ghash_clmulni_intel snd_pcm pcbc mxm_wmi snd_seq_midi snd_seq_midi_event aesni_intel snd_rawmidi aes_x86_64 crypto_simd glue_helper snd_seq joydev cryptd intel_cstate input_leds intel_rapl_perf serio_raw snd_seq_device snd_timer snd nvidia_uvm(POE) soundcore mei_me mei mac_hid shpchp wmi acpi_pad sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea
[    4.045551]  wrap_submit_irp+0x334/0xaf0 [ndiswrapper]
[    4.045560]  pdoDispatchDeviceControl+0x2d/0x70 [ndiswrapper]
[    4.045566]  win2lin_pdoDispatchDeviceControl_2+0x18/0x20 [ndiswrapper]
[    4.045571]  ? win2lin_IoInvalidDeviceRequest_2+0x20/0x20 [ndiswrapper]
[    4.045576]  lin2win2+0xd/0x20 [ndiswrapper]
[    4.045583]  ? KeReleaseSpinLock+0x4f/0x70 [ndiswrapper]
[    4.045591]  IofCallDriver+0x6b/0xc0 [ndiswrapper]
[    4.045596]  win2lin_IofCallDriver_2+0x18/0x20 [ndiswrapper]
[    4.045603]  ? ExAllocatePoolWithTag+0x37/0x60 [ndiswrapper]
[    4.045607]  ? ExAllocatePoolWithTag+0x37/0x60 [ndiswrapper]
[    4.045610]  ? ExAllocatePoolWithTag+0x37/0x60 [ndiswrapper]
[    4.045615]  ? NdisAllocateMemoryWithTag+0x16/0x30 [ndiswrapper]
[    4.045622]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[    4.045627]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[    4.045632]  ? ExAllocatePoolWithTag+0x37/0x60 [ndiswrapper]
[    4.045635]  ? ExAllocatePoolWithTag+0x37/0x60 [ndiswrapper]
[    4.045639]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[    4.045645]  ? pdoDispatchPnp+0x4c/0x4e0 [ndiswrapper]
[    4.045650]  ? lin2win6+0x22/0x28 [ndiswrapper]
[    4.045657]  ? mp_init+0x7a/0x250 [ndiswrapper]
[    4.045661]  ? NdisDispatchPnp+0xd9/0xc00 [ndiswrapper]
[    4.045669]  ? IoAllocateIrp+0x48/0x70 [ndiswrapper]
[    4.045673]  ? IoInitializeIrp+0x1e/0x50 [ndiswrapper]
[    4.045678]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
[    4.045682]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
[    4.045686]  ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
[    4.045690]  ? lin2win2+0xd/0x20 [ndiswrapper]
[    4.045695]  ? IofCallDriver+0x6b/0xc0 [ndiswrapper]
[    4.045700]  ? IoSendIrpTopDev+0xd6/0x130 [ndiswrapper]
[    4.045704]  ? wrap_pnp_start_device+0x204/0x2e0 [ndiswrapper]
[    4.045708]  ? wrap_pnp_start_usb_device+0xcc/0x100 [ndiswrapper]
[    4.045726]  ? loader_init+0xba/0x140 [ndiswrapper]
[    4.045731]  ? wrapper_init+0xa6/0x1000 [ndiswrapper]
[    4.045777] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[    4.045778] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[    4.045780] ndiswrapper (mp_halt:254): device 00000000a6723941 is not initialized - not halting
[    4.045780] ndiswrapper: device eth%d removed
[    4.045800] ndiswrapper: probe of 1-5:1.0 failed with error -22
[    4.045829] usbcore: registered new interface driver ndiswrapper
[  493.882397] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  493.882935] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  493.882940] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  493.882946] ndiswrapper (mp_halt:254): device 000000000470ecb7 is not initialized - not halting
[  493.882949] ndiswrapper: device eth%d removed
[  493.883044] ndiswrapper: probe of 1-5:1.0 failed with error -22

---

### Post by QIII on 2018-07-26
The view counter is broken.  Canonical has been made aware of the issue.  You cannot take it to indicate how many views any post has gotten.

Please keep your language family friendly.

The instructions you are following are extremely old and are probably no longer useful.

---

### Post by chili555 on 2018-07-27
I have three points. First, I haven't seen ndiswrapper work successfully in many years. As far as I know, development on it stopped a few years ago. The Linux kernel marches forward and ndiswrapper and the required Windows XP driver files stand still. The gap is now just too large.

Second, I have a WNA3100v1 (similar, but not the same, I know) that can only be driven with ndiswrapper. With my years of experience, I can't get it to work. It was sent to me by my esteemed colleague Jeremy31, I assume as a form of torture but probably because he, with his years of experience, couldn't get it to work either. There are only about three or four devices that can't be supported in Linux and needed ndiswrapper back when it actually sort of worked. You have one and I have one.

Finally, if you believe that 'There's just way too many issues with ubuntu' then your course is clear. See if it works in Arch or Debian or CentOS or Windows.

---

