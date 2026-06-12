---
title: "randomly failing to boot (ndiswrapper problem?)"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by geraschenko on 2007-09-23
[EDIT: Resolved]

At least half the time, in no predictable pattern, my laptop fails to boot. This isn't a huge problem because I can reboot (sometimes a few times) until things work, and then everything seems to work fine, but I'd like to get to the bottom of it.

I'm running 64-bit Kubuntu Feisty on a Dell Vostro 1500. Here is my lspci output:```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```
If I recall properly, I followed this thread to get my wireless card working:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Unfortunately, I can't find anything in /var/log which matches what I see when my machine in starting up (enabling bootlogd doesn't work), so I copied the relevant parts (I think) to a text file by hand. I hope somebody can make more sense of it than I can.

When my laptop is booting, I look for the "* Configuring network interfaces... " line. If it goes on to say something about sensors, then everything is ok. Otherwise, I get
```
 * Mounting local filesystems... [ OK ]
 * Activating swapfile swap... [ OK ]
 * Configuring network interfaces... [ OK ]
[   29.535117] Unable to handle kernel paging request at fffc20000323b18 RIP:
[   29.535206]  [<fffc2000040b307>]
[   29.535445] PGD 3df5c067 PUD 3df5d067 PMD 3d1cb 067 PTE 0
[   29.535803] Oops: 0000 [1] SMP
[   29.536023] CPU 0
[   29.536173] Modules linked in: ndiswrapper eeprom i2c_i801 sbp2 parport_pc lp parport fuse snd_hda_intel snd_hda_codec snd_pcm_oss snd_pcm snd_mixer_oss uvcvideo snd_seq_dummy snd_seq_oss joydev snd_seq_midi snd_rawmidi videodev v4l1_compat v412_common ide_cd snd_seq_midi_event usbhid snd_seq snd_timer snd_seq_device hci_usb af_packet hid cdrom bluetooth snd sdhci nvidia(P) pcspkr psmouse serio_raw mmc_core soundcore generic i2c_core intel_agp shpchp pci_hotplug snd_page_alloc tsdev evdev xt_tcpudp nf_conntrack_ipv4 xt_state nf_conntrack nfnetlink ipt_REJECT xt_limit ipt_LOG iptable_filter ip_tables x_tables ext3 jbd mbcache sg sd_mod ohci1394 ieee1394 b44 mii ehci_hcd ata_generic uhci_hcd ahci libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap piix
[   29.542699] Pid: 4654, comm: modprobe Tainted: P      2.6.20-16-generic #2
[   29.542788] RIP: 0010:[<fffc2000040b307>]  [<fffc2000040b307>]
[   29.542945] RSP: 0018:ffff8100396b76f0  EFLAGS: 00010286
[   29.543032] RAX: ffffc20000323b18 RBX:

```
followed by a bunch more hex (like in the last few lines). Then
```
[   29.544960] Call Trace:
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:win2lin2+0xe/0x11
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:win2lin3+0x11/0x14
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:miniport_init+0xa7/0x170
[   29.545146]  [<ffffffff88b837a7>] task_rp_lock+0x4c/0x90
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:NdisDispatchPnp+0xab/0xc90
[   29.545146]  [<ffffffff88b837a7>] thread_return+0x77/0xf5
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IoAllocateIrp+0x86/0xa0
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:win2lin2+0xe/0x11
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IofCallDriver+0x70/0xa0
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:IoSendIrpTopDev+0xac/0xac/0x100
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:pnp_start_device+0xac/0x100
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:wrap_pnp_start_device+0x1f8/0x240
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[   29.545146]  [<ffffffff88b837a7>] sysfx_make_dirent+0x29/0xb0
[   29.545146]  [<ffffffff88b837a7>] pci_device_probe+0xe1/0x170
[   29.545146]  [<ffffffff88b837a7>] reall_probe+0xe5/0x190
[   29.545146]  [<ffffffff88b837a7>] __driver_attach+0x7c/0xd0
[   29.545146]  [<ffffffff88b837a7>] __driver_attach+0x0/0xd0
[   29.545146]  [<ffffffff88b837a7>] bus_for_each_dev+0x49/0x80
[   29.545146]  [<ffffffff88b837a7>] bus_add_driver+0x7e/0x1e0
[   29.545146]  [<ffffffff88b837a7>] __pci_register_driver+0x87/0xd0
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper:loader_init+0x15c/0x250
[   29.545146]  [<ffffffff88b837a7>] :ndiswrapper::wrapper_init+0x95/0xd2
[   29.545146]  [<ffffffff88b837a7>] sys_init_module+0x21/0x130
[   29.545146]  [<ffffffff88b837a7>] system_call+0x7e/0x83
[   29.548085]
[   29.549309]
[   29.549310] Code 66 8b 00 66 89 44 24 30 44 0f b7 44 24 30 41 8b c8 c1 e9 08

```
("[   29.545146]  [<ffffffff88b837a7>]" isn't actually repeated like that, but I didn't think it was important and I was copying this by hand)

Then nothing happens. I can scroll around using Shift+PgUp and Shift+PgDown, but that's it. Any help is welcome. Let me know if there is any other information I can provide.

---

### Post by geraschenko on 2007-09-29
This problem seems to have gone away after some updates that changed my /boot/grub/menu.lst (whatever adept told me to update ... there were only a few packages, and one of them was linux-headers).

I'm glad the problem is gone, but I'm still curious about what was causing it, and I'd really like to know how to get a boot log that shows me the things that scroll across my screen when I boot.

---

