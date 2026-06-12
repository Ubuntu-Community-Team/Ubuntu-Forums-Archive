---
title: "Slow nForce 590 (MCP55) Ethernet  Speeds on Ubuntu 7.10 and 8.04(Alpha5)"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by svet-am on 2008-03-03
I experienced this same behavior/problem on Fedora Core 8 (x86_64), but I just verified that it also exists using LiveCD editions of Ubuntu 7.10 and 8.04(alpha5).

Here's my rig:
```

AMD Athlon FX-62 @ Stock (cooled by Zalman 9700)
Gigabyte GAM59SLI-S5(rev 1) 590SLI
4x1GB Mushkin DDR2
eVGA 8800GTX SuperClocked
WD WD500YS
WD WD800JD
Audigy 2 ZS with LiveDrive
Plextor PX-712A DVD-RW
Sony DDU1615 DVD-ROM

```

I'm running Ubuntu 7.10/8.04. The architecture I'm using is the x64 variant.

The networking is being controlled by forcedeth. I don't have the logs handy (I'm at work), but I ethtool reports that the networking is using mii as the port type, that my network card supports 100Mbps connects, that it is using auto-negotiate for duplex and speed, and that it is currently up and configured as a 100Mbps connection with full-duplex.

I can get an IP, browse the Internet, and browse my network just fine. The issue is not about connectivity, just speed and throughput.

My issue is that the networking is painfully slow. I've done some testing by copying files around and in all of my tests I'm seeing ~3.0-3.5MB/sec transfer rates with this machine.

The machine is a dual-boot with Windows XP x32 and when I reboot into XP, I can perform the exact same file copy test at ~6.5-7.5MB/sec.

I've done lots of googling and not found anyone else reporting on this issue. I've seen a couple comments about disabling segment offloading using "ethtool -K eth0 tso off" (yes, my NIC is eth0) and that makes no difference.

Anyone got any clues/ideas on what is going wrong and what I can do to fix this?

For reference, my network is set up like this when I perform the copy test:
```

My_PC -----> 100Mbps Switch <------ File Server

```

Yes, the file server (a repurposed Via Epia) is reporting a 100Mbps link. It is running Trustix Secure Linux, so Windows doesn't enter into the equation when testing my Ubuntu data rates.

Any advice or guidance would be appreciated.  I'm not a Linux n00b by any stretch, but this has me stumped.

---

### Post by svet-am on 2008-03-04
I found a BIOS update (F8) for the motherboard.  It is the latest BIOS update available.  No change in Linux performance.

---

