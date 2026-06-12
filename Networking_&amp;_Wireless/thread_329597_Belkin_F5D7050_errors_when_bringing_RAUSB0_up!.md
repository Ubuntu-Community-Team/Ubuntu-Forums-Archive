---
title: "Belkin F5D7050 errors when bringing RAUSB0 up!"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by Den4Wa on 2007-01-01
I have followed the WiFiDocs/Driver/RalinkRT73 docs to compile and load rt73 driver for a Belkin F5D7050 ver.3 USB adapter.  My system sees the module ok and I followed al the steps to the files and config where they need to be, but when I try to do "ifconfig rausb0 up" shows "killed" on cmd line.  Dmesg gives the following errors:

[  777.862681] rt73 driver version - 1.0.3.6
[  778.050495] Unable to handle kernel paging request at 000000000046c000 RIP:
[  778.050501] <ffffffff80214670>{__memset+32}
[  778.050508] PGD 2ac30067 PUD 2ba3a067 PMD 2b57c067 PTE 0
[  778.050512] Oops: 0002 [1] PREEMPT SMP
[  778.050515] CPU 0
[  778.050516] Modules linked in: rfcomm l2cap bluetooth ppdev driverloader cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ipv6 dm_mod md_mod sr_mod sbp2 lp snd_mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device floppy usb_storage tsdev parport_pc parport pcspkr usblp rt73 analog psmouse gameport serio_raw snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss usbhid nvidia snd_pcm snd_timer i2c_core snd soundcore snd_page_alloc shpchp pci_hotplug af_packet sg evdev ext3 jbd ide_generic ohci_hcd ohci1394 ieee1394 forcedeth ehci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sd_mod sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[  778.050552] Pid: 6160, comm: ifconfig Tainted: P      2.6.15-27-amd64-generic #1
[  778.050555] RIP: 0010:[<ffffffff80214670>] <ffffffff80214670>{__memset+32}
[  778.050560] RSP: 0018:ffff81002aebdca0  EFLAGS: 00010216
[  778.050563] RAX: 0000000000000000 RBX: ffff810036f60500 RCX: 0000000000000200
[  778.050565] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 000000000046c000
[  778.050567] RBP: 0000000000000000 R08: 0000000000000000 R09: 000000000046c000
[  778.050570] R10: 0000000000000002 R11: ffffffff801e7e90 R12: 000000000046d000
[  778.050572] R13: ffff810036f60500 R14: 000000000046c000 R15: 0000000000000000
[  778.050576] FS:  00002aaaaadfb6d0(0000) GS:ffffffff8044b800(0000) knlGS:0000000000000000
[  778.050578] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  778.050581] CR2: 000000000046c000 CR3: 000000003cbcd000 CR4: 00000000000006e0
[  778.050584] Process ifconfig (pid: 6160, threadinfo ffff81002aebc000, task ffff81002a247040)
[  778.050586] Stack: ffffffff887cbd48 000000000000006b 8000040000000006 ffff81003c1d0800
[  778.050591]        ffffffff887c0ae3 ffff81002c864380 0000000000000000 ffff81000046c000
[  778.050596]        ffff810036f60500 ffff810000000000
[  778.050599] Call Trace:<ffffffff887cbd48>{:rt73:RTMPReadParametersFromFile+328}
[  778.050616]        <ffffffff887c0ae3>{:rt73:RTUSB_VendorRequest+115} <ffffffff887c0ae3>{:rt73:RTUSB_VendorRequest+115}
[  778.050642]        <ffffffff887c0c81>{:rt73:RTUSBWriteMACRegister+49} <ffffffff887b541d>{:rt73:usb_rtusb_open+269}
[  778.050664]        <ffffffff802a53fe>{dev_open+62} <ffffffff802a44be>{dev_change_flags+110}
[  778.050676]        <ffffffff802f0752>{devinet_ioctl+722} <ffffffff802a646f>{dev_ioctl+863}
[  778.050686]        <ffffffff801a1a55>{__path_lookup_intent_open+149} <ffffffff80299e1c>{sock_ioctl+588}
[  778.050703]        <ffffffff801a4fff>{do_ioctl+47} <ffffffff801a531b>{vfs_ioctl+683}
[  778.050712]        <ffffffff8018edca>{get_unused_fd+234} <ffffffff801a53bc>{sys_ioctl+108}
[  778.050722]        <ffffffff8010febe>{system_call+126}
[  778.050738]
[  778.050739] Code: f3 48 ab 44 89 c1 f3 aa 4c 89 c8 c3 90 90 90 90 65 4c 8b 04
[  778.050747] RIP <ffffffff80214670>{__memset+32} RSP <ffff81002aebdca0>
[  778.050751] CR2: 000000000046c000
[  778.050753]

I am in need of some assistance as to why this is happening; (1) operator error (grin); (2) AMD64 incompatibility with RT73 driver; (3) Bug?  I tried the Ralink site and found a separate firmware file and tried that with the same result.  Any assistance would be greatly appreciated!  

Den4Wa ](*,)

---

