---
title: "Hotplug doesn't work"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by disappearedng on 2010-07-21
I plugged in my canon camera which would normally be automounted correctly. It now doesn't mount.

this is my dmesg:
```

[   11.347749] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   11.376037] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   11.400936] [drm] nouveau 0000:01:00.0: allocated 1440x900 fb: 0x40250000, bo ffff88011b4a2400
[   11.401043] fb0: nouveaufb frame buffer device
[   11.401044] registered panic notifier
[   11.401049] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   11.402319] vga16fb: initializing
[   11.402321] vga16fb: mapped to 0xffff8800000a0000
[   11.402323] vga16fb: not registering due to another framebuffer present
[   11.414895] [drm] nouveau 0000:01:00.0: 0x0FB1: parsing clock script 0
[   11.414959] Console: switching to colour frame buffer device 180x56
[   11.451684] r8169: eth0: link up
[   11.451690] r8169: eth0: link up
[   11.534458] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   12.473906] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   12.477352] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[   13.189361] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 1
[   13.189364] [drm:edid_is_valid] *ERROR* Raw EDID:
[   13.189367] <3>00 ff ff ff ff ff ff 00 4a 8b 52 ad 01 01 01 01  ........J.R.....
[   13.189369] <3>18 0f 01 03 68 29 1a 78 2e 4f a5 a4 59 49 99 24  ....h).x.O..YI.$
[   13.189371] <3>12 50 54 bf ef 00 81 80 81 40 71 4f 95 00 01 01  .PT......@qO....
[   13.189372] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   13.189374] <3>36 00 98 ff 10 00 00 1c 00 00 00 fd 00 38 4c 1e  6............8L.
[   13.189375] <3>52 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  R...      .....A
[   13.189377] <3>63 65 72 21 41 4c 31 39 31 36 57 0a 00 00 00 ff  cer!AL1916W.....
[   13.189378] <3>00 30 0a 20 20 20 20 20 20 20 20 20 20 20 00 45  .0.           .E
[   13.189379] 
[   14.593492] CPU0 attaching NULL sched-domain.
[   14.593497] CPU1 attaching NULL sched-domain.
[   14.640110] CPU0 attaching sched-domain:
[   14.640113]  domain 0: span 0-1 level MC
[   14.640115]   groups: 0 1
[   14.640120] CPU1 attaching sched-domain:
[   14.640121]  domain 0: span 0-1 level MC
[   14.640123]   groups: 1 0
[   15.145887] ppdev: user-space parallel port driver
[   21.571256] eth0: no IPv6 routers present
[   22.136995] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 2
[   22.136998] [drm:edid_is_valid] *ERROR* Raw EDID:
[   22.137001] <3>00 ff ff ff ff ff ff 00 4a 8b 52 ad 01 01 01 01  ........J.R.....
[   22.137002] <3>18 0f 01 03 68 29 1a 78 2e 4f a5 a4 59 49 99 24  ....h).x.O..YI.$
[   22.137004] <3>12 50 54 bf ef 00 81 80 81 40 71 4f 95 00 01 01  .PT......@qO....
[   22.137006] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   22.137007] <3>36 00 98 ff 10 00 00 1c 00 00 00 fd 00 38 4c 1e  6............8L.
[   22.137009] <3>52 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  R...      .....A
[   22.137010] <3>63 65 72 20 41 4c 33 39 31 36 57 0a 00 00 00 ff  cer AL3916W.....
[   22.137012] <3>00 30 0a 20 20 20 20 20 20 20 20 20 20 20 00 45  .0.           .E
[   22.137013] 
[   22.753679] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 4
[   22.753683] [drm:edid_is_valid] *ERROR* Raw EDID:
[   22.753685] <3>00 ff ff ff ff ff ff 00 4a 8b 52 ad 01 01 01 01  ........J.R.....
[   22.753687] <3>18 0f 05 03 68 29 1a 78 2e 4f a5 a4 59 49 99 24  ....h).x.O..YI.$
[   22.753688] <3>12 50 54 bf ef 00 81 80 81 40 71 4f 95 00 01 01  .PT......@qO....
[   22.753690] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   22.753691] <3>36 00 98 ff 10 00 00 1c 00 00 00 fd 00 38 4c 1e  6............8L.
[   22.753693] <3>52 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  R...      .....A
[   22.753694] <3>63 65 72 20 41 4c 31 39 31 36 57 0a 00 00 00 ff  cer AL1916W.....
[   22.753696] <3>00 30 0a 20 20 20 20 20 20 20 20 20 20 20 00 45  .0.           .E
[   22.753697] 
[   31.089693] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 8
[   31.089696] [drm:edid_is_valid] *ERROR* Raw EDID:
[   31.089699] <3>00 ff ff ff ff ff ff 00 4a 8b 52 ad 01 01 01 01  ........J.R.....
[   31.089701] <3>18 0f 01 03 68 29 1a 78 2e 4f a5 a4 59 49 99 24  ....h).x.O..YI.$
[   31.089703] <3>12 50 54 bf ef 00 81 80 81 40 71 4f 95 00 01 01  .PT......@qO....
[   31.089704] <3>01 01 01 01 01 01 9a 29 a0 d0 51 84 22 30 50 98  .......)..Q."0P.
[   31.089706] <3>36 00 98 ff 10 00 00 1c 00 00 00 fd 00 38 4c 1e  6............8L.
[   31.089707] <3>52 0e 00 0a 20 20 20 20 20 20 00 00 00 fc 00 41  R...      .....A
[   31.089709] <3>63 65 72 20 41 4c 31 39 31 36 57 0a 00 00 00 ff  cer AL1916W.....
[   31.089710] <3>00 30 0a 28 20 20 20 20 20 20 20 20 20 20 00 45  .0.(          .E
[   31.089711] 
[   78.190017] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   78.366290] usb 2-3: configuration #1 chosen from 1 choice
[  149.927253] tun0: Disabled Privacy Extensions

```

lsusb shows that it's mounted:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04a9:3110 Canon, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have *just* restarted my computer. Anyone here knows why?

---

