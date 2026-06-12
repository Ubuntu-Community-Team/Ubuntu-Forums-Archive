---
title: "Wi-Fi Hotspot disconnects after about 30 seconds"
date: 2023-07-07
forum: Networking &amp; Wireless
---

### Post by evanjames on 2023-07-07
Hello, I appreciate any help and insights.

I have a fresh Ubuntu 22.04 install. I have a Buffalo WI-U2-433DHP USB Wi-Fi adapter. The driver for the Wi-Fi adapter originally was not installed, but I followed the instructions [here]("https://mamimu-memo.com/techinfo/post-2420/"), and it seems to work, at least to connect to Wi-Fi networks. To be explicit, this device uses a Realtek 802.11ac (rtl8812au) chipset. The driver needed to be manually installed from a fork of the original Realtek driver, which is on [Github]("https://github.com/gnab/rtl8812au").

I would like to create a hotspot with the computer this is connected to (a desktop connected via a wired connection) so that I can connect my laptop to it. I do the following:

Settings --> Wi-Fi --> ... menu --> Turn on Wi-Fi Hotspot

Which successfully starts the Hotspot, and I can indeed even see it with my laptop. However, after about 30 seconds, the hotspot deactivates (Connection Failed). 

After a bunch of searching, I ran the following command to diagnose:

```
sudo systemctl status NetworkManager.service
```

And got the following output:

```
&#9679;     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-07-07 15:40:52 JST; 1h 40min ago
       Docs: man:NetworkManager(8)
   Main PID: 673 (NetworkManager)
      Tasks: 3 (limit: 76717)
     Memory: 12.1M
        CPU: 11.494s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;673 /usr/sbin/NetworkManager --no-daemon

Jul 07 17:21:01 DDDDD NetworkManager[673]: <info>  [1688718061.0170] Config: added 'wep_tx_keyidx' value '0'
Jul 07 17:21:01 DDDDD NetworkManager[673]: <info>  [1688718061.0301] device (enx18ece77e6b6b): supplicant interface state: disconnected -> associating
Jul 07 17:21:11 DDDDD NetworkManager[673]: <info>  [1688718071.0337] device (enx18ece77e6b6b): supplicant interface state: associating -> disconnected
Jul 07 17:21:11 DDDDD NetworkManager[673]: <info>  [1688718071.1339] device (enx18ece77e6b6b): supplicant interface state: disconnected -> scanning
Jul 07 17:21:21 DDDDD NetworkManager[673]: <info>  [1688718081.1377] device (enx18ece77e6b6b): supplicant interface state: scanning -> associating
Jul 07 17:21:26 DDDDD NetworkManager[673]: [COLOR=#daa520]<warn>  [1688718086.5310] device (enx18ece77e6b6b): Activation: (wifi) Ad-Hoc network creation took too long, failing activation[/COLOR]
Jul 07 17:21:26 DDDDD NetworkManager[673]: <info>  [1688718086.5311] device (enx18ece77e6b6b): state change: config -> failed (reason 'supplicant-timeout', sys-iface-state: 'managed')
Jul 07 17:21:26 DDDDD NetworkManager[673]: [COLOR=#daa520]<warn>  [1688718086.5316] device (enx18ece77e6b6b): Activation: failed for connection 'Hotspot'[/COLOR]
Jul 07 17:21:26 DDDDD NetworkManager[673]: <info>  [1688718086.5321] device (enx18ece77e6b6b): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul 07 17:21:26 DDDDD NetworkManager[673]: <info>  [1688718086.5398] device (enx18ece77e6b6b): supplicant interface state: associating -> disconnected


```

The output from dmesg is:

```
[ 6281.088914] RTL871X: set group key to hw: alg:1(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:0
[ 6281.088918] RTL871X: set bssid:00:00:00:00:00:00
[ 6281.088993] RTL871X: set ssid [DDDDD] fw_state=0x00000020
[ 6281.092174] UpdateHalRAMask8812A => mac_id:1, networkType:0x01, mask:0x00000000
                    ==> rssi_level:0, rate_bitmap:0x00000000
[ 6301.194086] RTL871X: set group key to hw: alg:1(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:0
[ 6301.194134] RTL871X: set bssid:00:00:00:00:00:00
[ 6301.194175] RTL871X: set ssid [DDDDD] fw_state=0x00000040
[ 6304.689842] rtl8812au 1-12:1.0 enx18ece77e6b6b: Current addr:  18 ec e7 7e 6b 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6304.689857] rtl8812au 1-12:1.0 enx18ece77e6b6b: Expected addr: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 6304.689863] ------------[ cut here ]------------
[ 6304.689866] netdevice: enx18ece77e6b6b: Incorrect netdev->dev_addr
[ 6304.689898] WARNING: CPU: 5 PID: 673 at net/core/dev_addr_lists.c:519 dev_addr_check.cold+0x65/0x9f
[ 6304.689916] Modules linked in: isofs nft_chain_nat xt_MASQUERADE nf_nat nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 nft_compat bridge stp llc rfcomm nf_tables libcrc32c nfnetlink uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common snd_usb_audio videodev snd_usbmidi_lib mc nvidia_uvm(PO) cmac algif_hash algif_skcipher cfg80211 af_alg intel_rapl_msr bnep intel_rapl_common nvidia_drm(PO) intel_uncore_frequency intel_uncore_frequency_common isst_if_common nvidia_modeset(PO) skx_edac nfit x86_pkg_temp_thermal intel_powerclamp coretemp nvidia(PO) kvm_intel snd_hda_codec_realtek kvm snd_hda_codec_generic ledtrig_audio crct10dif_pclmul ghash_clmulni_intel aesni_intel snd_hda_codec_hdmi crypto_simd cryptd rapl snd_hda_intel intel_cstate snd_intel_dspcfg snd_intel_sdw_acpi snd_seq_midi snd_hda_codec ucsi_ccg binfmt_misc snd_hda_core snd_seq_midi_event typec_ucsi typec snd_hwdep snd_rawmidi drm_kms_helper fb_sys_fops syscopyarea snd_pcm sysfillrect btusb sysimgblt btrtl
[ 6304.690123]  nls_iso8859_1 snd_seq btbcm btintel btmtk snd_seq_device snd_timer bluetooth joydev snd input_leds mei_me ecdh_generic ecc soundcore ioatdma mei dca mac_hid acpi_tad sch_fq_codel 8812au(OE) msr parport_pc ppdev lp parport drm ramoops pstore_blk reed_solomon pstore_zone efi_pstore ip_tables x_tables autofs4 hid_generic usbhid hid crc32_pclmul atlantic i2c_nvidia_gpu e1000e i2c_ccgx_ucsi i2c_i801 ahci macsec i2c_smbus xhci_pci libahci xhci_pci_renesas wmi
[ 6304.690226] CPU: 5 PID: 673 Comm: NetworkManager Tainted: P        W  OE     5.19.0-46-generic #47~22.04.1-Ubuntu
[ 6304.690235] Hardware name: Supermicro SYS-5039A-I/X11SRA, BIOS 2.3 10/19/2020
[ 6304.690239] RIP: 0010:dev_addr_check.cold+0x65/0x9f
[ 6304.690249] Code: 01 e8 3a 13 f5 ff 0f 0b 49 c7 c4 34 8e c6 89 80 3b 00 75 30 48 c7 c6 3f 8e c6 89 4c 89 e2 48 c7 c7 68 cc d0 89 e8 16 13 f5 ff <0f> 0b e9 8f da d1 ff 4c 8b 24 c5 60 5b 94 89 eb d4 49 c7 c4 34 8e
[ 6304.690254] RSP: 0018:ffffbe8202e5f718 EFLAGS: 00010246
[ 6304.690261] RAX: 0000000000000000 RBX: ffff9687d5f13000 RCX: 0000000000000000
[ 6304.690266] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
[ 6304.690270] RBP: ffffbe8202e5f728 R08: 0000000000000000 R09: 0000000000000000
[ 6304.690274] R10: 0000000000000000 R11: 0000000000000000 R12: ffffffff89c5a430
[ 6304.690278] R13: ffffffffc0717560 R14: 0000000000000001 R15: ffff9687d5f13000
[ 6304.690283] FS:  00007f0164d5a4c0(0000) GS:ffff969700140000(0000) knlGS:0000000000000000
[ 6304.690289] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 6304.690294] CR2: 00007f587388a0f8 CR3: 000000010866e004 CR4: 00000000003706e0
[ 6304.690299] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 6304.690304] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[ 6304.690309] Call Trace:
[ 6304.690312]  <TASK>
[ 6304.690320]  __dev_open+0x45/0x1d0
[ 6304.690333]  __dev_change_flags+0x1ad/0x230
[ 6304.690341]  ? rt6_dump_route+0xe2/0x2c0
[ 6304.690352]  dev_change_flags+0x26/0x70
[ 6304.690359]  do_setlink+0x293/0xce0
[ 6304.690373]  ? _raw_spin_unlock_bh+0x1d/0x30
[ 6304.690381]  ? fib6_dump_table.isra.0+0x1c6/0x1d0
[ 6304.690391]  ? __nla_validate_parse+0x4b/0x1c0
[ 6304.690403]  __rtnl_newlink+0x595/0x680
[ 6304.690412]  ? kmem_cache_alloc_trace+0x1a6/0x330
[ 6304.690425]  rtnl_newlink+0x49/0x80
[ 6304.690433]  rtnetlink_rcv_msg+0x179/0x440
[ 6304.690439]  ? sugov_update_single_freq+0x7f/0x3b0
[ 6304.690450]  ? rtnl_calcit.isra.0+0x150/0x150
[ 6304.690457]  netlink_rcv_skb+0x53/0x110
[ 6304.690469]  rtnetlink_rcv+0x15/0x30
[ 6304.690475]  netlink_unicast+0x241/0x360
[ 6304.690483]  netlink_sendmsg+0x25d/0x4f0
[ 6304.690491]  sock_sendmsg+0x6c/0x80
[ 6304.690500]  ____sys_sendmsg+0x264/0x2a0
[ 6304.690507]  ? import_iovec+0x1b/0x30
[ 6304.690515]  ? sendmsg_copy_msghdr+0x8d/0xb0
[ 6304.690527]  ___sys_sendmsg+0x81/0xd0
[ 6304.690536]  ? wireless_send_event+0x271/0x440
[ 6304.690553]  ? netdev_run_todo+0x5f/0x3e0
[ 6304.690560]  ? iw_handler_get_private+0x80/0x80
[ 6304.690570]  ? ioctl_standard_iw_point+0x3e0/0x3e0
[ 6304.690580]  ? __fget_light+0xb5/0x160
[ 6304.690592]  __sys_sendmsg+0x5c/0xb0
[ 6304.690603]  __x64_sys_sendmsg+0x1d/0x30
[ 6304.690611]  do_syscall_64+0x59/0x90
[ 6304.690619]  ? exit_to_user_mode_prepare+0x3b/0xd0
[ 6304.690628]  ? syscall_exit_to_user_mode+0x2a/0x50
[ 6304.690637]  ? do_syscall_64+0x69/0x90
[ 6304.690643]  ? do_syscall_64+0x69/0x90
[ 6304.690648]  ? do_syscall_64+0x69/0x90
[ 6304.690653]  ? do_syscall_64+0x69/0x90
[ 6304.690658]  ? do_syscall_64+0x69/0x90
[ 6304.690664]  entry_SYSCALL_64_after_hwframe+0x63/0xcd
[ 6304.690670] RIP: 0033:0x7f0165d27b4d
[ 6304.690677] Code: 28 89 54 24 1c 48 89 74 24 10 89 7c 24 08 e8 3a 8f f6 ff 8b 54 24 1c 48 8b 74 24 10 41 89 c0 8b 7c 24 08 b8 2e 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 33 44 89 c7 48 89 44 24 08 e8 7e 8f f6 ff 48
[ 6304.690682] RSP: 002b:00007fff0b5d2100 EFLAGS: 00000293 ORIG_RAX: 000000000000002e
[ 6304.690690] RAX: ffffffffffffffda RBX: 00000000000000f9 RCX: 00007f0165d27b4d
[ 6304.690696] RDX: 0000000000000000 RSI: 00007fff0b5d2140 RDI: 000000000000000c
[ 6304.690700] RBP: 0000558a8f222030 R08: 0000000000000000 R09: 0000000000000000
[ 6304.690704] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000000000
[ 6304.690709] R13: 00007fff0b5d2290 R14: 00007fff0b5d228c R15: 0000000000000000
[ 6304.690719]  </TASK>
[ 6304.690722] ---[ end trace 0000000000000000 ]---

```

Any idea what might be the cause of the failure? I also got this message on Ubuntu 20.04 (I upgraded to 22.04 in the hopes of fixing this problem).

Many thanks.

---

