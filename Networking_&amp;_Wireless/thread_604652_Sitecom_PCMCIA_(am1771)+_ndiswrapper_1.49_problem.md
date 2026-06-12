---
title: "Sitecom PCMCIA (am1771)+ ndiswrapper 1.49 problem"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by dobs on 2007-11-06
Hi,

I have problem using ndiswrapper 1.49 (i've compile the last version), with ubuntu 7.04 and PCMCIA wireless card (AM1771 chip)

AM1771 is installed in a [Sitecom pcmcia ](http://sitecom.com/drivers_result.php?groupid=5&productid=496)

I've installed the driver linked in ndiswrapper's site driver list for my chipset.

if i type "sudo ndiswrapper -l" i riceve this output

```

netam772 : driver installed
        device (1022:2003) present

```

I'm using a custom kernel with preemptive enabled.

The problem is that, when try to do modprobe i get this :S 

```

dobs@dobs-laptop:~$ sudo modprobe ndiswrapper
Password:
dobs@dobs-laptop:~$ 
Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.897810] PREEMPT SMP 

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.897807] Oops: 0000 [#1]

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898032] Process NetworkManager (pid: 5732, ti=c379c000 task=c2129570 task.ti=c379c000)

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898038] Stack: c379ddaa d05463be cde00000 c379de5c c379ddaa c379de4c c379de48 c379df40 

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898053]        00000002 cb3fe800 e43fe8a4 cb3fe8b4 0293a73c 0ec8e924 c072f000 7461000f 

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898068]        333d6d69 30343534 34333930 c1be0034 000000b9 000006d4 00000000 c2129680 

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898082] Call Trace:

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898157]  [preempt_schedule+102/128] preempt_schedule+0x66/0x80

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898177]  [<d053bad5>] mp_request+0x3b5/0x3e0 [ndiswrapper]

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898220]  [__next_cpu+18/48] __next_cpu+0x12/0x30

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898236]  [find_busiest_group+302/1408] find_busiest_group+0x12e/0x580

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898273]  [ioctl_standard_call+434/928] ioctl_standard_call+0x1b2/0x3a0

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898301]  [__switch_to+196/544] __switch_to+0xc4/0x220

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898331]  [wireless_process_ioctl+822/992] wireless_process_ioctl+0x336/0x3e0

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898340]  [<d0529720>] iw_get_scan+0x0/0x850 [ndiswrapper]

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898369]  [<d0529720>] iw_get_scan+0x0/0x850 [ndiswrapper]

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898399]  [_read_unlock+13/48] _read_unlock+0xd/0x30

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898408]  [dev_load+42/96] dev_load+0x2a/0x60

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898416]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898429]  [dev_ioctl+531/912] dev_ioctl+0x213/0x390

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898446]  [lock_hrtimer_base+39/96] lock_hrtimer_base+0x27/0x60

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.897949] EIP:    0060:[<d052985c>]    Tainted: P      VLI

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.897947] CPU:    0

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898007] EIP is at iw_get_scan+0x13c/0x850 [ndiswrapper]

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898013] eax: 00000000   ebx: c072e161   ecx: 00000000   edx: e43fe8a4

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898020] esi: c379ddb9   edi: c379de5c   ebp: c072e161   esp: c379dd6c

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898026] ds: 007b   es: 007b   ss: 0068

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.897952] EFLAGS: 00010246   (2.6.20.3-ubuntu1-sinner #1)

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898463]  [_spin_unlock_irqrestore+25/48] _spin_unlock_irqrestore+0x19/0x30

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898471]  [hrtimer_try_to_cancel+51/80] hrtimer_try_to_cancel+0x33/0x50

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898494]  [hrtimer_nanosleep+73/272] hrtimer_nanosleep+0x49/0x110

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898503]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898514]  [do_ioctl+43/144] do_ioctl+0x2b/0x90

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898530]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898547]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898561]  [sysenter_past_esp+105/157] sysenter_past_esp+0x69/0x9d

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898584]  [schedule+1763/2688] __sched_text_start+0x6e3/0xa80

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898604]  =======================

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898607] Code: 00 8b 7c 24 18 31 c0 f3 ab 8b 54 24 28 66 c7 84 24 de 00 00 00 15 8b 66 c7 84 24 e0 00 00 00 01 00 66 c7 84 24 dc 00 00 00 14 00 <8b> 42 04 89 84 24 e2 00 00 00 0f b7 42 08 66 89 84 24 e6 00 00 

Message from syslogd@dobs-laptop at Tue Nov  6 16:26:50 2007 ...
dobs-laptop kernel: [  800.898679] EIP: [<d052985c>] iw_get_scan+0x13c/0x850 [ndiswrapper] SS:ESP 0068:c379dd6c

```

So i try "dmesg | grep ndiswrapper": 

```

[  796.321558] ndiswrapper version 1.49 loaded (smp=yes, preempt=yes)
[  796.511285] ndiswrapper: driver netam772 (Advanced Micro Devices,10/27/2003,2.0.0.4) loaded
[  796.513518] ndiswrapper: using IRQ 10
[  796.514432] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 3, return_address: d05f4b8d
[  796.514685] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x0
[  796.514833] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x5
[  796.514981] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x0
[  797.119413] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BBÂ«Â»)
[  797.422386] usbcore: registered new interface driver ndiswrapper
[  800.897816] Modules linked in: ndiswrapper ipv6 8139cp 8139too mii binfmt_misc rfcomm l2cap bluetooth ppdev i915 drm capability commoncap cpufreq_stats cpufreq_conservative cpufreq_userspace cpufreq_powersave cpufreq_ondemand freq_table dev_acpi sony_acpi tc1100_wmi pcc_acpi asus_acpi button container ac dock battery backlight video sbs i2c_ec i2c_core af_packet lp fuse snd_intel8x0 snd_ac97_codec joydev ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event pcmcia parport_pc parport snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc serio_raw psmouse yenta_socket rsrc_nonstatic pcmcia_core iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg usbhid hid sr_mod cdrom sd_mod ata_generic floppy ata_piix libata scsi_mod generic uhci_hcd usbcore thermal processor fan
[  800.898007] EIP is at iw_get_scan+0x13c/0x850 [ndiswrapper]
[  800.898177]  [<d053bad5>] mp_request+0x3b5/0x3e0 [ndiswrapper]
[  800.898340]  [<d0529720>] iw_get_scan+0x0/0x850 [ndiswrapper]
[  800.898369]  [<d0529720>] iw_get_scan+0x0/0x850 [ndiswrapper]
[  800.898679] EIP: [<d052985c>] iw_get_scan+0x13c/0x850 [ndiswrapper] SS:ESP 0068:c379dd6c

```

the problem seems to be here:

```

[  797.119413] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)

```

what mean this? Someone can help me? :dry:

---

### Post by johnc@crosslink.net on 2007-12-20
kinda' sounds like where i's at. got this here c600 with a dlink dwl-g630, a brand new kernel, and same pesky syslog message 'bout some mode 717 & error 6. 1.51 on the ndis thingasmabob. i'm goinna' go here: [http://hostap.epitest.fi/releases/wpa_supplicant-0.5.9.tar.gz]("http://hostap.epitest.fi/releases/wpa_supplicant-0.5.9.tar.gz")

Maybe I'll be back, or maybe i'll see how many pieces a crappy pcmcia card breaks into when run over by a prius. i'm sure the NEW card will work!

BTW - this is my son's laptop and was using a fawn image before the 'upgrade'. had to manually mkdir misc. did you see that, too?

as for me - gusty gave me compiz & standby on my compaq v6130us. 1st lesson for all yous noobs -- always build yr. kernel if yr. running a laptop. then you can ask questions.

on desktops, i'm just using the image - maybe I'll stop using Debian for servers now (but, of course, still build the kern). Ubuntu all the way!

---

### Post by johnc@crosslink.net on 2007-12-20
that done fixed this here error:
set_iw_encr_mode:717 setting encryption to mode 6 failed

just go git you a brand new wpa_supplicant (see above)

now i jest gotta' figure out the right wpa combo & i'm G2G.

---

