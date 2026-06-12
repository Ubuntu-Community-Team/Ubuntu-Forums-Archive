---
title: "Wg111t Drops connection with ndiswapper"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by FireSoul on 2008-06-10
hi how are you all :popcorn:

after days and days i knew how to compile ndiswapper ( yeah i am a complete noobe but i learned a lot for a week and a half in ubuntu )
i installed the windows drivers ... ( tried all the versions) 

and what happens is that .. it connects easily ( after removing and adding the module) but after random amount of time ... it stops transfaring any data

dmesg gives this
> [ 234.557676] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 251.845129] wlan0: no IPv6 routers present


so iwconfig ..( it says i am connected ) i try and ping my netgear router and it says unreachable 
iwconfig gives this ..
> wlan0 IEEE 802.11g ESSID:"Al-alem"
          Mode:Managed Frequency:2.437 GHz Access Point: 00:14:6C:F0:1B:0E
          Bit Rate=108 Mb/s
          Power Management:off
          Link Quality:48/100 Signal level:-65 dBm Noise level:-96 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

here is the big news ... when i try to remove the module and add it again ..
the terminal just hangs , i opened another terminal and dmesg gives this

> [ 6134.430003] BUG: unable to handle kernel paging request at virtual address f8be81cc
[ 6134.430008] printing eip: f8db9d06 *pde = 37c47067 *pte = 00000000
[ 6134.430015] Oops: 0000 [#1] SMP
[ 6134.430018] Modules linked in: af_packet ndiswrapper binfmt_misc ipv6 rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_stats cpufreq_conservative cpufreq_ondemand cpufreq_powersave cpufreq_userspace freq_table video output sbs sbshc container dock battery iptable_filter ip_tables x_tables ac it87 hwmon_vid sbp2 lp nvidia(P) snd_hda_intel snd_pcm_oss i2c_core snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep serio_raw snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button intel_agp agpgart snd shpchp pci_hotplug evdev parport_pc parport soundcore iTCO_wdt iTCO_vendor_support psmouse pcspkr ext3 jbd mbcache loop sg sr_mod sd_mod cdrom pata_acpi ata_generic usb_storage libusual pata_it821x ata_piix ohci1394 ieee1394 uhci_hcd libata ehci_hcd scsi_mod usbcore tg3 thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 6134.430090]
[ 6134.430093] Pid: 9253, comm: modprobe Tainted: P (2.6.24-18-generic #1)
[ 6134.430096] EIP: 0060:[<f8db9d06>] EFLAGS: 00210246 CPU: 1
[ 6134.430102] EIP is at 0xf8db9d06
[ 6134.430105] EAX: f8be81cc EBX: da7ef628 ECX: 00200246 EDX: 00000000
[ 6134.430107] ESI: f8be81cc EDI: c047c8a0 EBP: dad40480 ESP: d4757ccc
[ 6134.430110] DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 6134.430113] Process modprobe (pid: 9253, ti=d4756000 task=ce4a5140 task.ti=d4756000)
[ 6134.430115] Stack: c047c8a0 00200246 f8b22d6f da7ef628 f8be81cc 00000000 00000000 e6767d00
[ 6134.430122] dc350e40 e6767d00 f8b2b4b8 c02153d0 c021624b c0403ee0 f7c8d080 c02153ab
[ 6134.430129] dad40370 e6767d00 e0cf4b20 e6767db0 dad40480 f8b26815 e0cf4b20 e6767d00
[ 6134.430139] Call Trace:
[ 6134.430147] [<f8b22d6f>] kdpc_worker+0x9f/0x110 [ndiswrapper]
[ 6134.430188] [<f8b2b4b8>] pdoDispatchPnp+0x148/0x3f0 [ndiswrapper]
[ 6134.430209] [<c02153d0>] kobject_release+0x0/0x10
[ 6134.430220] [<c021624b>] kref_put+0x2b/0xa0
[ 6134.430234] [<c02153ab>] kobject_cleanup+0x3b/0x60
[ 6134.430253] [<f8b26815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[ 6134.430282] [<f8b2c87d>] wrap_ndis_remove_device+0x15d/0x1a0 [ndiswrapper]
[ 6134.430310] [<f8b2694e>] IoAsyncForwardIrp+0x2e/0x40 [ndiswrapper]
[ 6134.430336] [<f8b2d29a>] NdisDispatchPnp+0x16a/0xfc0 [ndiswrapper]
[ 6134.430371] [<c01a2c9c>] d_rehash+0x1c/0x30
[ 6134.430381] [<c01cc49e>] proc_lookup+0xee/0x100
[ 6134.430395] [<c0121084>] kunmap_atomic+0x84/0xb0
[ 6134.430402] [<c012103d>] kunmap_atomic+0x3d/0xb0
[ 6134.430441] [<c012270b>] enqueue_entity+0x2b/0x60
[ 6134.430454] [<c0122767>] enqueue_task_fair+0x27/0x30
[ 6134.430480] [<f8b26521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
[ 6134.430514] [<c031c1e8>] _spin_lock_bh+0x8/0x20
[ 6134.430524] [<f8b22604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
[ 6134.430559] [<f8b26815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[ 6134.430598] [<f8b2b85b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[ 6134.430649] [<f8b2b933>] pnp_remove_device+0x73/0x1d0 [ndiswrapper]
[ 6134.430690] [<f88e66b0>] usb_unbind_interface+0x50/0xb0 [usbcore]
[ 6134.430723] [<c0282404>] __device_release_driver+0x64/0xa0
[ 6134.430737] [<c028295b>] driver_detach+0xcb/0xd0
[ 6134.430754] [<c0281f53>] bus_remove_driver+0x73/0xa0
[ 6134.430769] [<f88e5fba>] usb_deregister+0x9a/0xb0 [usbcore]
[ 6134.430804] [<f8b1a7e3>] loader_exit+0x13/0x90 [ndiswrapper]
[ 6134.430825] [<c015e1f9>] stop_machine_run+0x39/0x50
[ 6134.430838] [<f8b2b225>] module_cleanup+0x5/0x30 [ndiswrapper]
[ 6134.430859] [<c01521a2>] sys_delete_module+0x112/0x190
[ 6134.430878] [<c01804a0>] do_munmap+0x180/0x1f0
[ 6134.430917] [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 6134.430961] =======================
[ 6134.430963] Code: c3 d8 f8 8b 46 14 6a 00 6a 58 50 ff 15 2c c3 d8 f8 c7 46 14 00 00 00 00 33 c0 5e 59 c2 04 00 cc cc cc cc cc cc 56 8b 74 24 0c 57 <8b> 3e 8d 46 1c 50 ff 15 70 c3 d8 f8 8b 07 8a 88 40 06 00 00 84
[ 6134.431050] EIP: [<f8db9d06>] 0xf8db9d06 SS:ESP 0068:d4757ccc
[ 6134.431063] ---[ end trace 57b821cd16f052d8 ]---


please i need your help
after a week on ubuntu i don't even want to boot on vista ... i feel sick even when it is loading
and i can't have a wired connection cause the router is 3 rooms away ..
so please HELP ME:(

---

### Post by FireSoul on 2008-06-10
come on not even a single replay

---

### Post by FireSoul on 2008-06-10
Up Up Up Up

---

### Post by FireSoul on 2008-06-10
at least one replay for god sake

---

### Post by FireSoul on 2008-06-11
fly fly up in the sky ... :P

---

### Post by FireSoul on 2008-06-15
hello no answer

i really need help

---

### Post by csokiszabi on 2009-05-10
Hi

I know that it is not much help but i have exactly the same problem... i have no solution yet
At least you know that you are not alone :)

---

