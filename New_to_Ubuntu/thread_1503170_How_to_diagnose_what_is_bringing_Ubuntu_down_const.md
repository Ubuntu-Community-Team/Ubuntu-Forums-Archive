---
title: "How to diagnose what is bringing Ubuntu down constantly"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Keith Myers on 2010-06-06
I am a new user so don't know how to interpret any of the message logs.  I have been a OS/2 user for over 10 years and is my primary OS on this computer.  It does not have any issues with the hardware with this computer and stay up forever until I decide to reboot.  I run the computer 24/7 processing WU's for Seti@Home.  I do not think there is any hardware issues, such as memory since I figure OS/2 and Seti@Home gives it a constant workout.  I have read all the message topics dealing with system crashes and mainly they seem to concentrate on what application is bringing down the system.  In my case, no application is in use other than the BOINC and SETI clients.  I haven't had the system crash on me when directly using it such as browsing or email.  I did have one crash within about 5 minutes after booting while I had a terminal open.  Mostly, I have stepped away from the computer and come back in a few hours to find the screen black with only the NUM LOCK and CAPS LOCK LED's flashing on the keyboard.  The only way to get the system back is to use the computer reset button.  I have just learned about the proper way of recovering a system from another post and I attempted to use all of the measures to no avail. I tried the CTRL+ALT+BACKSPACE keystrokes.  Nothing happens.  I tried next the ALT+SysRq+K keystrokes.  Nothing happens.  I tried next the ALT+SysRq REISUB keystrokes and nothing happened.  I pushed the reset button and rebooted the computer.  I signed up for the bug reporting service.  I set APPORT=1 active supposedly.  I am stuck with what is the proper response in the ubuntu-bug command in the terminal.  I don't fit any of the categories.  I don't know what is killing the system. I have made one report so far when I stumbled onto a message thread that showed me some commands.  It gathered up a bunch of data and sent it off but I can't find the message thread again and I don't remember what it was I put into the terminal to make it happen.  Can anyone help me out?  I would like to continue to use Ubuntu since it has considerably more multimedia capabilities over eComStation, the OS/2 variant I normally run.  If I can't get the system stable, I will have to give up on this experiment and stay over in eComStation primarily.  Thanks in advance.

Cheers,  Keith
:confused:

---

### Post by mapes12 on 2010-06-06
Hi

Could we have a look at your hardware please. Applications>Accessories>Terminal ```
sudo lshw
``` then your partitions ```
sudo fdisk -l
``` and post the output back here.

---

### Post by Keith Myers on 2010-06-06
Hi and thanks for the help.  Well, I will have to modify what I stated in my post.  I was just submitting a but report #590474 and was reading through the various text files it submitted and the darn system crashes on me again.  This was within 5 minutes of the last reboot.  Hope I can get through this email reply before it happens again.  I submitted bug report #590477 in response to #590474 in LaunchPad.  Anyway here is the info you requested:

```

```
keith@keith-desktop:~$ sudo lshw
[sudo] password for keith: 
keith-desktop             
    description: Desktop Computer
    product: MS-6712
    vendor: MSI
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS-6712
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: Version 07.00T (04/02/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket-A
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 169MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 1015MiB
     *-pci
          description: Host bridge
          product: VT8366/A/7 [Apollo KT266/A/333]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via
          resources: irq:0 memory:e0000000-e7ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8366/A/7 [Apollo KT266/A/333 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:b000(size=4096) memory:dfe00000-dfefffff memory:bfd00000-dfcfffff(prefetchable)
           *-display:0
                description: VGA compatible controller
                product: R480 [Radeon X850Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:16 memory:d0000000-d7ffffff(prefetchable) ioport:b800(size=256) memory:dfef0000-dfefffff memory:dfec0000-dfedffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: R480 [Radeon X850Pro] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:c8000000-cfffffff(prefetchable) memory:dfee0000-dfeeffff
        *-scsi:0
             description: SCSI storage controller
             product: 53c1010 Ultra3 SCSI Adapter
             vendor: LSI Logic / Symbios Logic
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: scsi2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm bus_master cap_list rom scsi-host
             configuration: driver=sym53c8xx latency=72 maxlatency=18 mingnt=17
             resources: irq:17 ioport:e400(size=256) memory:dffff800-dffffbff memory:dfffa000-dfffbfff memory:dffa0000-dffbffff(prefetchable)
           *-tape
                description: SCSI Tape
                product: Python 06408-XXX
                vendor: ARCHIVE
                physical id: 0.5.0
                bus info: scsi@2:0.5.0
                logical name: /dev/nst0
                logical name: /dev/st0
                version: 9050
                serial: HN01JEH
                capabilities: removable
                configuration: ansiversion=3
           *-disk
                description: SCSI Disk
                product: ATLAS10K3_18_WLS
                vendor: QUANTUM
                physical id: 0.6.0
                bus info: scsi@2:0.6.0
                logical name: /dev/sda
                version: 020W
                serial: 342250143173
                size: 17GiB (18GB)
                capacity: 17GiB (18GB)
                capabilities: 10000rpm partitioned partitioned:dos
                configuration: ansiversion=3 signature=000ea193
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.6.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0a5490cb-2f11-4620-968b-8667422558e0
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-01 20:45:59 filesystem=ext4 lastmountpoint=/P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1048897;&#65533;p&#65533;&#65533;&#65533;u^ &#65533;U/&#65533;d&#65533;&#65533;&#65533;~!&#65533;&#65533;[&#65533;&#65533;[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a modified=2010-06-06 11:38:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-06 11:38:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.6.0,2
                   logical name: /dev/sda2
                   size: 776MiB
                   capacity: 776MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 776MiB
                      capabilities: nofs
        *-scsi:1 UNCLAIMED
             description: SCSI storage controller
             product: 53c1010 Ultra3 SCSI Adapter
             vendor: LSI Logic / Symbios Logic
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm cap_list
             configuration: latency=72 maxlatency=18 mingnt=17
             resources: ioport:e800(size=256) memory:dffffc00-dfffffff memory:dfffc000-dfffdfff memory:40000000-4001ffff(prefetchable)
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
             resources: irq:18 ioport:e000(size=32)
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=64
             resources: irq:0 ioport:ec00(size=8)
        *-network
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 00
             serial: 00:60:97:37:b1:df
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.101 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:dc00(size=64) memory:dffe0000-dffeffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:dffff700-dffff7ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-disk
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sdb
                version: A1Y.
                serial: 793127806262
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000035c4
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 8032MiB
                   capabilities: primary bootable
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22LP20
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
keith@keith-desktop:~$ 
```

```

```

```
keith@keith-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000035c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1024     8225248+   7  HPFS/NTFS

Disk /dev/sda: 18.4 GB, 18389272576 bytes
255 heads, 63 sectors/track, 2235 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea193

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2137    17161216   83  Linux
/dev/sda2            2137        2236      794625    5  Extended
/dev/sda5            2137        2236      794624   82  Linux swap / Solaris
keith@keith-desktop:~$ 
```

```

Hope this helps you help me figure this out.

Cheers,  Keith
:confused:

---

### Post by clhsharky on 2010-06-06
HI Keith Myers

What release are you using?

What are the logs reporting? 
Look in (System >Administration >Log file viewer >Messages)


Sharky

[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by Keith Myers on 2010-06-06
I am using Ubuntu 10.04 LTS.  If I knew what I was looking at, I wouldn't have need to ask the original posting. I have looked at all the various logs in the Log Viewer, but have no clue what any of it means.

Cheers,  Keith:confused:

---

### Post by clhsharky on 2010-06-06
Keith Myers

KMS(kernel mode setting)in Lucid has caused some lockups on some hardware (AGP chips, acpi).
Karmic might be better choice with older hardware, it has UMS(user mode setting)on by default. UMS is used by all releases but Lucid.

Looking for errors or warnings in logs may lead to a device.
Then maybe a workaround or solution may be found.

Post back the Messages Log would be a start.
Then maybe we can chose what other info would be needed.


Sharky

---

### Post by Keith Myers on 2010-06-07
Hi, I'll post the content of the messages log next.  I'm curious why all the logs seem to have been truncated.  Does the logging system only keep so many days of content available?  When I first looked at the logs, they all went back to 6/1, the day I first got this system installed.  When I looked at them last, they seem to only go back to 6/6.  Not important I guess, just curious.

On the matter of whether I really should be running Lucid Lynx ....  maybe it's a good suggestion to back level to an earlier distribution.  I certainly am not running current hardware..... more like +5 year old hardware.  eComStation has never complained about it since the OS is that old too.

Also I got an automatic reply to all my bug reports saying I should try some of the newer builds??  Is that a good idea?  Since I have no idea what part of my system this LTS is having issues with, I don't have a clue at to what to look for in the fix notes in the newer distributions. I guess it's a matter of try new things out until something seems to fix the problem.  Doesn't sound like logical troubleshooting in my opinion.

Anyway the content of messages.txt:

Jun  7 17:04:10 keith-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun  7 17:04:10 keith-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="590" x-info="http://www.rsyslog.com"] (re)start
Jun  7 17:04:10 keith-desktop rsyslogd: rsyslogd's groupid changed to 103
Jun  7 17:04:11 keith-desktop rsyslogd: rsyslogd's userid changed to 101
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] KERNEL supported cpus:
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Intel GenuineIntel
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   NSC Geode by NSC
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] DMI 2.3 present.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] modified physical RAM map:
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 000000003fff0000 - 000000003fff8000 (ACPI data)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 000000003fff8000 - 0000000040000000 (ACPI NVS)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] RAMDISK: 2f89e000 - 30033ba7
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: RSDP 000fa980 00014 (v00 AMI   )
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: RSDT 3fff0000 0002C (v01 AMIINT VIA_K7   00000010 MSFT 00000097)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: FACP 3fff0030 00081 (v01 AMIINT VIA_K7   00000011 MSFT 00000097)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: DSDT 3fff0120 03362 (v01    VIA   VIA_K7 00001000 MSFT 0100000D)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: FACS 3fff8000 00040
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: APIC 3fff00c0 00054 (v01 AMIINT VIA_K7   00000009 MSFT 00000097)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] 135MB HIGHMEM available.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #4 [002f89e000 - 0030033ba7]          RAMDISK ==> [002f89e000 - 0030033ba7]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #6 [00008da000 - 00008dd108]              BRK ==> [00008da000 - 00008dd108]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] found SMP MP-table at [c00fb930] fb930
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Zone PFN ranges:
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003fff0
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0003fff0
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Using APIC driver default
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u4194304
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=0a5490cb-2f11-4620-968b-8667422558e0 ro quiet splash
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Initializing CPU#0
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] allocated 5242240 bytes of page_cgroup
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003fff0)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Memory: 1017432k/1048512k available (4673k kernel code, 30032k reserved, 2121k data, 656k init, 139208k highmem)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] virtual kernel memory layout:
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] console [tty0] enabled
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jun  7 17:04:11 keith-desktop kernel: [    0.000000] Detected 2190.883 MHz processor.
Jun  7 17:04:11 keith-desktop kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4381.76 BogoMIPS (lpj=8763532)
Jun  7 17:04:11 keith-desktop kernel: [    0.004032] Security Framework initialized
Jun  7 17:04:11 keith-desktop kernel: [    0.004071] AppArmor: AppArmor initialized
Jun  7 17:04:11 keith-desktop kernel: [    0.004080] Mount-cache hash table entries: 512
Jun  7 17:04:11 keith-desktop kernel: [    0.004250] Initializing cgroup subsys ns
Jun  7 17:04:11 keith-desktop kernel: [    0.004256] Initializing cgroup subsys cpuacct
Jun  7 17:04:11 keith-desktop kernel: [    0.004260] Initializing cgroup subsys memory
Jun  7 17:04:11 keith-desktop kernel: [    0.004272] Initializing cgroup subsys devices
Jun  7 17:04:11 keith-desktop kernel: [    0.004275] Initializing cgroup subsys freezer
Jun  7 17:04:11 keith-desktop kernel: [    0.004278] Initializing cgroup subsys net_cls
Jun  7 17:04:11 keith-desktop kernel: [    0.004302] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  7 17:04:11 keith-desktop kernel: [    0.004305] CPU: L2 Cache: 512K (64 bytes/line)
Jun  7 17:04:11 keith-desktop kernel: [    0.004311] mce: CPU supports 4 MCE banks
Jun  7 17:04:11 keith-desktop kernel: [    0.004335] Performance Events: AMD PMU driver.
Jun  7 17:04:11 keith-desktop kernel: [    0.004342] ... version:                0
Jun  7 17:04:11 keith-desktop kernel: [    0.004344] ... bit width:              48
Jun  7 17:04:11 keith-desktop kernel: [    0.004346] ... generic registers:      4
Jun  7 17:04:11 keith-desktop kernel: [    0.004348] ... value mask:             0000ffffffffffff
Jun  7 17:04:11 keith-desktop kernel: [    0.004351] ... max period:             00007fffffffffff
Jun  7 17:04:11 keith-desktop kernel: [    0.004353] ... fixed-purpose events:   0
Jun  7 17:04:11 keith-desktop kernel: [    0.004355] ... event mask:             000000000000000f
Jun  7 17:04:11 keith-desktop kernel: [    0.004360] Checking 'hlt' instruction... OK.
Jun  7 17:04:11 keith-desktop kernel: [    0.020572] SMP alternatives: switching to UP code
Jun  7 17:04:11 keith-desktop kernel: [    0.026292] Freeing SMP alternatives: 19k freed
Jun  7 17:04:11 keith-desktop kernel: [    0.026323] ACPI: Core revision 20090903
Jun  7 17:04:11 keith-desktop kernel: [    0.032017] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun  7 17:04:11 keith-desktop kernel: [    0.032027] ftrace: allocating 21771 entries in 43 pages
Jun  7 17:04:11 keith-desktop kernel: [    0.036141] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun  7 17:04:11 keith-desktop kernel: [    0.037182] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  7 17:04:11 keith-desktop kernel: [    0.079072] CPU0: AMD Athlon(tm) XP 3000+ stepping 00
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] Brought up 1 CPUs
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] Total of 1 processors activated (4381.76 BogoMIPS).
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] devtmpfs: initialized
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] regulator: core version 0.5
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] Time: 17:03:57  Date: 06/07/10
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] NET: Registered protocol family 16
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] EISA bus registered
Jun  7 17:04:11 keith-desktop kernel: [    0.080001] ACPI: bus type pci registered
Jun  7 17:04:11 keith-desktop kernel: [    0.081252] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
Jun  7 17:04:11 keith-desktop kernel: [    0.081255] PCI: Using configuration type 1 for base access
Jun  7 17:04:11 keith-desktop kernel: [    0.082249] bio: create slab <bio-0> at 0
Jun  7 17:04:11 keith-desktop kernel: [    0.087626] ACPI: Interpreter enabled
Jun  7 17:04:11 keith-desktop kernel: [    0.087632] ACPI: (supports S0 S1 S4 S5)
Jun  7 17:04:11 keith-desktop kernel: [    0.087653] ACPI: Using IOAPIC for interrupt routing
Jun  7 17:04:11 keith-desktop kernel: [    0.091135] ACPI: Power Resource [URP1] (off)
Jun  7 17:04:11 keith-desktop kernel: [    0.091165] ACPI: Power Resource [URP2] (off)
Jun  7 17:04:11 keith-desktop kernel: [    0.091193] ACPI: Power Resource [FDDP] (off)
Jun  7 17:04:11 keith-desktop kernel: [    0.091222] ACPI: Power Resource [LPTP] (off)
Jun  7 17:04:11 keith-desktop kernel: [    0.091337] ACPI: No dock devices found.
Jun  7 17:04:11 keith-desktop kernel: [    0.091457] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  7 17:04:11 keith-desktop kernel: [    0.091967] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun  7 17:04:11 keith-desktop kernel: [    0.091971] pci 0000:00:10.0: PME# disabled
Jun  7 17:04:11 keith-desktop kernel: [    0.092043] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Jun  7 17:04:11 keith-desktop kernel: [    0.092047] pci 0000:00:10.3: PME# disabled
Jun  7 17:04:11 keith-desktop kernel: [    0.092100] HPET not enabled in BIOS. You might try hpet=force boot option
Jun  7 17:04:11 keith-desktop kernel: [    0.092106] pci 0000:00:11.0: quirk: region 0800-087f claimed by vt8235 PM
Jun  7 17:04:11 keith-desktop kernel: [    0.092110] pci 0000:00:11.0: quirk: region 0400-040f claimed by vt8235 SMB
Jun  7 17:04:11 keith-desktop kernel: [    0.094125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun  7 17:04:11 keith-desktop kernel: [    0.094220] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 *12 14 15)
Jun  7 17:04:11 keith-desktop kernel: [    0.094314] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jun  7 17:04:11 keith-desktop kernel: [    0.094406] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun  7 17:04:11 keith-desktop kernel: [    0.094515] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun  7 17:04:11 keith-desktop kernel: [    0.094519] vgaarb: loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.094657] SCSI subsystem initialized
Jun  7 17:04:11 keith-desktop kernel: [    0.094832] usbcore: registered new interface driver usbfs
Jun  7 17:04:11 keith-desktop kernel: [    0.094846] usbcore: registered new interface driver hub
Jun  7 17:04:11 keith-desktop kernel: [    0.094879] usbcore: registered new device driver usb
Jun  7 17:04:11 keith-desktop kernel: [    0.095025] ACPI: WMI: Mapper loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.095028] PCI: Using ACPI for IRQ routing
Jun  7 17:04:11 keith-desktop kernel: [    0.095165] NetLabel: Initializing
Jun  7 17:04:11 keith-desktop kernel: [    0.095167] NetLabel:  domain hash size = 128
Jun  7 17:04:11 keith-desktop kernel: [    0.095169] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  7 17:04:11 keith-desktop kernel: [    0.095186] NetLabel:  unlabeled traffic allowed by default
Jun  7 17:04:11 keith-desktop kernel: [    0.095218] Switching to clocksource tsc
Jun  7 17:04:11 keith-desktop kernel: [    0.096001] AppArmor: AppArmor Filesystem Enabled
Jun  7 17:04:11 keith-desktop kernel: [    0.096001] pnp: PnP ACPI init
Jun  7 17:04:11 keith-desktop kernel: [    0.096001] ACPI: bus type pnp registered
Jun  7 17:04:11 keith-desktop kernel: [    0.096001] pnp 00:01: io resource (0x820-0x821) overlaps 0000:00:11.0 BAR 13 (0x800-0x87f), disabling
Jun  7 17:04:11 keith-desktop kernel: [    0.097368] pnp: PnP ACPI: found 11 devices
Jun  7 17:04:11 keith-desktop kernel: [    0.097371] ACPI: ACPI bus type pnp unregistered
Jun  7 17:04:11 keith-desktop kernel: [    0.097376] PnPBIOS: Disabled by ACPI PNP
Jun  7 17:04:11 keith-desktop kernel: [    0.097392] system 00:01: ioport range 0x290-0x297 has been reserved
Jun  7 17:04:11 keith-desktop kernel: [    0.097396] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
Jun  7 17:04:11 keith-desktop kernel: [    0.097399] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jun  7 17:04:11 keith-desktop kernel: [    0.097402] system 00:01: ioport range 0x400-0x40f has been reserved
Jun  7 17:04:11 keith-desktop kernel: [    0.097407] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Jun  7 17:04:11 keith-desktop kernel: [    0.132119] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun  7 17:04:11 keith-desktop kernel: [    0.132124] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
Jun  7 17:04:11 keith-desktop kernel: [    0.132129] pci 0000:00:01.0:   MEM window: 0xdfe00000-0xdfefffff
Jun  7 17:04:11 keith-desktop kernel: [    0.132134] pci 0000:00:01.0:   PREFETCH window: 0xbfd00000-0xdfcfffff
Jun  7 17:04:11 keith-desktop kernel: [    0.132209] NET: Registered protocol family 2
Jun  7 17:04:11 keith-desktop kernel: [    0.132310] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.132792] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.134373] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.135194] TCP: Hash tables configured (established 131072 bind 65536)
Jun  7 17:04:11 keith-desktop kernel: [    0.135197] TCP reno registered
Jun  7 17:04:11 keith-desktop kernel: [    0.135321] NET: Registered protocol family 1
Jun  7 17:04:11 keith-desktop kernel: [    0.135341] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Jun  7 17:04:11 keith-desktop kernel: [    0.135654] cpufreq-nforce2: No nForce2 chipset.
Jun  7 17:04:11 keith-desktop kernel: [    0.135687] Scanning for low memory corruption every 60 seconds
Jun  7 17:04:11 keith-desktop kernel: [    0.135813] audit: initializing netlink socket (disabled)
Jun  7 17:04:11 keith-desktop kernel: [    0.135836] type=2000 audit(1275930237.132:1): initialized
Jun  7 17:04:11 keith-desktop kernel: [    0.144806] Trying to unpack rootfs image as initramfs...
Jun  7 17:04:11 keith-desktop kernel: [    0.157045] highmem bounce pool size: 64 pages
Jun  7 17:04:11 keith-desktop kernel: [    0.157053] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun  7 17:04:11 keith-desktop kernel: [    0.158822] VFS: Disk quotas dquot_6.5.2
Jun  7 17:04:11 keith-desktop kernel: [    0.158901] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun  7 17:04:11 keith-desktop kernel: [    0.159564] fuse init (API version 7.13)
Jun  7 17:04:11 keith-desktop kernel: [    0.159660] msgmni has been set to 1716
Jun  7 17:04:11 keith-desktop kernel: [    0.165248] alg: No test for stdrng (krng)
Jun  7 17:04:11 keith-desktop kernel: [    0.165333] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun  7 17:04:11 keith-desktop kernel: [    0.165336] io scheduler noop registered
Jun  7 17:04:11 keith-desktop kernel: [    0.165339] io scheduler anticipatory registered
Jun  7 17:04:11 keith-desktop kernel: [    0.165341] io scheduler deadline registered
Jun  7 17:04:11 keith-desktop kernel: [    0.165401] io scheduler cfq registered (default)
Jun  7 17:04:11 keith-desktop kernel: [    0.165524] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  7 17:04:11 keith-desktop kernel: [    0.165550] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  7 17:04:11 keith-desktop kernel: [    0.165676] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun  7 17:04:11 keith-desktop kernel: [    0.165682] ACPI: Power Button [PWRB]
Jun  7 17:04:11 keith-desktop kernel: [    0.165743] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Jun  7 17:04:11 keith-desktop kernel: [    0.165751] ACPI: Sleep Button [SLPB]
Jun  7 17:04:11 keith-desktop kernel: [    0.165805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jun  7 17:04:11 keith-desktop kernel: [    0.165808] ACPI: Power Button [PWRF]
Jun  7 17:04:11 keith-desktop kernel: [    0.165994] processor LNXCPU:00: registered as cooling_device0
Jun  7 17:04:11 keith-desktop kernel: [    0.169268] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun  7 17:04:11 keith-desktop kernel: [    0.169365] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  7 17:04:11 keith-desktop kernel: [    0.169453] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun  7 17:04:11 keith-desktop kernel: [    0.169733] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  7 17:04:11 keith-desktop kernel: [    0.169855] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun  7 17:04:11 keith-desktop kernel: [    0.171008] brd: module loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.171556] loop: module loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.171667] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jun  7 17:04:11 keith-desktop kernel: [    0.171827] pata_acpi 0000:00:11.1: can't derive routing for PCI INT A
Jun  7 17:04:11 keith-desktop kernel: [    0.171903] pata_acpi 0000:00:11.1: can't derive routing for PCI INT A
Jun  7 17:04:11 keith-desktop kernel: [    0.172227] Fixed MDIO Bus: probed
Jun  7 17:04:11 keith-desktop kernel: [    0.172265] PPP generic driver version 2.4.2
Jun  7 17:04:11 keith-desktop kernel: [    0.172311] tun: Universal TUN/TAP device driver, 1.6
Jun  7 17:04:11 keith-desktop kernel: [    0.172313] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  7 17:04:11 keith-desktop kernel: [    0.172400] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  7 17:04:11 keith-desktop kernel: [    0.172435] ehci_hcd 0000:00:10.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Jun  7 17:04:11 keith-desktop kernel: [    0.172455] ehci_hcd 0000:00:10.3: EHCI Host Controller
Jun  7 17:04:11 keith-desktop kernel: [    0.172494] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
Jun  7 17:04:11 keith-desktop kernel: [    0.172556] ehci_hcd 0000:00:10.3: irq 21, io mem 0xdffff700
Jun  7 17:04:11 keith-desktop kernel: [    0.172603] isapnp: Scanning for PnP cards...
Jun  7 17:04:11 keith-desktop kernel: [    0.184776] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
Jun  7 17:04:11 keith-desktop kernel: [    0.184944] usb usb1: configuration #1 chosen from 1 choice
Jun  7 17:04:11 keith-desktop kernel: [    0.184981] hub 1-0:1.0: USB hub found
Jun  7 17:04:11 keith-desktop kernel: [    0.184998] hub 1-0:1.0: 2 ports detected
Jun  7 17:04:11 keith-desktop kernel: [    0.185070] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  7 17:04:11 keith-desktop kernel: [    0.185090] uhci_hcd: USB Universal Host Controller Interface driver
Jun  7 17:04:11 keith-desktop kernel: [    0.185167] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun  7 17:04:11 keith-desktop kernel: [    0.185178] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jun  7 17:04:11 keith-desktop kernel: [    0.185222] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Jun  7 17:04:11 keith-desktop kernel: [    0.185249] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
Jun  7 17:04:11 keith-desktop kernel: [    0.185368] usb usb2: configuration #1 chosen from 1 choice
Jun  7 17:04:11 keith-desktop kernel: [    0.185401] hub 2-0:1.0: USB hub found
Jun  7 17:04:11 keith-desktop kernel: [    0.185414] hub 2-0:1.0: 2 ports detected
Jun  7 17:04:11 keith-desktop kernel: [    0.185498] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun  7 17:04:11 keith-desktop kernel: [    0.185501] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun  7 17:04:11 keith-desktop kernel: [    0.185652] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  7 17:04:11 keith-desktop kernel: [    0.185786] mice: PS/2 mouse device common for all mice
Jun  7 17:04:11 keith-desktop kernel: [    0.185941] rtc_cmos 00:03: RTC can wake from S4
Jun  7 17:04:11 keith-desktop kernel: [    0.185996] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun  7 17:04:11 keith-desktop kernel: [    0.186043] rtc0: alarms up to one year, y3k, 114 bytes nvram
Jun  7 17:04:11 keith-desktop kernel: [    0.186123] device-mapper: uevent: version 1.0.3
Jun  7 17:04:11 keith-desktop kernel: [    0.229803] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Jun  7 17:04:11 keith-desktop kernel: [    0.232261] device-mapper: multipath: version 1.1.0 loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.232265] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun  7 17:04:11 keith-desktop kernel: [    0.232453] EISA: Probing bus 0 at eisa.0
Jun  7 17:04:11 keith-desktop kernel: [    0.232489] EISA: Detected 0 cards.
Jun  7 17:04:11 keith-desktop kernel: [    0.235076] cpuidle: using governor ladder
Jun  7 17:04:11 keith-desktop kernel: [    0.235079] cpuidle: using governor menu
Jun  7 17:04:11 keith-desktop kernel: [    0.235562] TCP cubic registered
Jun  7 17:04:11 keith-desktop kernel: [    0.235728] NET: Registered protocol family 10
Jun  7 17:04:11 keith-desktop kernel: [    0.236192] lo: Disabled Privacy Extensions
Jun  7 17:04:11 keith-desktop kernel: [    0.236501] NET: Registered protocol family 17
Jun  7 17:04:11 keith-desktop kernel: [    0.236545] powernow-k8: Processor cpuid 6a0 not supported
Jun  7 17:04:11 keith-desktop kernel: [    0.236573] Using IPI No-Shortcut mode
Jun  7 17:04:11 keith-desktop kernel: [    0.236717] registered taskstats version 1
Jun  7 17:04:11 keith-desktop kernel: [    0.236963]   Magic number: 14:839:86
Jun  7 17:04:11 keith-desktop kernel: [    0.237079] rtc_cmos 00:03: setting system clock to 2010-06-07 17:03:57 UTC (1275930237)
Jun  7 17:04:11 keith-desktop kernel: [    0.237083] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  7 17:04:11 keith-desktop kernel: [    0.237085] EDD information not available.
Jun  7 17:04:11 keith-desktop kernel: [    0.243552] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jun  7 17:04:11 keith-desktop kernel: [    0.607044] Freeing initrd memory: 7766k freed
Jun  7 17:04:11 keith-desktop kernel: [    0.748340] isapnp: No Plug & Play device found
Jun  7 17:04:11 keith-desktop kernel: [    0.748361] Freeing unused kernel memory: 656k freed
Jun  7 17:04:11 keith-desktop kernel: [    0.749362] Write protecting the kernel text: 4676k
Jun  7 17:04:11 keith-desktop kernel: [    0.749395] Write protecting the kernel read-only data: 1840k
Jun  7 17:04:11 keith-desktop kernel: [    0.772188] udev: starting version 151
Jun  7 17:04:11 keith-desktop kernel: [    0.920772] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun  7 17:04:11 keith-desktop kernel: [    0.963096] pata_via 0000:00:11.1: can't derive routing for PCI INT A
Jun  7 17:04:11 keith-desktop kernel: [    0.978485] Floppy drive(s): fd0 is 1.44M
Jun  7 17:04:11 keith-desktop kernel: [    0.980053] scsi0 : pata_via
Jun  7 17:04:11 keith-desktop kernel: [    0.986702] scsi1 : pata_via
Jun  7 17:04:11 keith-desktop kernel: [    0.988666] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Jun  7 17:04:11 keith-desktop kernel: [    0.988670] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Jun  7 17:04:11 keith-desktop kernel: [    0.988824] sym53c8xx 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  7 17:04:11 keith-desktop kernel: [    1.123934] sym0: <1010-33> rev 0x1 at pci 0000:00:06.0 irq 17
Jun  7 17:04:11 keith-desktop kernel: [    1.126118] sym53c8xx 0000:00:06.0: PCI: Disallowing DAC for device
Jun  7 17:04:11 keith-desktop kernel: [    1.128130] sym0: Symbios NVRAM, ID 7, Fast-80, LVD, parity checking
Jun  7 17:04:11 keith-desktop kernel: [    1.128133] sym0: open drain IRQ line driver, using on-chip SRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.128135] sym0: using LOAD/STORE-based firmware.
Jun  7 17:04:11 keith-desktop kernel: [    1.128137] sym0: handling phase mismatch from SCRIPTS.
Jun  7 17:04:11 keith-desktop kernel: [    1.128911] FDC 0 is a post-1991 82077
Jun  7 17:04:11 keith-desktop kernel: [    1.132005] sym0: SCSI BUS has been reset.
Jun  7 17:04:11 keith-desktop kernel: [    1.135895] scsi2 : sym-2.2.3
Jun  7 17:04:11 keith-desktop kernel: [    1.136783] 3c59x 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  7 17:04:11 keith-desktop kernel: [    1.136787] 3c59x: Donald Becker and others.
Jun  7 17:04:11 keith-desktop kernel: [    1.136795] 0000:00:08.0: 3Com PCI 3c905 Boomerang 100baseTx at 0001dc00.
Jun  7 17:04:11 keith-desktop kernel: [    1.158093] scsi target2:0:0: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158124] scsi target2:0:1: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158145] scsi target2:0:2: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158165] scsi target2:0:3: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158185] scsi target2:0:4: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158205] scsi target2:0:5: Multiple LUNs disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.158931] sym53c8xx 0000:00:06.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Jun  7 17:04:11 keith-desktop kernel: [    1.304820] sym1: <1010-33> rev 0x1 at pci 0000:00:06.1 irq 18
Jun  7 17:04:11 keith-desktop kernel: [    1.305455] sym53c8xx 0000:00:06.1: PCI: Disallowing DAC for device
Jun  7 17:04:11 keith-desktop kernel: [    1.307462] sym1: Symbios NVRAM, ID 7, Fast-80, SE, parity checking
Jun  7 17:04:11 keith-desktop kernel: [    1.307465] sym1: open drain IRQ line driver, using on-chip SRAM
Jun  7 17:04:11 keith-desktop kernel: [    1.307467] sym1: using LOAD/STORE-based firmware.
Jun  7 17:04:11 keith-desktop kernel: [    1.307469] sym1: handling phase mismatch from SCRIPTS.
Jun  7 17:04:11 keith-desktop kernel: [    1.308002] sym1: suspicious SCSI data while resetting the BUS.
Jun  7 17:04:11 keith-desktop kernel: [    1.308002] sym1: dp1,d15-8,dp0,d7-0,rst,req,ack,bsy,sel,atn,msg,c/d,i/o = 0x400100, expecting 0x100
Jun  7 17:04:11 keith-desktop kernel: [    1.309787] sym1: giving up ...
Jun  7 17:04:11 keith-desktop kernel: [    1.309852] sym53c8xx 0000:00:06.1: PCI INT B disabled
Jun  7 17:04:11 keith-desktop kernel: [    1.312555] ata1.00: ATA-5: QUANTUM FIREBALLP AS30.0, A1Y.1500, max UDMA/100
Jun  7 17:04:11 keith-desktop kernel: [    1.312558] ata1.00: 58633344 sectors, multi 16: LBA 
Jun  7 17:04:11 keith-desktop kernel: [    1.328428] ata1.00: configured for UDMA/100
Jun  7 17:04:11 keith-desktop kernel: [    1.328448] scsi: waiting for bus probes to complete ...
Jun  7 17:04:11 keith-desktop kernel: [    1.559061] usb 2-1: configuration #1 chosen from 1 choice
Jun  7 17:04:11 keith-desktop kernel: [    1.800011] usb 2-2: new low speed USB device using uhci_hcd and address 3
Jun  7 17:04:11 keith-desktop kernel: [    1.974951] usb 2-2: configuration #1 chosen from 1 choice
Jun  7 17:04:11 keith-desktop kernel: [    4.134669] scsi 2:0:5:0: Sequential-Access ARCHIVE  Python 06408-XXX 9050 PQ: 0 ANSI: 3
Jun  7 17:04:11 keith-desktop kernel: [    4.134693] scsi target2:0:5: Beginning Domain Validation
Jun  7 17:04:11 keith-desktop kernel: [    4.145743] scsi 2:0:5:0: phase change 6-7 9@368acf9c resid=6.
Jun  7 17:04:11 keith-desktop kernel: [    4.147976] scsi target2:0:5: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 31)
Jun  7 17:04:11 keith-desktop kernel: [    4.151694] scsi target2:0:5: Domain Validation skipping write tests
Jun  7 17:04:11 keith-desktop kernel: [    4.151697] scsi target2:0:5: Ending Domain Validation
Jun  7 17:04:11 keith-desktop kernel: [    4.156444] scsi target2:0:6: Multiple LUNs disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.156936] scsi 2:0:6:0: Direct-Access     QUANTUM  ATLAS10K3_18_WLS 020W PQ: 0 ANSI: 3
Jun  7 17:04:11 keith-desktop kernel: [    4.156941] scsi target2:0:6: tagged command queuing enabled, command queue depth 16.
Jun  7 17:04:11 keith-desktop kernel: [    4.156946] scsi target2:0:6: Beginning Domain Validation
Jun  7 17:04:11 keith-desktop kernel: [    4.159648] scsi target2:0:6: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 62)
Jun  7 17:04:11 keith-desktop kernel: [    4.164229] scsi target2:0:6: Ending Domain Validation
Jun  7 17:04:11 keith-desktop kernel: [    4.164402] scsi target2:0:8: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164427] scsi target2:0:9: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164448] scsi target2:0:10: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164469] scsi target2:0:11: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164490] scsi target2:0:12: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164510] scsi target2:0:13: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164530] scsi target2:0:14: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164551] scsi target2:0:15: Scan at boot disabled in NVRAM
Jun  7 17:04:11 keith-desktop kernel: [    4.164914] scsi 2:0:5:0: Attached scsi generic sg0 type 1
Jun  7 17:04:11 keith-desktop kernel: [    4.165379] sd 2:0:6:0: Attached scsi generic sg1 type 0
Jun  7 17:04:11 keith-desktop kernel: [    4.165535] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A1Y. PQ: 0 ANSI: 5
Jun  7 17:04:11 keith-desktop kernel: [    4.165664] sd 0:0:0:0: Attached scsi generic sg2 type 0
Jun  7 17:04:11 keith-desktop kernel: [    4.166041] sd 0:0:0:0: [sdb] 58633344 512-byte logical blocks: (30.0 GB/27.9 GiB)
Jun  7 17:04:11 keith-desktop kernel: [    4.166097] sd 0:0:0:0: [sdb] Write Protect is off
Jun  7 17:04:11 keith-desktop kernel: [    4.166115] sd 2:0:6:0: [sda] 35916548 512-byte logical blocks: (18.3 GB/17.1 GiB)
Jun  7 17:04:11 keith-desktop kernel: [    4.166151] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  7 17:04:11 keith-desktop kernel: [    4.166312]  sdb:
Jun  7 17:04:11 keith-desktop kernel: [    4.167545] sd 2:0:6:0: [sda] Write Protect is off
Jun  7 17:04:11 keith-desktop kernel: [    4.168709] sd 2:0:6:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
Jun  7 17:04:11 keith-desktop kernel: [    4.171586]  sda: sdb1
Jun  7 17:04:11 keith-desktop kernel: [    4.172293] sd 0:0:0:0: [sdb] Attached SCSI disk
Jun  7 17:04:11 keith-desktop kernel: [    4.180303]  sda1 sda2 < sda5 >
Jun  7 17:04:11 keith-desktop kernel: [    4.197171] sd 2:0:6:0: [sda] Attached SCSI disk
Jun  7 17:04:11 keith-desktop kernel: [    4.328384] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22LP20, 1.04, max UDMA/66
Jun  7 17:04:11 keith-desktop kernel: [    4.344271] ata2.00: configured for UDMA/66
Jun  7 17:04:11 keith-desktop kernel: [    4.346267] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LP20 1.04 PQ: 0 ANSI: 5
Jun  7 17:04:11 keith-desktop kernel: [    4.349714] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun  7 17:04:11 keith-desktop kernel: [    4.349718] Uniform CD-ROM driver Revision: 3.20
Jun  7 17:04:11 keith-desktop kernel: [    4.349910] sr 1:0:0:0: Attached scsi generic sg3 type 5
Jun  7 17:04:11 keith-desktop kernel: [    4.370679] usbcore: registered new interface driver hiddev
Jun  7 17:04:11 keith-desktop kernel: [    4.374340] st: Version 20081215, fixed bufsize 32768, s/g segs 256
Jun  7 17:04:11 keith-desktop kernel: [    4.375045] st 2:0:5:0: Attached scsi tape st0
Jun  7 17:04:11 keith-desktop kernel: [    4.375048] st 2:0:5:0: st0: try direct i/o: yes (alignment 4 B)
Jun  7 17:04:11 keith-desktop kernel: [    4.382394] osst :I: Tape driver with OnStream support version 0.99.4
Jun  7 17:04:11 keith-desktop kernel: [    4.382397] osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
Jun  7 17:04:11 keith-desktop kernel: [    4.386705] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input5
Jun  7 17:04:11 keith-desktop kernel: [    4.386834] generic-usb 0003:046D:C408.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:10.0-2/input0
Jun  7 17:04:11 keith-desktop kernel: [    4.386869] usbcore: registered new interface driver usbhid
Jun  7 17:04:11 keith-desktop kernel: [    4.386872] usbhid: v2.6:USB HID core driver
Jun  7 17:04:11 keith-desktop kernel: [    4.558581] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun  7 17:04:11 keith-desktop kernel: [   12.701389] udev: starting version 151
Jun  7 17:04:11 keith-desktop kernel: [   12.717293] Adding 794616k swap on /dev/sda5.  Priority:-1 extents:1 across:794616k 
Jun  7 17:04:11 keith-desktop kernel: [   12.837609] lp: driver loaded but no devices found
Jun  7 17:04:11 keith-desktop kernel: [   12.843710] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun  7 17:04:11 keith-desktop kernel: [   12.936894] Linux agpgart interface v0.103
Jun  7 17:04:11 keith-desktop kernel: [   13.249735] agpgart: Detected VIA KT266/KY266x/KT333 chipset
Jun  7 17:04:11 keith-desktop kernel: [   13.266041] usbcore: registered new interface driver usblp
Jun  7 17:04:11 keith-desktop kernel: [   13.266844] parport_pc 00:0a: reported by Plug and Play ACPI
Jun  7 17:04:11 keith-desktop kernel: [   13.266960] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun  7 17:04:11 keith-desktop kernel: [   13.274525] NET: Registered protocol family 23
Jun  7 17:04:11 keith-desktop kernel: [   13.327535] type=1505 audit(1275955450.586:2):  operation="profile_load" pid=488 name="/sbin/dhclient3"
Jun  7 17:04:11 keith-desktop kernel: [   13.327850] type=1505 audit(1275955450.586:3):  operation="profile_load" pid=488 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun  7 17:04:11 keith-desktop kernel: [   13.336081] type=1505 audit(1275955450.598:4):  operation="profile_load" pid=488 name="/usr/lib/connman/scripts/dhclient-script"
Jun  7 17:04:11 keith-desktop kernel: [   13.346503] type=1505 audit(1275955450.606:5):  operation="profile_load" pid=502 name="/usr/sbin/ntpd"
Jun  7 17:04:11 keith-desktop kernel: [   13.347364] ppdev: user-space parallel port driver
Jun  7 17:04:11 keith-desktop kernel: [   13.354573] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Jun  7 17:04:11 keith-desktop kernel: [   13.370552] lp0: using parport0 (interrupt-driven).
Jun  7 17:04:11 keith-desktop kernel: [   13.511379] gameport: EMU10K1 is pci0000:00:07.1/gameport0, io 0xec00, speed 1242kHz
Jun  7 17:04:11 keith-desktop kernel: [   13.526036] ACPI: resource vt596_smbus [0x400-0x407] conflicts with ACPI region SMOV [0x400-0x406]
Jun  7 17:04:11 keith-desktop kernel: [   13.526040] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun  7 17:04:11 keith-desktop kernel: [   13.529270] [drm] Initialized drm 1.1.0 20060810
Jun  7 17:04:11 keith-desktop kernel: [   13.692128] [drm] radeon defaulting to kernel modesetting.
Jun  7 17:04:11 keith-desktop kernel: [   13.692133] [drm] radeon kernel modesetting enabled.
Jun  7 17:04:11 keith-desktop kernel: [   13.692219] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  7 17:04:11 keith-desktop kernel: [   13.711983] [drm] radeon: Initializing kernel modesetting.
Jun  7 17:04:11 keith-desktop kernel: [   13.715214] [drm] register mmio base: 0xDFEF0000
Jun  7 17:04:11 keith-desktop kernel: [   13.715219] [drm] register mmio size: 65536
Jun  7 17:04:11 keith-desktop kernel: [   13.715362] ATOM BIOS: R481
Jun  7 17:04:11 keith-desktop kernel: [   13.715602] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Jun  7 17:04:11 keith-desktop kernel: [   13.715625] [drm] Generation 2 PCI interface, using max accessible memory
Jun  7 17:04:11 keith-desktop kernel: [   13.715634] agpgart-via 0000:00:00.0: AGP 2.0 bridge
Jun  7 17:04:11 keith-desktop kernel: [   13.715653] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Jun  7 17:04:11 keith-desktop kernel: [   13.715694] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
Jun  7 17:04:11 keith-desktop kernel: [   13.715702] [drm] radeon: VRAM 128M
Jun  7 17:04:11 keith-desktop kernel: [   13.715704] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
Jun  7 17:04:11 keith-desktop kernel: [   13.715706] [drm] radeon: GTT 256M
Jun  7 17:04:11 keith-desktop kernel: [   13.715708] [drm] radeon: GTT from 0xE0000000 to 0xEFFFFFFF
Jun  7 17:04:11 keith-desktop kernel: [   13.715768] [drm] radeon: irq initialized.
Jun  7 17:04:11 keith-desktop kernel: [   13.716056] [drm] Detected VRAM RAM=128M, BAR=128M
Jun  7 17:04:11 keith-desktop kernel: [   13.716062] [drm] RAM width 256bits DDR
Jun  7 17:04:11 keith-desktop kernel: [   13.718106] [TTM] Zone  kernel: Available graphics memory: 443632 kiB.
Jun  7 17:04:11 keith-desktop kernel: [   13.718111] [TTM] Zone highmem: Available graphics memory: 513236 kiB.
Jun  7 17:04:11 keith-desktop kernel: [   13.718140] [drm] radeon: 128M of VRAM memory ready
Jun  7 17:04:11 keith-desktop kernel: [   13.718142] [drm] radeon: 256M of GTT memory ready.
Jun  7 17:04:11 keith-desktop kernel: [   13.718190] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
Jun  7 17:04:11 keith-desktop kernel: [   13.718201] [drm] radeon: cp idle (0x10000C03)
Jun  7 17:04:11 keith-desktop kernel: [   13.718349] [drm] Loading R400 Microcode
Jun  7 17:04:11 keith-desktop kernel: [   13.718777] platform radeon_cp.0: firmware: requesting radeon/R420_cp.bin
Jun  7 17:04:11 keith-desktop kernel: [   13.882071] type=1505 audit(1275955451.142:6):  operation="profile_load" pid=641 name="/usr/share/gdm/guest-session/Xsession"
Jun  7 17:04:11 keith-desktop kernel: [   13.887663] type=1505 audit(1275955451.146:7):  operation="profile_replace" pid=642 name="/sbin/dhclient3"
Jun  7 17:04:11 keith-desktop kernel: [   13.888060] type=1505 audit(1275955451.150:8):  operation="profile_replace" pid=642 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun  7 17:04:11 keith-desktop kernel: [   13.896745] [drm] radeon: ring at 0x00000000E0000000
Jun  7 17:04:11 keith-desktop kernel: [   13.896768] [drm] ring test succeeded in 0 usecs
Jun  7 17:04:11 keith-desktop kernel: [   13.914912] type=1505 audit(1275955451.174:9):  operation="profile_replace" pid=642 name="/usr/lib/connman/scripts/dhclient-script"
Jun  7 17:04:11 keith-desktop kernel: [   13.983649] type=1505 audit(1275955451.242:10):  operation="profile_load" pid=645 name="/usr/bin/evince"
Jun  7 17:04:11 keith-desktop kernel: [   13.991067] eth0:  setting full-duplex.
Jun  7 17:04:11 keith-desktop kernel: [   13.995311] type=1505 audit(1275955451.254:11):  operation="profile_load" pid=645 name="/usr/bin/evince-previewer"
Jun  7 17:04:11 keith-desktop kernel: [   14.074010] [drm] radeon: ib pool ready.
Jun  7 17:04:11 keith-desktop kernel: [   14.074116] [drm] ib test succeeded in 0 usecs
Jun  7 17:04:11 keith-desktop kernel: [   14.074173] [drm] Default TV standard: NTSC
Jun  7 17:04:11 keith-desktop kernel: [   14.075444] [drm] Default TV standard: NTSC
Jun  7 17:04:11 keith-desktop kernel: [   14.076975] [drm] Radeon Display Connectors
Jun  7 17:04:11 keith-desktop kernel: [   14.076979] [drm] Connector 0:
Jun  7 17:04:11 keith-desktop kernel: [   14.076981] [drm]   VGA
Jun  7 17:04:11 keith-desktop kernel: [   14.076984] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jun  7 17:04:11 keith-desktop kernel: [   14.076986] [drm]   Encoders:
Jun  7 17:04:11 keith-desktop kernel: [   14.076988] [drm]     CRT1: INTERNAL_DAC1
Jun  7 17:04:11 keith-desktop kernel: [   14.076990] [drm] Connector 1:
Jun  7 17:04:11 keith-desktop kernel: [   14.076991] [drm]   S-video
Jun  7 17:04:11 keith-desktop kernel: [   14.076992] [drm]   Encoders:
Jun  7 17:04:11 keith-desktop kernel: [   14.076994] [drm]     TV1: INTERNAL_DAC2
Jun  7 17:04:11 keith-desktop kernel: [   14.076996] [drm] Connector 2:
Jun  7 17:04:11 keith-desktop kernel: [   14.076997] [drm]   DVI-I
Jun  7 17:04:11 keith-desktop kernel: [   14.076998] [drm]   HPD1
Jun  7 17:04:11 keith-desktop kernel: [   14.077001] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
Jun  7 17:04:11 keith-desktop kernel: [   14.077003] [drm]   Encoders:
Jun  7 17:04:11 keith-desktop kernel: [   14.077004] [drm]     CRT2: INTERNAL_DAC2
Jun  7 17:04:11 keith-desktop kernel: [   14.077006] [drm]     DFP1: INTERNAL_TMDS1
Jun  7 17:04:11 keith-desktop kernel: [   14.114644] EMU10K1_Audigy 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun  7 17:04:11 keith-desktop kernel: [   14.368695] [drm] fb mappable at 0xD0040000
Jun  7 17:04:11 keith-desktop kernel: [   14.368699] [drm] vram apper at 0xD0000000
Jun  7 17:04:11 keith-desktop kernel: [   14.368701] [drm] size 5242880
Jun  7 17:04:11 keith-desktop kernel: [   14.368703] [drm] fb depth is 24
Jun  7 17:04:11 keith-desktop kernel: [   14.368705] [drm]    pitch is 5120
Jun  7 17:04:11 keith-desktop kernel: [   14.373078] fb0: radeondrmfb frame buffer device
Jun  7 17:04:11 keith-desktop kernel: [   14.373082] registered panic notifier
Jun  7 17:04:11 keith-desktop kernel: [   14.373090] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Jun  7 17:04:11 keith-desktop kernel: [   14.380191] vga16fb: mapped to 0xc00a0000
Jun  7 17:04:11 keith-desktop kernel: [   14.380197] vga16fb: not registering due to another framebuffer present
Jun  7 17:04:11 keith-desktop kernel: [   14.627696] Console: switching to colour frame buffer device 160x64
Jun  7 17:08:57 keith-desktop kernel: [  300.004011] Disabling lock debugging due to kernel taint
Jun  7 17:08:57 keith-desktop kernel: [  300.004020] Machine check events logged
Jun  7 17:11:27 keith-desktop kernel: [  450.004032] Machine check events logged
Jun  7 17:12:42 keith-desktop kernel: [  525.004029] Machine check events logged
:confused:

---

### Post by Keith Myers on 2010-06-07
A quick question.  Just what is the normal syntax or callout of an error message?  How does it announce itself in Linux?  Does it have a number assigned to it like in OS/2?  Or does each message differ according to what sub-system it applies to?

Keith

---

