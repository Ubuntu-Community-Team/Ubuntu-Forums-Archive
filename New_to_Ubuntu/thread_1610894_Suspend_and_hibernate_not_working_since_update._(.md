---
title: "Suspend and hibernate not working since update. :("
date: 2010-11-01
forum: New to Ubuntu
---

### Post by jon.reeve on 2010-11-01
Suspend and hibernate no longer work on my laptop, since upgrading to Maverick. It suspends OK but then it when it resumes I just get a blank screen. It's unresponsive and I have to hard-reset. Here are (what I think are) the appropriate log lines: 

```
Nov  1 19:43:08 jon-laptop kernel: [ 1205.997541] =>>>>>>>>>>=============================>set power:0,0!
Nov  1 19:43:08 jon-laptop kernel: [ 1205.997556] Timeout 1
Nov  1 19:43:24 jon-laptop kernel: [ 1221.732581] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Nov  1 19:43:24 jon-laptop kernel: [ 1221.880929] =>>>>>>>>>>=============================>set power:1,114!
Nov  1 19:43:27 jon-laptop kernel: [ 1225.311157] PM: Syncing filesystems ... done.
Nov  1 19:43:35 jon-laptop kernel: [ 1225.540919] Freezing user space processes ... (elapsed 0.01 seconds) done.
Nov  1 19:43:35 jon-laptop kernel: [ 1225.556289] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Nov  1 19:43:35 jon-laptop kernel: [ 1225.572341] Suspending console(s) (use no_console_suspend to debug)
Nov  1 19:43:35 jon-laptop kernel: [ 1225.572920] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  1 19:43:35 jon-laptop kernel: [ 1225.573389] sd 0:0:0:0: [sda] Stopping disk
Nov  1 19:43:35 jon-laptop kernel: [ 1226.028890] PM: suspend of drv:sd dev:0:0:0:0 complete after 455.965 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.028943] PM: suspend of drv:scsi dev:target0:0:0 complete after 455.890 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.028983] PM: suspend of drv:scsi dev:host0 complete after 455.770 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.070961] PM: suspend of drv:psmouse dev:serio1 complete after 498.088 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.077675] r8180 0000:02:00.0: PCI INT A disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.078149] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.078241] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.078305] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.078399] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.078545] pciehp 0000:00:1c.0:pcie04: pciehp_suspend ENTRY
Nov  1 19:43:35 jon-laptop kernel: [ 1226.079066] i915 0000:00:02.0: PCI INT A disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.092148] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.092255] pciehp 0000:00:1c.1:pcie04: pciehp_suspend ENTRY
Nov  1 19:43:35 jon-laptop kernel: [ 1226.180225] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov  1 19:43:35 jon-laptop kernel: [ 1226.196127] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.505 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.196182] PM: suspend of drv: dev:pci0000:00 complete after 116.964 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.196219] PM: suspend of devices complete after 623.584 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.196235] PM: suspend devices took 0.624 seconds
Nov  1 19:43:35 jon-laptop kernel: [ 1226.196726] pcieport 0000:00:1c.0: wake-up capability enabled by ACPI
Nov  1 19:43:35 jon-laptop kernel: [ 1226.228383] PM: late suspend of devices complete after 32.131 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.228457] ACPI: Preparing to enter system sleep state S3
Nov  1 19:43:35 jon-laptop kernel: [ 1226.228918] PM: Saving platform NVS memory
Nov  1 19:43:35 jon-laptop kernel: [ 1226.234830] Disabling non-boot CPUs ...
Nov  1 19:43:35 jon-laptop kernel: [ 1226.340070] CPU 1 is now offline
Nov  1 19:43:35 jon-laptop kernel: [ 1226.340076] SMP alternatives: switching to UP code
Nov  1 19:43:35 jon-laptop kernel: [ 1226.346441] Extended CMOS year: 2000
Nov  1 19:43:35 jon-laptop kernel: [ 1226.346441] PM: Restoring platform NVS memory
Nov  1 19:43:35 jon-laptop kernel: [ 1226.346441] Extended CMOS year: 2000
Nov  1 19:43:35 jon-laptop kernel: [ 1226.346441] Enabling non-boot CPUs ...
Nov  1 19:43:35 jon-laptop kernel: [ 1226.346441] SMP alternatives: switching to SMP code
Nov  1 19:43:35 jon-laptop kernel: [ 1226.352086] Booting Node 0 Processor 1 APIC 0x1
Nov  1 19:43:35 jon-laptop kernel: [ 1226.345405] Initializing CPU#1
Nov  1 19:43:35 jon-laptop kernel: [ 1226.345405] Atom PSE erratum detected, BIOS microcode update recommended
Nov  1 19:43:35 jon-laptop kernel: [ 1226.469046] CPU1 is up
Nov  1 19:43:35 jon-laptop kernel: [ 1226.469429] ACPI: Waking up from system sleep state S3
Nov  1 19:43:35 jon-laptop kernel: [ 1226.471119] PM: early resume of devices complete after 1.315 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.471594] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  1 19:43:35 jon-laptop kernel: [ 1226.475992] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476062] pciehp 0000:00:1c.0:pcie04: pciehp_resume ENTRY
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476076] pciehp 0000:00:1c.1:pcie04: pciehp_resume ENTRY
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476101] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476128] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476143] usb usb2: root hub lost power or was reset
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476178] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476179] usb usb3: root hub lost power or was reset
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476210] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476221] usb usb4: root hub lost power or was reset
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476252] usb usb5: root hub lost power or was reset
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476271] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476323] usb usb1: root hub lost power or was reset
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476424] pcieport 0000:00:1c.0: wake-up capability disabled by ACPI
Nov  1 19:43:35 jon-laptop kernel: [ 1226.476457] r8180 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov  1 19:43:35 jon-laptop kernel: [ 1226.477067] sd 0:0:0:0: [sda] Starting disk
Nov  1 19:43:35 jon-laptop kernel: [ 1226.573305] PM: resume of drv:i915 dev:0000:00:02.0 complete after 101.717 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617173] PM: resume of drv:usb dev:usb2 complete after 140.652 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617216] PM: resume of drv:hub dev:2-0:1.0 complete after 140.684 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617239] PM: resume of drv:usb dev:usb3 complete after 140.703 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617285] PM: resume of drv:hub dev:3-0:1.0 complete after 140.739 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617302] PM: resume of drv:usb dev:usb5 complete after 140.735 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.617349] PM: resume of drv:hub dev:5-0:1.0 complete after 140.695 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.713143] PM: resume of drv:usb dev:usb1 complete after 236.657 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.713186] PM: resume of drv:hub dev:1-0:1.0 complete after 236.673 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.721178] PM: resume of drv:usb dev:usb4 complete after 244.624 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.721219] PM: resume of drv:hub dev:4-0:1.0 complete after 244.658 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.793163] ata3: SATA link down (SStatus 0 SControl 300)
Nov  1 19:43:35 jon-laptop kernel: [ 1226.825146] usb 1-6: reset high speed USB device using ehci_hcd and address 3
Nov  1 19:43:35 jon-laptop kernel: [ 1226.865272] PM: resume of drv:battery dev:PNP0C0A:00 complete after 372.019 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965302] PM: resume of drv:usb dev:1-6 complete after 488.445 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965345] PM: resume of drv:usb-storage dev:1-6:1.0 complete after 488.445 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965388] PM: resume of drv:scsi dev:host4 complete after 488.443 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965426] PM: resume of drv:scsi_host dev:host4 complete after 488.433 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965445] PM: resume of drv:scsi dev:target4:0:0 complete after 488.240 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965498] PM: resume of drv:sd dev:4:0:0:0 complete after 488.249 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1226.965537] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 488.242 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1227.069149] usb 1-5: reset high speed USB device using ehci_hcd and address 2
Nov  1 19:43:35 jon-laptop kernel: [ 1227.257056] PM: resume of drv:usb dev:1-5 complete after 780.394 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1227.257106] PM: resume of drv:uvcvideo dev:1-5:1.0 complete after 780.438 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1227.257123] PM: resume of drv:uvcvideo dev:1-5:1.1 complete after 780.329 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1227.257159] PM: resume of drv: dev:ep_83 complete after 332.532 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1228.025151] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov  1 19:43:35 jon-laptop kernel: [ 1228.071124] ata1.00: configured for UDMA/133
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088095] PM: resume of drv:sd dev:0:0:0:0 complete after 1611.022 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088143] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1610.980 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088161] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 830.956 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088354] PM: resume of devices complete after 1617.190 msecs
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088603] PM: resume devices took 1.620 seconds
Nov  1 19:43:35 jon-laptop kernel: [ 1228.088687] Restarting tasks ... done.
Nov  1 19:43:35 jon-laptop kernel: [ 1228.090485] video LNXVIDEO:00: Restoring backlight state
Nov  1 19:43:35 jon-laptop kernel: [ 1228.144715] atkbd serio0: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Nov  1 19:43:35 jon-laptop kernel: [ 1228.144727] atkbd serio0: Use 'setkeycodes e077 <keycode>' to make it known.
Nov  1 19:43:35 jon-laptop kernel: [ 1228.148332] atkbd serio0: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Nov  1 19:43:35 jon-laptop kernel: [ 1228.148344] atkbd serio0: Use 'setkeycodes e077 <keycode>' to make it known.
Nov  1 19:43:35 jon-laptop kernel: [ 1228.204112] Skipping EDID probe due to cached edid
Nov  1 19:43:35 jon-laptop kernel: [ 1228.245858] pciehp 0000:00:1c.0:pcie04: Card present on Slot(0)
Nov  1 19:43:35 jon-laptop kernel: [ 1228.614519] r8169 0000:01:00.0: eth0: link down
Nov  1 19:43:35 jon-laptop kernel: [ 1228.615715] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  1 19:43:35 jon-laptop kernel: [ 1228.618609] r8180: Bringing up iface
Nov  1 19:43:36 jon-laptop kernel: [ 1228.817179] r8180: Card successfully reset
Nov  1 19:43:36 jon-laptop kernel: [ 1229.557953] r8180: WIRELESS_MODE_G
Nov  1 19:43:36 jon-laptop kernel: [ 1229.557961] 
Nov  1 19:43:36 jon-laptop kernel: [ 1229.586136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  1 19:43:36 jon-laptop kernel: [ 1229.714116] pciehp 0000:00:1c.1:pcie04: Card present on Slot(0-1)
Nov  1 19:44:44 jon-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov  1 19:44:44 jon-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="802" x-info="http://www.rsyslog.com"] (re)start
Nov  1 19:44:44 jon-laptop rsyslogd: rsyslogd's groupid changed to 103
Nov  1 19:44:44 jon-laptop rsyslogd: rsyslogd's userid changed to 101
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f5b2000 (usable)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f5b2000 - 000000003f5d5000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f5d5000 - 000000003f5e6000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f5e6000 - 000000003f5e9000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f5e9000 - 000000003f605000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f605000 - 000000003f606000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f606000 - 000000003f608000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f608000 - 000000003f611000 (ACPI data)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f611000 - 000000003f617000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 000000003f617000 - 000000003f700000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] DMI 2.4 present.
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] last_pfn = 0x3f5b2 max_arch_pfn = 0x100000
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] modified physical RAM map:
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003f5b2000 (usable)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f5b2000 - 000000003f5d5000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f5d5000 - 000000003f5e6000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f5e6000 - 000000003f5e9000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f5e9000 - 000000003f605000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f605000 - 000000003f606000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f606000 - 000000003f608000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f608000 - 000000003f611000 (ACPI data)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f611000 - 000000003f617000 (ACPI NVS)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 000000003f617000 - 000000003f700000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Nov  1 19:44:44 jon-laptop kernel: [    0.000000] RAMDISK: 2ee40000 - 2f885000
```

Any ideas?

---

### Post by Hippytaff on 2010-11-01
Read up on this first, but my inital thoughts are that it doesn't like the bios firmware. But it is an amaturish guess - might want to have a play around with the power management settings, or try an older kernel if you already have one there to select at bootup.
 
Also what does your swap partition look like? I think this might play a part in hibernation and suspend issues

---

### Post by thongstele on 2010-11-10
**What happens in Suspend mode of Ubuntu 10.10?**

In my laptop (Sony Vaio FW) with Ubuntu 10.4, Suspend mode (click on menu or laptop close lid): the power light: turn from green to yellow, HDD light is off...After that, i press any key, a login window appears and I log on the Ubuntu with existing programs as before.
It's ok with me.

But with the same laptop after clean ubuntu 10.10: everythings is the same as above case except for I press anykey to return Ubuntu, IT RESTART (NOT RESUME, OF COURSE EXISTING PROGRAMS DISAPPEAR). **[COLOR=Blue]_I think it has a issue with Suspend mode in Ubuntu 10.10._[/COLOR]** 

Anyone has the same situation with me and how to solve? 

My hardware of laptop: Vaio FW190E
CPU: P8400 2,26G (Core2 Duo)
Ram: 4G
Ubuntu 10.10 32bit.

---

### Post by dalonso on 2010-12-06
Exactly same problem here (Vaio VGN-FZ21S). It was working when I first installed Maverick 10.10. 

Now after some update it stopped working.

I've tried everything I have found without success. I even tried to follow the suspend debugging guide in the wiki ([https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume")) and it didn't worked at all.

I haven't found any bug report about this.

Have you fixed your problem somehow?

---

### Post by avenca on 2010-12-10
I have exactly the same problem. Everything works fine until I upgraded to Ubuntu 10.10. 

I have tried to install the hibernate package and to change the acpi configuration - as suggested in other posts -, but nothing works.

This problem is really annoying... I see lots of posts about this issue what should be solved.

Linux version 2.6.35-23-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Lin
aro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010

---

### Post by ariwe on 2010-12-15
Hi, same problem with a Vaio FW-140E, 2.6.35-23-generic. 
Appending acpi_sleep=nonvs to my first menuentry in /boot/grub/grub.cfg worked.

See 
  - bug: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/654870](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/654870)
  - solution: [http://ubuntuforums.org/showpost.php?p=9934814&postcount=42](http://ubuntuforums.org/showpost.php?p=9934814&postcount=42)

---

