---
title: "System CPU locksup"
date: 2021-02-19
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2021-02-19
I get a message like this: "kernel: NMI watchdog: Watchdog detected hard LOCKUP on cpu 1". This is about the third time or so that this has happened now.  I have a Dell XPS 9550.  I am running Lubuntu.  


I hope this helps:
```
Feb 19 10:56:43 <hostname> kernel: iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: time out after 2000ms.
Feb 19 10:56:43 <hostname> kernel: iwlwifi 0000:02:00.0: Current CMD queue read_ptr 116 write_ptr 117
Feb 19 10:56:43 <hostname> kernel: iwlwifi 0000:02:00.0: HW error, resetting before reading
Feb 19 10:56:43 <hostname> kernel: iwlwifi 0000:02:00.0: Microcode SW error detected. Restarting 0xA5A50002.
Feb 19 10:56:43 <hostname> kernel: BUG: kernel NULL pointer dereference, address: 0000000000000008
Feb 19 10:56:43 <hostname> kernel: #PF: supervisor read access in kernel mode
Feb 19 10:56:43 <hostname> kernel: #PF: error_code(0x0000) - not-present page
Feb 19 10:56:43 <hostname> kernel: PGD 0 P4D 0  
Feb 19 10:56:43 <hostname> kernel: Oops: 0000 [#1] SMP PTI
Feb 19 10:56:43 <hostname> kernel: CPU: 1 PID: 967 Comm: irq/152-iwlwifi Tainted: G        W  OE     5.4.0-65-generic #73-Ubuntu
Feb 19 10:56:43 <hostname> kernel: Hardware name: Dell Inc. XPS 15 9550/0N7TVV, BIOS 1.12.0 10/03/2019
Feb 19 10:56:43 <hostname> kernel: RIP: 0010:iwl_pcie_irq_msix_handler+0x1ec/0x4a0 [iwlwifi]
Feb 19 10:56:43 <hostname> kernel: Code: 34 ff ff ff 49 8b 44 24 30 a8 02 0f 84 27 ff ff ff 49 8b 36 4c 89 e7 e8 42 d3 ff ff e9 17 ff ff >
Feb 19 10:56:43 <hostname> kernel: RSP: 0018:ffffa3b100dcfe38 EFLAGS: 00010202
Feb 19 10:56:43 <hostname> kernel: RAX: 0000000000000000 RBX: 0000000024000182 RCX: ffff8b93c06b1e00
Feb 19 10:56:43 <hostname> kernel: RDX: 0000000000000001 RSI: 0000000000000246 RDI: ffff8b93d951b0b0
Feb 19 10:56:43 <hostname> kernel: RBP: ffffa3b100dcfe70 R08: 0000000000000000 R09: ffffa3b100dcfd98
Feb 19 10:56:43 <hostname> kernel: R10: ffffffff863971a8 R11: ffffa3b100dcfb00 R12: ffff8b93c06b0018
Feb 19 10:56:43 <hostname> kernel: R13: 00000000a5a50002 R14: ffff8b93c06b0318 R15: ffff8b93c06b1eb0
Feb 19 10:56:43 <hostname> kernel: FS:  0000000000000000(0000) GS:ffff8b93dde40000(0000) knlGS:0000000000000000
Feb 19 10:56:43 <hostname> kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 19 10:56:43 <hostname> kernel: CR2: 0000000000000008 CR3: 000000087d4ee002 CR4: 00000000003606e0
Feb 19 10:56:43 <hostname> kernel: DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 19 10:56:43 <hostname> kernel: DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Feb 19 10:56:43 <hostname> kernel: Call Trace:
Feb 19 10:56:43 <hostname> kernel:  ? irq_finalize_oneshot.part.0+0xf0/0xf0
Feb 19 10:56:43 <hostname> kernel:  irq_thread_fn+0x28/0x60
...
Feb 19 10:56:43 <hostname> kernel: BUG: kernel NULL pointer dereference, address: 0000000000000001
Feb 19 10:56:43 <hostname> kernel: #PF: supervisor instruction fetch in kernel mode
Feb 19 10:56:43 <hostname> kernel: #PF: error_code(0x0010) - not-present page
Feb 19 10:56:43 <hostname> kernel: PGD 0 P4D 0 
Feb 19 10:56:43 <hostname> kernel: Oops: 0010 [#2] SMP PTI
Feb 19 10:56:43 <hostname> kernel: CPU: 1 PID: 967 Comm: irq/152-iwlwifi Tainted: G      D W  OE     5.4.0-65-generic #73-Ubuntu
Feb 19 10:56:43 <hostname> kernel: Hardware name: Dell Inc. XPS 15 9550/0N7TVV, BIOS 1.12.0 10/03/2019
Feb 19 10:56:43 <hostname> kernel: RIP: 0010:0x1
Feb 19 10:56:43 <hostname> kernel: Code: Bad RIP value.
Feb 19 10:56:43 <hostname> kernel: RSP: 0018:ffffa3b100dcfea0 EFLAGS: 00010286
Feb 19 10:56:43 <hostname> kernel: RAX: 0000000000000001 RBX: 0000000000000001 RCX: 0000000000000000
Feb 19 10:56:43 <hostname> kernel: RDX: ffffa3b100dcfec0 RSI: 0000000000000000 RDI: ffffa3b100dcfec0
Feb 19 10:56:43 <hostname> kernel: RBP: ffffa3b100dcfed0 R08: ffffffff85e5ece0 R09: 0000000000000000
Feb 19 10:56:43 <hostname> kernel: R10: ffffffff863971a8 R11: ffffa3b100dcf9e8 R12: ffff8b93c8ed5f00
Feb 19 10:56:43 <hostname> kernel: R13: ffff8b93c8ed6a64 R14: ffff8b93c8ed6a28 R15: 0000000000000000
Feb 19 10:56:43 <hostname> kernel: FS:  0000000000000000(0000) GS:ffff8b93dde40000(0000) knlGS:0000000000000000
Feb 19 10:56:43 <hostname> kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 19 10:56:43 <hostname> kernel: CR2: ffffffffffffffd7 CR3: 000000087d4ee002 CR4: 00000000003606e0
Feb 19 10:56:43 <hostname> kernel: DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000


Feb 19 11:06:57 <hostname> avahi-daemon[1227]: Registering new address record for <redacted> on lo.*.
Feb 19 11:06:57 <hostname> avahi-daemon[1227]: Withdrawing address record for ::1 on lo.
Feb 19 11:06:57 <hostname> avahi-daemon[1227]: Registering new address record for <redacted> on lo.*.
Feb 19 11:06:57 <hostname> kernel: [   25.353639] ------------[ cut here ]------------
Feb 19 11:06:57 <hostname> kernel: [   25.353640] General protection fault in user access. Non-canonical address?
Feb 19 11:06:57 <hostname> kernel: [   25.353646] WARNING: CPU: 7 PID: 1898 at arch/x86/mm/extable.c:126 ex_handler_uaccess+0x52/0x60
Feb 19 11:06:57 <hostname> kernel: [   25.353646] Modules linked in: xt_conntrack xt_MASQUERADE nf_conntrack_netlink nfnetlink xfrm_user xfrm_algo xt_addrtype iptable_filter iptable_nat nf_nat nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 bpfilter br_netfilter bridge stp llc nls_utf8 cifs fscache libdes ccm aufs overlay bluetooth ecdh_generic ecc sch_fq_codel binfmt_misc mei_hdcp intel_rapl_msr snd_hda_codec_hdmi intel_hid dell_laptop snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio uvcvideo videobuf2_vmalloc cdc_mbim videobuf2_memops snd_hda_intel videobuf2_v4l2 snd_intel_dspcfg cdc_wdm x86_pkg_temp_thermal videobuf2_common intel_powerclamp coretemp snd_hda_codec snd_usb_audio videodev snd_hda_core kvm_intel cdc_ncm snd_usbmidi_lib snd_hwdep snd_seq_midi usbnet snd_seq_midi_event kvm mii snd_rawmidi mc iwlmvm snd_pcm rapl snd_seq mac80211 joydev snd_seq_device dell_wmi usblp intel_cstate libarc4 snd_timer dell_smbios dcdbas input_leds sparse_keymap serio_raw wmi_bmof iwlwifi dell_wmi_descriptor intel_wmi_thunderbolt snd
Feb 19 11:06:57 <hostname> kernel: [   25.353679]  mei_me rtsx_pci_ms cfg80211 soundcore memstick hid_multitouch mei intel_pch_thermal processor_thermal_device intel_rapl_common intel_soc_dts_iosf int3403_thermal int3402_thermal int340x_thermal_zone int3400_thermal mac_hid acpi_thermal_rel acpi_pad evdi(OE) ppdev lp parport ip_tables x_tables autofs4 btrfs xor zstd_compress raid6_pq libcrc32c dm_crypt dm_mirror dm_region_hash dm_log usbhid hid_generic crct10dif_pclmul crc32_pclmul ghash_clmulni_intel rtsx_pci_sdmmc nouveau i915 aesni_intel crypto_simd cryptd mxm_wmi glue_helper ttm psmouse i2c_algo_bit i2c_i801 drm_kms_helper nvme syscopyarea sysfillrect sysimgblt rtsx_pci fb_sys_fops drm ahci nvme_core intel_lpss_pci intel_lpss libahci idma64 virt_dma i2c_hid hid video wmi [last unloaded: parport_pc]
Feb 19 11:06:57 <hostname> kernel: [   25.353698] CPU: 7 PID: 1898 Comm: auditbeat Tainted: G           OE     5.4.0-65-generic #73-Ubuntu
Feb 19 11:06:57 <hostname> kernel: [   25.353698] Hardware name: Dell Inc. XPS 15 9550/0N7TVV, BIOS 1.12.0 10/03/2019
Feb 19 11:06:57 <hostname> kernel: [   25.353700] RIP: 0010:ex_handler_uaccess+0x52/0x60
...

```


Uname -r: 5.4.0-65-generic


cat /etc/os-release 
NAME="Ubuntu"
VERSION="20.04.2 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.2 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

---

### Post by praseodym on 2021-02-19
Please show
```

lscpu
lspci -nnk
lsmod
uname -a
```

---

### Post by guiverc on 2021-02-19
I don't know sorry, but I'll provide what I found, and my thoughts
*Note: please read all; first two are likely useless*

**(1) clocksource**

A quick search online came up with the following being added to the kernel line

```
clocksource=tsc
```

I'll assume you're familiar with editing an entry in grub (which is a single time only, you can make the change permanent but I wouldn't until you're sure).  The bug I grabbed that from is **old**, and I'd hope doesn't apply with a 5.4 kernel, but I'd still likely consider trying it, though given your issue is intermittent & rare, this is likely unhelpful (*and may not apply anyway!*)

Source: [https://bugzilla.redhat.com/show_bug.cgi?id=1428556](https://bugzilla.redhat.com/show_bug.cgi?id=1428556)
[B]
(2) others[/B]

On others ([https://bugzilla.kernel.org/show_bug.cgi?id=196683](https://bugzilla.kernel.org/show_bug.cgi?id=196683)) a memory test is suggested, and many issues appeared to be related to Ryzen cpus.. but I don't know your CPU yet.
[B]
(3) try HWE kernel[/B]

In your case I'd consider trying the HWE kernel, which will mean 5.8 for 20.04/*focal* currently.  I personally wouldn't remove your GA (5.4) kernel. You can get details of how to add HWE to your system in the Server section of 

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

ie. 


```
 sudo apt install --install-recommends linux-generic-hwe-20.04 

```
[I]
FYI: it's in the Server section, as Ubuntu Desktop (GNOME) defaults to HWE by default for 20.04[/I]

Please note:  I have no idea, the first two are just from what I can see online and most likely are of no use to you, the third (HWE) is all I really can suggest.

---

