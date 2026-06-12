---
title: "Screen-sort-of-freezes crash"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by ethidda on 2009-04-26
**Problem:** Screen freezes except for cursor, which still moves when I move the mouse. No response to the keyboard at all (pressing caps lock doesn't turn on the caps light either). I have to do a force shutdown and reboot.

**Ubuntu version:** Xubuntu 9.04

**A little background:** I was running Intrepid just fine, but was smart and decided to upgrade to jaunty. That's when this problem started (it would do this anywhere from 30 minutes to 2 days after boot up). I thought it might have been due to some conflict in the upgrade so I wiped the system partition (but kept my */home* partition) and did a fresh install, to no avail.

**Programs I usually have running:** Irssi (commandline irc client), deluge, skype, firefox, amarok14. I also use wine, and the native pdf reader.

It's really frustrating, considering I switched from windows to linux to avoid explained crashes like this. If anybody has experienced a similar problem, or knows how to fix it (or a site that says how to fix it), I will be much obliged.

TIA
ethidda

---

### Post by cariboo on 2009-04-26
Is there anything in /var/log/messages that may indicate what it is that is crashing? If you had the same sort of problem in Windows. I would suggest you may have a hardware problem.

---

### Post by ethidda on 2009-04-26
> **cariboo907 said:**
> Is there anything in /var/log/messages that may indicate what it is that is crashing? If you had the same sort of problem in Windows. I would suggest you may have a hardware problem.

I considered it being a hardware problem. However, the computer NEVER crashed under Intrepid, and only started experiencing problems after I tried Windows 7 Beta. I even did a memory scan and a harddisk check, which both indicated no problems.

Is there something in particular I should be looking for in the /var/log/messages? Mostly, it's confusing me. I did a "tail -n 100 /var/log/messages" and this is what I got: (Notice how the timestamps make no sense. It is currently April 26, 22:34 where I am.)

```
Apr 27 00:24:32 Tyche kernel: [    7.697563] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 27 00:24:32 Tyche kernel: [    7.697565] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 00:24:32 Tyche kernel: [    7.697567] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 27 00:24:32 Tyche kernel: [    7.697569] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 27 00:24:32 Tyche kernel: [    7.697570] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 00:24:32 Tyche kernel: [    7.697572] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 00:24:32 Tyche kernel: [    7.711871] yenta_cardbus 0000:05:00.0: CardBus bridge found [17aa:20c6]
Apr 27 00:24:32 Tyche kernel: [    7.731929] iTCO_vendor_support: vendor-support=0
Apr 27 00:24:32 Tyche kernel: [    7.733457] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Apr 27 00:24:32 Tyche kernel: [    7.733539] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
Apr 27 00:24:32 Tyche kernel: [    7.733598] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 27 00:24:32 Tyche kernel: [    7.749405] Linux agpgart interface v0.103
Apr 27 00:24:32 Tyche kernel: [    7.769798] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr 27 00:24:32 Tyche kernel: [    7.770582] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr 27 00:24:32 Tyche kernel: [    7.773460] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Apr 27 00:24:32 Tyche kernel: [    7.792892] Non-volatile memory driver v1.2
Apr 27 00:24:32 Tyche kernel: [    7.804753] acpi device:03: registered as cooling_device2
Apr 27 00:24:32 Tyche kernel: [    7.804954] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input5
Apr 27 00:24:32 Tyche kernel: [    7.808151] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 27 00:24:32 Tyche kernel: [    7.823099] sdhci: Secure Digital Host Controller Interface driver
Apr 27 00:24:32 Tyche kernel: [    7.823101] sdhci: Copyright(c) Pierre Ossman
Apr 27 00:24:32 Tyche kernel: [    7.841275] yenta_cardbus 0000:05:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
Apr 27 00:24:32 Tyche kernel: [    7.841281] yenta_cardbus 0000:05:00.0: Socket status: 30000006
Apr 27 00:24:32 Tyche kernel: [    7.841285] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
Apr 27 00:24:32 Tyche kernel: [    7.841288] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x7fff: clean.
Apr 27 00:24:32 Tyche kernel: [    7.841980] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd7efffff
Apr 27 00:24:32 Tyche kernel: [    7.841982] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff
Apr 27 00:24:32 Tyche kernel: [    8.141814] input: PC Speaker as /devices/platform/pcspkr/input/input6
Apr 27 00:24:32 Tyche kernel: [    8.204274] sdhci-pci 0000:05:00.2: SDHCI controller found [1180:0822] (rev 21)
Apr 27 00:24:32 Tyche kernel: [    8.204306] sdhci-pci 0000:05:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 27 00:24:32 Tyche kernel: [    8.205341] sdhci-pci 0000:05:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 27 00:24:32 Tyche kernel: [    8.207502] mmc0: SDHCI controller on PCI [0000:05:00.2] using DMA
Apr 27 00:24:32 Tyche kernel: [    8.282861] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Apr 27 00:24:32 Tyche kernel: [    8.282864] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Apr 27 00:24:32 Tyche kernel: [    8.282999] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 27 00:24:32 Tyche kernel: [    8.283099] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
Apr 27 00:24:32 Tyche kernel: [    8.324263] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr 27 00:24:32 Tyche kernel: [    8.358723] thinkpad_acpi: ThinkPad ACPI Extras v0.21
Apr 27 00:24:32 Tyche kernel: [    8.358725] thinkpad_acpi: http://ibm-acpi.sf.net/
Apr 27 00:24:32 Tyche kernel: [    8.358727] thinkpad_acpi: ThinkPad BIOS 7NETB9WW (2.19 ), EC 7MHT25WW-1.03
Apr 27 00:24:32 Tyche kernel: [    8.358728] thinkpad_acpi: Lenovo ThinkPad X61, model 7675CTO
Apr 27 00:24:32 Tyche kernel: [    8.359346] thinkpad_acpi: radio switch found; radios are enabled
Apr 27 00:24:32 Tyche kernel: [    8.359438] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
Apr 27 00:24:32 Tyche kernel: [    8.359441] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
Apr 27 00:24:32 Tyche kernel: [    8.370053] Registered led device: tpacpi::thinklight
Apr 27 00:24:32 Tyche kernel: [    8.370089] Registered led device: tpacpi::power
Apr 27 00:24:32 Tyche kernel: [    8.370101] Registered led device: tpacpi:orange:batt
Apr 27 00:24:32 Tyche kernel: [    8.370113] Registered led device: tpacpi:green:batt
Apr 27 00:24:32 Tyche kernel: [    8.370124] Registered led device: tpacpi::dock_active
Apr 27 00:24:32 Tyche kernel: [    8.370138] Registered led device: tpacpi::bay_active
Apr 27 00:24:32 Tyche kernel: [    8.370150] Registered led device: tpacpi::dock_batt
Apr 27 00:24:32 Tyche kernel: [    8.370162] Registered led device: tpacpi::unknown_led
Apr 27 00:24:32 Tyche kernel: [    8.370173] Registered led device: tpacpi::standby
Apr 27 00:24:32 Tyche kernel: [    8.373427] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
Apr 27 00:24:32 Tyche kernel: [    8.373705] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
Apr 27 00:24:32 Tyche kernel: [    8.466730] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 27 00:24:32 Tyche kernel: [    8.466734] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
Apr 27 00:24:32 Tyche kernel: [    8.487132] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Apr 27 00:24:32 Tyche kernel: [    8.570638] usbcore: registered new interface driver snd-usb-audio
Apr 27 00:24:32 Tyche kernel: [    8.654489] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Apr 27 00:24:32 Tyche kernel: [    8.656467] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Apr 27 00:24:32 Tyche kernel: [    8.657284] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Apr 27 00:24:32 Tyche kernel: [    8.658051] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Apr 27 00:24:32 Tyche kernel: [    8.658951] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Apr 27 00:24:32 Tyche kernel: [    9.070357] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Apr 27 00:24:32 Tyche kernel: [    9.096163] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
Apr 27 00:24:32 Tyche kernel: [    9.147152] Adding 3991640k swap on /dev/sda5.  Priority:-1 extents:1 across:3991640k
Apr 27 00:24:32 Tyche kernel: [    9.677046] EXT3 FS on sda6, internal journal
Apr 27 00:24:32 Tyche kernel: [   12.883373] kjournald starting.  Commit interval 5 seconds
Apr 27 00:24:32 Tyche kernel: [   12.883770] EXT3 FS on sda7, internal journal
Apr 27 00:24:32 Tyche kernel: [   12.883773] EXT3-fs: mounted filesystem with ordered data mode.
Apr 27 00:24:32 Tyche kernel: [   13.031395] type=1505 audit(1240784672.037:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2466
Apr 27 00:24:32 Tyche kernel: [   13.031466] type=1505 audit(1240784672.037:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2466
Apr 27 00:24:32 Tyche kernel: [   13.031501] type=1505 audit(1240784672.037:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2466
Apr 27 00:24:32 Tyche kernel: [   13.031530] type=1505 audit(1240784672.037:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2466
Apr 27 00:24:32 Tyche kernel: [   13.124528] type=1505 audit(1240784672.132:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2471
Apr 27 00:24:32 Tyche kernel: [   13.124677] type=1505 audit(1240784672.132:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2471
Apr 27 00:24:32 Tyche kernel: [   13.145170] type=1505 audit(1240784672.153:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2475
Apr 27 00:24:34 Tyche kernel: [   15.003088] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 27 00:24:34 Tyche kernel: [   15.003090] Bluetooth: BNEP filters: protocol multicast
Apr 27 00:24:34 Tyche kernel: [   15.010019] Bridge firewalling registered
Apr 27 00:24:35 Tyche kernel: [   16.078311] ppdev: user-space parallel port driver
Apr 27 00:24:35 Tyche kernel: [   16.676280] [drm] Initialized drm 1.1.0 20060810
Apr 27 00:24:35 Tyche kernel: [   16.680829] pci 0000:00:02.0: power state changed by ACPI to D0
Apr 27 00:24:35 Tyche kernel: [   16.680837] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 00:24:35 Tyche kernel: [   16.681027] [drm] Initialized i915 1.6.0 20080730 on minor 0
Apr 27 00:24:39 Tyche kernel: [   20.184530] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 27 00:24:39 Tyche kernel: [   20.185487] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
Apr 27 00:24:39 Tyche kernel: [   20.436587] Registered led device: iwl-phy0:radio
Apr 27 00:24:39 Tyche kernel: [   20.436743] Registered led device: iwl-phy0:assoc
Apr 27 00:24:39 Tyche kernel: [   20.437849] Registered led device: iwl-phy0:RX
Apr 27 00:24:39 Tyche kernel: [   20.438459] Registered led device: iwl-phy0:TX
Apr 27 00:24:39 Tyche kernel: [   20.463056] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 00:25:10 Tyche kernel: [   51.597587] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 26 22:25:17 Tyche kernel: [   57.325203] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
Apr 26 22:25:19 Tyche pulseaudio[4136]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Apr 26 22:25:19 Tyche pulseaudio[4136]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Apr 26 22:25:19 Tyche pulseaudio[4136]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Apr 26 22:25:20 Tyche pulseaudio[4139]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Apr 26 22:25:20 Tyche pulseaudio[4139]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

```

---

### Post by dirk_k on 2009-04-27
I had a similair program with a very small and simple program: alarm-clock. This is a small python program that was running in my systray and started by default. But a bug in the pygtk library causes the screen to freeze. See also:
[https://bugs.launchpad.net/ubuntu/+source/pygtk/+bug/321176](https://bugs.launchpad.net/ubuntu/+source/pygtk/+bug/321176)
Maybe one of your programs uses the same library?
Are you still able to go back to a terminal with ctrl-alt-F1? I could. If so, try killing individual programs/applets that started after you logged in. After each kill, go back with ctrl-alt-F7 and check if the desktop is responsive again.

---

