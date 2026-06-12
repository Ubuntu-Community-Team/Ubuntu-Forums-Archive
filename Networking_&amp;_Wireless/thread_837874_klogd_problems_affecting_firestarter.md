---
title: "klogd problems affecting firestarter"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by dspdude2000 on 2008-06-22
The problem I have is I cannot see any events on the Firestarter events tab.  The events show up in dmesg but they never make it to /var/log/kern.log (which is where they are supposed to end up according to my syslog.conf file).  If I restart klogd, then a few events from the dmesg buffer get logged, but it immediately stops working and I have to restart klogd again if I want to see more messages.

I looked at /var/log/kern.log and saw that all dmesg messages after a certain time were not getting logged.  At the time that things stop working I get a kernel oops as seen here:

```

[   69.207584] ndiswrapper: using IRQ 10
[   69.481215] BUG: unable to handle kernel paging request at virtual address f097e0d0
[   69.481374] printing eip: f097e0d0 *pde = 2e0c2067 *pte = 00000000 
[   69.481636] Oops: 0000 [#1] SMP 
[   69.481828] Modules linked in: ndiswrapper ppdev ipv6 speedstep_lib cpufreq_stats cpufreq_conservative cpufreq_userspace cpufreq_powersave cpufreq_ondemand freq_table container video output dock sbs sbshc battery iptable_filter ip_tables x_tables af_packet ac lp rfkill_input snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss usblp snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy arc4 ecb blkcipher evdev dcdbas parport_pc parport snd_seq_oss snd_seq_midi snd_rawmidi serio_raw rfkill psmouse snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore emu10k1_gp gameport i2c_core button pcspkr iTCO_wdt iTCO_vendor_support shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic pata_acpi floppy uhci_hcd ata_piix 3c59x mii usbcore libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   69.487774] 
[   69.487846] Pid: 3792, comm: ipolldevd Tainted: P        (2.6.24-19-generic #1)
[   69.487935] EIP: 0060:[<f097e0d0>] EFLAGS: 00010247 CPU: 0
[   69.488019] EIP is at 0xf097e0d0
[   69.488094] EAX: dfb69134 EBX: dfb69134 ECX: dfb69138 EDX: dfb690d8
[   69.488173] ESI: ee3bc180 EDI: ee3bc180 EBP: f097e0d0 ESP: ef3edf84
[   69.488252]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   69.488331] Process ipolldevd (pid: 3792, ti=ef3ec000 task=ef3ef700 task.ti=ef3ec000)
[   69.488412] Stack: c013ce8f 00000000 000000ff 00000000 00000000 ee3bc184 ee3bc18c ee3bc180 
[   69.489032]        c013d930 ee3bc184 c013d9b4 00000000 ef3ef700 c0140c40 ef3edfbc ef3edfbc 
[   69.489651]        fffffffc ee3bc180 c013d930 00000000 c0140982 c0140940 00000000 00000000 
[   69.490270] Call Trace:
[   69.490409]  [<c013ce8f>] run_workqueue+0xbf/0x160
[   69.490583]  [<c013d930>] worker_thread+0x0/0xe0
[   69.490726]  [<c013d9b4>] worker_thread+0x84/0xe0
[   69.490873]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[   69.491030]  [<c013d930>] worker_thread+0x0/0xe0
[   69.491173]  [<c0140982>] kthread+0x42/0x70
[   69.491309]  [<c0140940>] kthread+0x0/0x70
[   69.491453]  [<c0105677>] kernel_thread_helper+0x7/0x10
[   69.491617]  =======================
[   69.491690] Code:  Bad EIP value.
[   69.491885] EIP: [<f097e0d0>] 0xf097e0d0 SS:ESP 0068:ef3edf84
[   69.492089] ---[ end trace c1a50cefb564d6fe ]---
[   69.740704] wlan0: ethernet device 00:18:39:15:1f:07 using NDIS driver: wmp54gs, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf

```

The last message that gets logged to /var/log/kern.log is
```

[   69.207584] ndiswrapper: using IRQ 10

```

I don't know if the problem is related to ndiswrapper or what.  I manually built a new version of ndiswrapper (1.53 instead of 1.52) but that didn't help.  I've never been able to get the native kernel support for my wireless chipset (Broadcom 4318 ) to work so that is why I use ndiswrapper.  Any ideas on how to fix this problem?

---

### Post by dspdude2000 on 2008-06-23
The problem is definitely related to ndiswrapper somehow because if I disable it (so that my internet doesn't work), the kernel oops doesn't happen.  If anyone has any insight on this, let me know.  Otherwise, I'll try to get the native support to work (for the umpteenth time).

---

