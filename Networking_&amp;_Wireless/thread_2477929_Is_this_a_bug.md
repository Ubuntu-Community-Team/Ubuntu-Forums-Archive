---
title: "Is this a bug?"
date: 2022-08-11
forum: Networking &amp; Wireless
---

### Post by blackxiao on 2022-08-11
I am running the ubuntu-server version on a new server. I heard using the kernel-5.18 will be faster and the I upgraded the kernel from  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18.12/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18.12/)  a few days ago. But after about half a month, the ethernet network suddenly did not work. 
"Ip addr" shows the interface with "[NO-CARRIER]" like
```

eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 100

```The wireless is still working. I can be sure that the cable is fine.
The dmesg shows a lot of  entries like
```

[938036.920107] igb 0000:e4:00.0 eno1: malformed Tx packet detected and dropped, LVMMC:0xffffffff

```
The ethernet controller is
```

e4:00.0 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)

```
I tried to "rmmod igb" driver and tried to modprobe the igb again, and dmesg shows
```

[967952.688335] ------------[ cut here ]------------
[967952.688336] igb: Failed to read reg 0x18!
[967952.688371] WARNING: CPU: 64 PID: 56227 at drivers/net/ethernet/intel/igb/igb_main.c:745 igb_rd32.cold+0x3a/0x46 [igb]
[967952.688400] Modules linked in: igb(+) cpuid tls intel_rapl_msr intel_rapl_common amd64_edac edac_mce_amd kvm_amd kvm rapl wmi_bmof 88x2bu(
OE) ipmi_ssif nls_iso8859_1 joydev input_leds cfg80211 ccp acpi_ipmi ptdma k10temp ipmi_si mac_hid sch_fq_codel dm_multipath scsi_dh_rdac ipmi
_devintf scsi_dh_emc ipmi_msghandler scsi_dh_alua msr parport_pc ppdev lp parport ramoops pstore_blk reed_solomon pstore_zone mtd efi_pstore i
p_tables x_tables autofs4 hid_generic rndis_host usbhid cdc_ether usbnet hid mii btrfs blake2b_generic zstd_compress raid10 raid456 async_raid
6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear ast drm_vram_helper drm_ttm_helper ttm cr
ct10dif_pclmul crc32_pclmul ghash_clmulni_intel drm_kms_helper syscopyarea aesni_intel sysfillrect crypto_simd sysimgblt cryptd fb_sys_fops nv
me xhci_pci dca ahci libahci i2c_algo_bit megaraid_sas drm nvme_core xhci_pci_renesas i2c_piix4 wmi [last unloaded: igb]
[967952.688477] CPU: 64 PID: 56227 Comm: kworker/64:0 Tainted: G        W  OE     5.18.12-051812-generic #202207150942
[967952.688481] Hardware name: Supermicro AS -4124GS-TNR/H12DSG-O-CPU, BIOS 2.4 04/22/2022
[967952.688483] Workqueue: events work_for_cpu_fn
[967952.688490] RIP: 0010:igb_rd32.cold+0x3a/0x46 [igb]
[967952.688500] Code: c7 c6 13 05 4b c0 e8 bd c7 f1 cd 48 8b bb 30 ff ff ff e8 95 c2 84 cd 84 c0 74 16 44 89 ee 48 c7 c7 a8 11 4b c0 e8 ad fd 
e7 cd <0f> 0b e9 77 f9 fd ff e9 8f f9 fd ff 0f b6 d0 be 00 00 04 00 48 c7
[967952.688502] RSP: 0018:ffffb38049567d80 EFLAGS: 00010282
[967952.688504] RAX: 0000000000000000 RBX: ffff9ad351958f10 RCX: 0000000000000027
[967952.688505] RDX: ffff9b4f7f6215a8 RSI: 0000000000000001 RDI: ffff9b4f7f6215a0
[967952.688506] RBP: ffffb38049567d98 R08: 000000000000001d R09: 0000000000189f78
[967952.688507] R10: 0000000000ffff10 R11: 000000000000000f R12: 00000000ffffffff
[967952.688508] R13: 0000000000000018 R14: 0000000000000000 R15: ffff99518ee180d0
[967952.688509] FS:  0000000000000000(0000) GS:ffff9b4f7f600000(0000) knlGS:0000000000000000
[967952.688510] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[967952.688511] CR2: 00007ffcb2b73b98 CR3: 00000380105f0002 CR4: 0000000000770ee0
[967952.688512] PKRU: 55555554
[967952.688513] Call Trace:
[967952.688516]  <TASK>
[967952.688519]  igb_get_invariants_82575+0xa0/0x710 [igb]
[967952.688530]  igb_probe+0x3f8/0x1010 [igb]
[967952.688538]  local_pci_probe+0x4f/0x90
[967952.688543]  work_for_cpu_fn+0x1e/0x30
[967952.688545]  process_one_work+0x21f/0x3f0
[967952.688548]  worker_thread+0x204/0x3e0
[967952.688551]  ? rescuer_thread+0x3a0/0x3a0
[967952.688552]  kthread+0xf2/0x120
[967952.688554]  ? kthread_complete_and_exit+0x30/0x30
[967952.688556]  ret_from_fork+0x22/0x30
[967952.688561]  </TASK>
[967952.688562] ---[ end trace 0000000000000000 ]---
[967953.011633] igb 0000:e4:00.1: PHY reset is blocked due to SOL/IDER session.
[967954.750679] igb 0000:e4:00.1: The NVM Checksum Is Not Valid
[967955.215509] igb: probe of 0000:e4:00.1 failed with error -5


```
The eno1 would never show up in "ip link".
Is this a bug? Do I need to report this one? Tomorrow I will reboot the server. I hope after the reboot it will go back to normal.

---

### Post by TheFu on 2022-08-11
Perhaps the NIC is failing?
Or the switch port?

---

### Post by Doug S on 2022-08-12
Your kernel taint flags show external unsigned modules loaded, which would be of concern for any escalation.
You mention things have been working for a half month, but you tried the newer kernel few days ago. Does going back to the previous kernel work? Also, and just as a test, try the latest mainline PPA kernel, [5.19.1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19.1/") at the time of writing this. There have been 2 recent commits (mid June) to the file listed in your posted log.

EDIT: I see that kernel 5.18.12 is fairly old (by bleeding edge standards). You should also try [5.18.17]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.18.17/")

Let us know your findings.

---

### Post by blackxiao on 2022-08-13
Thanks. I didn't see this post and rebooted the machine, and it returned to normal. It still runs the 5.18.12 kernel. I suspect whether the problem was caused by the ubuntu unattended-upgrade which upgraded the older kernels and modules. I've now disabled the unattended-upgrade. 
Maybe I can try the newer kernel on next reboot if this problem happens again.

---

