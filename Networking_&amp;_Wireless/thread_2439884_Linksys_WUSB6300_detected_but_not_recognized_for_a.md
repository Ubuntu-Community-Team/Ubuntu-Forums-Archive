---
title: "Linksys WUSB6300 detected but not recognized for as wireless device"
date: 2020-04-02
forum: Networking &amp; Wireless
---

### Post by thisishowtanksaremade on 2020-04-02
Hi there,

I tried to install the package for the RTL8812AU device as apt install RTL8812AU-dkms. It hasn't worked, and I can't select the devise for wireless.

 This same device was working under Windows 7.

I ran the wireless troubleshooting script and nothing jumps out at me as the culprit. Here are the results.

[ATTACH]285369[/ATTACH]

---

### Post by chili555 on 2020-04-02
Please run and post:

```
modinfo 8812au | grep 003F
```Thanks.

---

### Post by thisishowtanksaremade on 2020-04-02
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*

---

### Post by chili555 on 2020-04-02
> **thisishowtanksaremade said:**
> alias:          usb:v[COLOR="#FF0000"]13B1[/COLOR]p[COLOR="#FF0000"]003F[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
That's your device:> 
ID [COLOR="#FF0000"]13b1:003f [/COLOR]Linksys WUSB6300 802.11a/b/g/n/ac Wireless Adapter [Realtek RTL8812AU]

We wonder then, why the driver loads and doesn't create an interface and trigger Network Manager and get to work.

Let's look for clues in the log:

```
sudo modprobe 8812au && dmesg | grep -i rtl
```

---

### Post by thisishowtanksaremade on 2020-04-02
Nothing looks unusual here

```

sudo modprobe 8812au && dmesg | grep -i rtl
[    1.432496] r8169 0000:05:00.0 eth0: RTL8168evl/8111evl, 70:85:c2:d4:82:d8, XID 2c9, IRQ 32
[    2.608744] RTL871X: module init start
[    2.608746] RTL871X: rtl8812au v4.3.8_12175.20140902
[    2.608747] RTL871X: build time: Apr  2 2020 13:53:34
[    2.769290] usbcore: registered new interface driver rtl8812au
[    2.769292] RTL871X: module init ret=0
[    3.535665] RTL8211E Gigabit Ethernet r8169-500:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)

```

---

### Post by thisishowtanksaremade on 2020-04-02
I ran dmesg after plugging in the device and was greeted by a wonderful stack trace.

```

[  445.586272] ------------[ cut here ]------------
[  445.586425] WARNING: CPU: 4 PID: 2441 at /build/linux-hwe-UUUsac/linux-hwe-5.3.0/net/wireless/core.c:868 wiphy_register+0x855/0xba0 [cfg80211]
[  445.586426] Modules linked in: amdgpu amd_iommu_v2 gpu_sched edac_mce_amd kvm_amd ccp snd_hda_codec_realtek kvm snd_hda_codec_generic irqbypass ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_nhlt uvcvideo radeon snd_hda_codec snd_usb_audio videobuf2_vmalloc videobuf2_memops snd_hda_core snd_usbmidi_lib videobuf2_v4l2 crct10dif_pclmul snd_hwdep videobuf2_common snd_pcm crc32_pclmul videodev snd_seq_midi ghash_clmulni_intel joydev mc 8812au(OE) snd_seq_midi_event ttm snd_rawmidi drm_kms_helper aesni_intel drm snd_seq cfg80211 aes_x86_64 i2c_algo_bit crypto_simd fb_sys_fops cryptd snd_seq_device syscopyarea k10temp fam15h_power input_leds snd_timer glue_helper sysfillrect sysimgblt snd soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid pata_acpi r8169 ahci realtek pata_atiixp i2c_piix4 libahci
[  445.586480] CPU: 4 PID: 2441 Comm: kworker/4:0 Tainted: G        W  OE     5.3.0-45-generic #37~18.04.1-Ubuntu
[  445.586481] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./970M Pro3, BIOS P1.60 06/17/2016
[  445.586487] Workqueue: usb_hub_wq hub_event
[  445.586524] RIP: 0010:wiphy_register+0x855/0xba0 [cfg80211]
[  445.586527] Code: 52 48 c1 e2 04 48 01 c2 48 83 38 00 74 28 48 39 c2 74 72 48 83 c0 30 48 83 78 10 00 75 ea 48 c7 c7 b8 22 54 c0 e8 fe b8 02 d3 <0f> 0b b8 ea ff ff ff e9 e9 f8 ff ff 48 83 78 08 00 75 d1 48 c7 c7
[  445.586529] RSP: 0018:ffffb6d343ee7720 EFLAGS: 00010282
[  445.586532] RAX: 0000000000000024 RBX: ffff9dfaf7474300 RCX: 0000000000000006
[  445.586534] RDX: 0000000000000000 RSI: 0000000000000082 RDI: ffff9dfb77b17440
[  445.586535] RBP: ffffb6d343ee77b0 R08: 0000000000000498 R09: 0000000000000004
[  445.586537] R10: ffffb6d343ee77c8 R11: 0000000000000001 R12: 000000000000034e
[  445.586539] R13: ffff9dfb735d5000 R14: ffff9dfb6f16e030 R15: ffff9dfb6f16e030
[  445.586541] FS:  0000000000000000(0000) GS:ffff9dfb77b00000(0000) knlGS:0000000000000000
[  445.586543] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  445.586545] CR2: 00007f33ccdea028 CR3: 0000000234468000 CR4: 00000000000406e0
[  445.586547] Call Trace:
[  445.586610]  ? _rtw_malloc+0x2d/0x2f [8812au]
[  445.586659]  ? _rtw_memcpy+0x10/0x12 [8812au]
[  445.586712]  rtw_wdev_alloc+0xf9/0x29f [8812au]
[  445.586766]  ? rtw_wdev_alloc+0xf9/0x29f [8812au]
[  445.586817]  rtw_usb_if1_init+0xf0/0x209 [8812au]
[  445.586868]  rtw_drv_init+0x244/0x2f7 [8812au]
[  445.586874]  usb_probe_interface+0x149/0x300
[  445.586878]  really_probe+0xf5/0x3e0
[  445.586881]  driver_probe_device+0x11b/0x130
[  445.586884]  __device_attach_driver+0x7b/0xe0
[  445.586887]  ? driver_allows_async_probing+0x60/0x60
[  445.586891]  bus_for_each_drv+0x6b/0xb0
[  445.586894]  __device_attach+0xd8/0x160
[  445.586897]  device_initial_probe+0x13/0x20
[  445.586901]  bus_probe_device+0x92/0xa0
[  445.586904]  device_add+0x402/0x690
[  445.586909]  ? _cond_resched+0x19/0x40
[  445.586913]  usb_set_configuration+0x3fd/0x8f0
[  445.586917]  ? kernfs_activate+0x78/0x80
[  445.586921]  generic_probe+0x2e/0x80
[  445.586925]  usb_probe_device+0x31/0x70
[  445.586928]  really_probe+0xf5/0x3e0
[  445.586930]  driver_probe_device+0x11b/0x130
[  445.586933]  __device_attach_driver+0x7b/0xe0
[  445.586936]  ? driver_allows_async_probing+0x60/0x60
[  445.586940]  bus_for_each_drv+0x6b/0xb0
[  445.586942]  __device_attach+0xd8/0x160
[  445.586945]  device_initial_probe+0x13/0x20
[  445.586949]  bus_probe_device+0x92/0xa0
[  445.586952]  device_add+0x402/0x690
[  445.586956]  ? add_device_randomness+0x9d/0x1c0
[  445.586958]  usb_new_device+0x218/0x4a0
[  445.586962]  hub_port_connect+0x661/0x990
[  445.586965]  port_event+0x67a/0x7e0
[  445.586968]  ? __switch_to_asm+0x40/0x70
[  445.586971]  hub_event+0x21e/0x3b0
[  445.586977]  process_one_work+0x1fd/0x3f0
[  445.586980]  worker_thread+0x34/0x410
[  445.586984]  kthread+0x121/0x140
[  445.586987]  ? process_one_work+0x3f0/0x3f0
[  445.586990]  ? kthread_park+0xb0/0xb0
[  445.586993]  ret_from_fork+0x22/0x40
[  445.586996] ---[ end trace ee72ca70dac4560f ]---

```

That led me to this [https://forums.kali.org/showthread.php?45819-Module-88XXau-core-dump-crash-on-load-in-2019-03-w-all-updates-applied](https://forums.kali.org/showthread.php?45819-Module-88XXau-core-dump-crash-on-load-in-2019-03-w-all-updates-applied)

I followed the instructions on that page and it worked. Thanks for the hint to look in dmesg!

---

