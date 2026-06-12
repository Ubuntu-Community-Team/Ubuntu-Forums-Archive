---
title: "Ubuntu 10.04 keeps rebooting"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by 416inversed on 2010-10-04
My dual-booting (10.04 & XP) Acer Aspire D250 keeps rebooting itself.

Most times, it lasts long enough to load firefox before suddenly rebooting, although other times it reboots again mid-boot (after BURG, but before login). Happens both in Gnome & Lubuntu and all three kernels I have -25, -24 & -23.

However it's stable from my 9.10 UNR thumbdrive & in XP.

Any thought on how to further diagnose & remedy this?

---

### Post by 416inversed on 2010-10-05
Bump?

---

### Post by Clever_Username on 2010-10-05
Does it do it when you have the OS other than Ubuntu loaded?
Assuming it doesn't, can you maybe post the messages or syslog log files

---

### Post by lukeiamyourfather on 2010-10-05
Typically random restarts are power related (e.g. bad power supply or voltage regulators on the motherboard). Since it doesn't happen in other operating systems I'm not sure what to suggest.

---

### Post by 416inversed on 2010-10-05
Only happens when I boot into 10.04; I'm stable in XP & when I boot 9.10 UNR off of a thumb drive.

The last entries from the Messages log before the last reboot:
```
Oct  5 13:02:51 Minotaur-Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="896" x-info="http://www.rsyslog.com"] (re)start
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: rsyslogd's groupid changed to 102
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: rsyslogd's userid changed to 101
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] KERNEL supported cpus:
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Intel GenuineIntel
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   NSC Geode by NSC
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ef000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f6ef000 - 000000003f6ff000 (ACPI data)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct  5 13:02:51 Minotaur-UbunOct  5 15:13:09 Minotaur-Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.

```And from the Syslog
```
Oct  5 13:02:51 Minotaur-Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="896" x-info="http://www.rsyslog.com"] (re)start
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: rsyslogd's groupid changed to 102
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd: rsyslogd's userid changed to 101
Oct  5 13:02:51 Minotaur-Ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] KERNEL supported cpus:
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Intel GenuineIntel
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   NSC Geode by NSC
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
Oct  5 13:02:51 Minotaur-Ubuntu kernel: [    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ef000 (usable)
Oct  5 13:02:51 Minotaur-Ubuntu kernel:Oct  5 15:13:09 Minotaur-Ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

---

### Post by NightwishFan on 2010-10-05
Try booting with the option "acpi=off". Do you know how to add boot options?

---

### Post by 416inversed on 2010-10-05
> **NightwishFan said:**
> Try booting with the option "acpi=off". Do you know how to add boot options?

I think so. I add "acpi=off" to "GRUB_CMDLINE_LINUX" variables in /etc/default/burg (and /etc/default/grub), right?

If so, I'll give it a try.

---

### Post by NightwishFan on 2010-10-05
Just /etc/default/grub, and then run "sudo update-grub"

---

### Post by P4man on 2010-10-06
As someone else said, random reboots are usually a sign of hardware trouble. 
The fact other OS's dont seem to have this problem doesnt quite dispove this thesis; its possible ubuntu loads in ram bottom up and windows top down and 9.10 uses considerably less memory.

Since memtest86 is right in your grub/burg menu, it wont hurt to let it run overnight to make sure its not a bad memory module.

---

### Post by 416inversed on 2010-10-07
Ok. So I ran memtest last night for just under 12 hours: 14 passes, no errors.

But as soon as I ESC to restart, the machine goes into a rebooting tizzy, where it would reboot just past BURG.

I also had GRUB error messages "free magic is broken" and "null in the ring" that would stall the reboots.

Thoughts?

---

### Post by P4man on 2010-10-07
Interesting. Googling on that error, I find this "bug" report:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882)

Same symptoms as you, but it turns out.. he had bad RAM. But if yours passes 14 hours of memtest, its gotta be something else. IM still suspecting a hardware issue though. Insufficient power supply, corrupted bios, overheating,.. ?

---

### Post by 416inversed on 2010-10-07
I swapped out the RAM with a spare stick, just because I could.

Power supply-wise, it happens both on AC & on Battery.

Doing a little research, my bios is out-of-date: I'm @ v1.01 while it's up to 1.28, but I'm not certain as to how to upgrade it....

It could possibly related to overheating, as netbooks have terrible airflow & the reboots seem to be more prevalent after it has been on awhile than from a cold start, but they still occasionally happen while cold and  the computer never seems unusually warm.

[B]
UPDATE[/B]: So it's still happening, even after swapping out the RAM.

---

### Post by P4man on 2010-10-07
There is chance swapping the memory module didnt help because half the memory is soldered to the motherboard (well, on some machines anyway). But again, RAM doesnt seem likely as a cause if it passes memtest.

Flashing the BIOS would be a very good idea. In ubuntu, it might be tricky though. If Acer has a flash utility that works under DOS, then have a look here:
[http://macles.blogspot.com/2008/07/flashing-bios.html](http://macles.blogspot.com/2008/07/flashing-bios.html)

If it requires windows, then you might try with Bart PE, though Im not sure if that works for flashing.

---

### Post by 416inversed on 2010-10-07
Ok. I flashed the BIOS... keeping my fingers crossed.

---

### Post by 416inversed on 2010-10-07
And it still happens....

---

### Post by P4man on 2010-10-07
Bummer :(
Can you post your dmesg output?

---

### Post by 416inversed on 2010-10-07
dmesg log:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  BIOS-e820: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  BIOS-e820: 000000003f6ee000 - 000000003f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f576000 (usable)
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (reserved)
[    0.000000]  modified: 000000003f5bf000 - 000000003f66d000 (usable)
[    0.000000]  modified: 000000003f66d000 - 000000003f6bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f6bf000 - 000000003f6ee000 (usable)
[    0.000000]  modified: 000000003f6ee000 - 000000003f6ff000 (ACPI data)
[    0.000000]  modified: 000000003f6ff000 - 000000003f700000 (usable)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2eab4000 - 2f858729
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f6f0000 0710E (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f688000 00040
[    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [002eab4000 - 002f858729]          RAMDISK ==> [002eab4000 - 002f858729]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008dd000 - 00008e0178]              BRK ==> [00008dd000 - 00008e0178]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f576
[    0.000000]     0: 0x0003f5bf -> 0x0003f66d
[    0.000000]     0: 0x0003f6bf -> 0x0003f6ee
[    0.000000]     0: 0x0003f6ff -> 0x0003f700
[    0.000000] On node 0 totalpages: 259567
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32087 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257536
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=7849cfb4-2aec-4b51-9793-b825eae667a3 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5196800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f700)
[    0.000000] Memory: 1001484k/1039360k available (4680k kernel code, 36200k reserved, 2122k data, 656k init, 129368k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc05922c7 - 0xc07a4e68   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05922c7   (4680 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.847 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.69 BogoMIPS (lpj=6383388)
[    0.004050] Security Framework initialized
[    0.004097] AppArmor: AppArmor initialized
[    0.004114] Mount-cache hash table entries: 512
[    0.004369] Initializing cgroup subsys ns
[    0.004380] Initializing cgroup subsys cpuacct
[    0.004390] Initializing cgroup subsys memory
[    0.004405] Initializing cgroup subsys devices
[    0.004411] Initializing cgroup subsys freezer
[    0.004417] Initializing cgroup subsys net_cls
[    0.004458] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004464] CPU: L2 cache: 512K
[    0.004470] CPU: Physical Processor ID: 0
[    0.004475] CPU: Processor Core ID: 0
[    0.004482] mce: CPU supports 5 MCE banks
[    0.004502] CPU0: Thermal monitoring enabled (TM2)
[    0.004511] using mwait in idle threads.
[    0.004524] Performance Events: Atom events, Intel PMU driver.
[    0.004542] ... version:                3
[    0.004547] ... bit width:              40
[    0.004551] ... generic registers:      2
[    0.004556] ... value mask:             000000ffffffffff
[    0.004561] ... max period:             000000007fffffff
[    0.004566] ... fixed-purpose events:   3
[    0.004571] ... event mask:             0000000700000003
[    0.004581] Checking 'hlt' instruction... OK.
[    0.020009] Disabling 4MB page tables to avoid TLB bug
[    0.024466] ACPI: Core revision 20090903
[    0.052015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.052027] ftrace: allocating 21789 entries in 43 pages
[    0.056120] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056528] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.096869] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.100001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.184096] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.184125] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.188041] Brought up 2 CPUs
[    0.188048] Total of 2 processors activated (6383.63 BogoMIPS).
[    0.188324] CPU0 attaching sched-domain:
[    0.188334]  domain 0: span 0-1 level SIBLING
[    0.188340]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.188353]   domain 1: span 0-1 level MC
[    0.188358]    groups: 0-1 (cpu_power = 1178)
[    0.188371] CPU1 attaching sched-domain:
[    0.188375]  domain 0: span 0-1 level SIBLING
[    0.188380]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.188392]   domain 1: span 0-1 level MC
[    0.188397]    groups: 0-1 (cpu_power = 1178)
[    0.188640] devtmpfs: initialized
[    0.188640] regulator: core version 0.5
[    0.188640] Time: 11:24:44  Date: 10/07/10
[    0.188640] NET: Registered protocol family 16
[    0.188640] Trying to unpack rootfs image as initramfs...
[    0.188640] EISA bus registered
[    0.188640] ACPI: bus type pci registered
[    0.188802] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.188812] PCI: MCFG area at e0000000 reserved in E820
[    0.188820] PCI: Using MMCONFIG for extended config space
[    0.188827] PCI: Using configuration type 1 for base access
[    0.194077] bio: create slab <bio-0> at 0
[    0.197297] ACPI: EC: Look up EC in DSDT
[    0.234075] ACPI: Executed 1 blocks of module-level executable AML code
[    0.239597] ACPI: BIOS _OSI(Linux) query ignored
[    0.240196] ACPI: BIOS _OSI(Linux) query ignored
[    0.241737] ACPI: Interpreter enabled
[    0.241749] ACPI: (supports S0 S3 S4 S5)
[    0.241830] ACPI: Using IOAPIC for interrupt routing
[    0.384469] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.384695] ACPI: Power Resource [FN00] (on)
[    0.385411] ACPI: No dock devices found.
[    0.387166] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.387188] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.387211] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.387292] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.387508] pci 0000:00:02.0: reg 10 32bit mmio: [0x58280000-0x582fffff]
[    0.387521] pci 0000:00:02.0: reg 14 io port: [0x60f0-0x60f7]
[    0.387533] pci 0000:00:02.0: reg 18 32bit mmio pref: [0x40000000-0x4fffffff]
[    0.387546] pci 0000:00:02.0: reg 1c 32bit mmio: [0x58300000-0x5833ffff]
[    0.387614] pci 0000:00:02.1: reg 10 32bit mmio: [0x58200000-0x5827ffff]
[    0.387791] pci 0000:00:1b.0: reg 10 64bit mmio: [0x58340000-0x58343fff]
[    0.387876] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.387887] pci 0000:00:1b.0: PME# disabled
[    0.388051] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.388062] pci 0000:00:1c.0: PME# disabled
[    0.388194] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.388205] pci 0000:00:1c.1: PME# disabled
[    0.388335] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.388345] pci 0000:00:1c.2: PME# disabled
[    0.388486] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.388497] pci 0000:00:1c.3: PME# disabled
[    0.388591] pci 0000:00:1d.0: reg 20 io port: [0x60a0-0x60bf]
[    0.388683] pci 0000:00:1d.1: reg 20 io port: [0x6080-0x609f]
[    0.388773] pci 0000:00:1d.2: reg 20 io port: [0x6060-0x607f]
[    0.388863] pci 0000:00:1d.3: reg 20 io port: [0x6040-0x605f]
[    0.388960] pci 0000:00:1d.7: reg 10 32bit mmio: [0x58344400-0x583447ff]
[    0.389044] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.389055] pci 0000:00:1d.7: PME# disabled
[    0.389310] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.389323] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.389336] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.389347] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.389452] pci 0000:00:1f.2: reg 10 io port: [0x60d8-0x60df]
[    0.389468] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.389483] pci 0000:00:1f.2: reg 18 io port: [0x60d0-0x60d7]
[    0.389498] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.389514] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x602f]
[    0.389530] pci 0000:00:1f.2: reg 24 32bit mmio: [0x58344000-0x583443ff]
[    0.389583] pci 0000:00:1f.2: PME# supported from D3hot
[    0.389593] pci 0000:00:1f.2: PME# disabled
[    0.389679] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.389824] pci 0000:01:00.0: reg 10 64bit mmio: [0x57100000-0x5710ffff]
[    0.389940] pci 0000:01:00.0: supports D1 D2
[    0.389947] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.389960] pci 0000:01:00.0: PME# disabled
[    0.390075] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.390089] pci 0000:00:1c.0: bridge 32bit mmio: [0x57100000-0x581fffff]
[    0.390105] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.390193] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.390204] pci 0000:00:1c.1: bridge 32bit mmio: [0x56100000-0x570fffff]
[    0.390220] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.390319] pci 0000:03:00.0: reg 10 64bit mmio: [0x55000000-0x5503ffff]
[    0.390337] pci 0000:03:00.0: reg 18 io port: [0x2000-0x207f]
[    0.390443] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.390456] pci 0000:03:00.0: PME# disabled
[    0.390557] pci 0000:00:1c.2: bridge io port: [0x2000-0x3fff]
[    0.390568] pci 0000:00:1c.2: bridge 32bit mmio: [0x55000000-0x560fffff]
[    0.390585] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]
[    0.390670] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    0.390682] pci 0000:00:1c.3: bridge 32bit mmio: [0x54000000-0x54ffffff]
[    0.390697] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53000000-0x53ffffff]
[    0.390786] pci 0000:00:1e.0: transparent bridge
[    0.390852] pci_bus 0000:00: on NUMA node 0
[    0.390883] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.391489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.391846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.392149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.392409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.392959] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.392980] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.411092] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.411450] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.411807] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.412195] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.412558] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.412906] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.413275] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.413619] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.414028] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.414064] vgaarb: loaded
[    0.414415] SCSI subsystem initialized
[    0.414697] libata version 3.00 loaded.
[    0.414943] usbcore: registered new interface driver usbfs
[    0.414991] usbcore: registered new interface driver hub
[    0.415079] usbcore: registered new device driver usb
[    0.415796] ACPI: WMI: Mapper loaded
[    0.415804] PCI: Using ACPI for IRQ routing
[    0.416297] NetLabel: Initializing
[    0.416304] NetLabel:  domain hash size = 128
[    0.416310] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.416343] NetLabel:  unlabeled traffic allowed by default
[    0.416464] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.416481] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.420360] Switching to clocksource tsc
[    0.425127] AppArmor: AppArmor Filesystem Enabled
[    0.425172] pnp: PnP ACPI init
[    0.425218] ACPI: bus type pnp registered
[    0.491969] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
[    0.494650] pnp: PnP ACPI: found 9 devices
[    0.494659] ACPI: ACPI bus type pnp unregistered
[    0.494668] PnPBIOS: Disabled by ACPI PNP
[    0.494708] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.494720] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.494729] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.494739] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.494749] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.494758] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.494809] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.494822] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.494834] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.494847] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.494863] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.494874] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.494889] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.494904] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.530170] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.530182] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.530196] pci 0000:00:1c.0:   MEM window: 0x57100000-0x581fffff
[    0.530208] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.530224] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.530233] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.530246] pci 0000:00:1c.1:   MEM window: 0x56100000-0x570fffff
[    0.530257] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.530273] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.530283] pci 0000:00:1c.2:   IO window: 0x2000-0x3fff
[    0.530296] pci 0000:00:1c.2:   MEM window: 0x55000000-0x560fffff
[    0.530307] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff
[    0.530323] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.530332] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    0.530344] pci 0000:00:1c.3:   MEM window: 0x54000000-0x54ffffff
[    0.530356] pci 0000:00:1c.3:   PREFETCH window: 0x00000053000000-0x00000053ffffff
[    0.530371] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.530378] pci 0000:00:1e.0:   IO window: disabled
[    0.530389] pci 0000:00:1e.0:   MEM window: disabled
[    0.530398] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.530443]   alloc irq_desc for 16 on node -1
[    0.530450]   alloc kstat_irqs on node -1
[    0.530469] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.530483] pci 0000:00:1c.0: setting latency timer to 64
[    0.530503] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.530514]   alloc irq_desc for 17 on node -1
[    0.530520]   alloc kstat_irqs on node -1
[    0.530531] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.530545] pci 0000:00:1c.1: setting latency timer to 64
[    0.530565]   alloc irq_desc for 18 on node -1
[    0.530571]   alloc kstat_irqs on node -1
[    0.530582] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.530593] pci 0000:00:1c.2: setting latency timer to 64
[    0.530612] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.530623]   alloc irq_desc for 19 on node -1
[    0.530629]   alloc kstat_irqs on node -1
[    0.530640] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.530654] pci 0000:00:1c.3: setting latency timer to 64
[    0.530672] pci 0000:00:1e.0: setting latency timer to 64
[    0.530685] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.530693] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.530702] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.530713] pci_bus 0000:01: resource 1 mem: [0x57100000-0x581fffff]
[    0.530722] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.530731] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.530740] pci_bus 0000:02: resource 1 mem: [0x56100000-0x570fffff]
[    0.530750] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.530759] pci_bus 0000:03: resource 0 io:  [0x2000-0x3fff]
[    0.530816] pci_bus 0000:03: resource 1 mem: [0x55000000-0x560fffff]
[    0.530824] pci_bus 0000:03: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.530833] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.530842] pci_bus 0000:04: resource 1 mem: [0x54000000-0x54ffffff]
[    0.530851] pci_bus 0000:04: resource 2 pref mem [0x53000000-0x53ffffff]
[    0.530859] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.530868] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.530987] NET: Registered protocol family 2
[    0.531274] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.532226] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.533854] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.534424] TCP: Hash tables configured (established 131072 bind 65536)
[    0.534439] TCP reno registered
[    0.534733] NET: Registered protocol family 1
[    0.534886] pci 0000:00:02.0: Boot video device
[    0.535228] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.535236] Simple Boot Flag at 0x44 set to 0x1
[    0.535738] cpufreq-nforce2: No nForce2 chipset.
[    0.535819] Scanning for low memory corruption every 60 seconds
[    0.536171] audit: initializing netlink socket (disabled)
[    0.536200] type=2000 audit(1286450684.534:1): initialized
[    0.558059] highmem bounce pool size: 64 pages
[    0.558078] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.563460] VFS: Disk quotas dquot_6.5.2
[    0.563679] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.565747] fuse init (API version 7.13)
[    0.566052] msgmni has been set to 1704
[    0.566756] alg: No test for stdrng (krng)
[    0.567001] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.567011] io scheduler noop registered
[    0.567017] io scheduler anticipatory registered
[    0.567023] io scheduler deadline registered
[    0.567178] io scheduler cfq registered (default)
[    0.567547]   alloc irq_desc for 24 on node -1
[    0.567555]   alloc kstat_irqs on node -1
[    0.567579] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.567599] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.567877]   alloc irq_desc for 25 on node -1
[    0.567884]   alloc kstat_irqs on node -1
[    0.567904] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.567924] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.568202]   alloc irq_desc for 26 on node -1
[    0.568209]   alloc kstat_irqs on node -1
[    0.568227] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.568245] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.568522]   alloc irq_desc for 27 on node -1
[    0.568529]   alloc kstat_irqs on node -1
[    0.568546] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.568564] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.568811] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.569105] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.569125] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.569484] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.569504] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.569859] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.569878] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.570220] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.570239] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.570653] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.570672] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.571081] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.571100] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.571468] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.571487] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.571846] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.571864] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7016a68), AE_ALREADY_EXISTS
[    0.572004] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.635129] ACPI: AC Adapter [AC] (on-line)
[    0.635419] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.635431] ACPI: Power Button [PWRB]
[    0.635581] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.635721] ACPI: Lid Switch [LID0]
[    0.635874] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.635883] ACPI: Sleep Button [SLPB]
[    0.636064] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.636073] ACPI: Power Button [PWRF]
[    0.636505] fan PNP0C0B:00: registered as cooling_device0
[    0.636525] ACPI: Fan [FAN] (on)
[    0.638479] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.639759] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.642048] Marking TSC unstable due to TSC halts in idle
[    0.642313] processor LNXCPU:00: registered as cooling_device1
[    0.643415] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.644550] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.645471] Switching to clocksource hpet
[    0.647988] processor LNXCPU:01: registered as cooling_device2
[    0.718982] thermal LNXTHERM:01: registered as thermal_zone0
[    0.719009] ACPI: Thermal Zone [THRM] (27 C)
[    0.724489] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.728724] brd: module loaded
[    0.730601] loop: module loaded
[    0.730897] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.732359] Fixed MDIO Bus: probed
[    0.732482] PPP generic driver version 2.4.2
[    0.732642] tun: Universal TUN/TAP device driver, 1.6
[    0.732649] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.732920] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.732998] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.733081] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.733091] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.733222] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.733271] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.733294] ehci_hcd 0000:00:1d.7: debug port 1
[    0.737187] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.737287] isapnp: Scanning for PnP cards...
[    0.786469] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58344400
[    0.834057] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.834407] usb usb1: configuration #1 chosen from 1 choice
[    0.834512] hub 1-0:1.0: USB hub found
[    0.834540] hub 1-0:1.0: 8 ports detected
[    0.834744] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.834798] uhci_hcd: USB Universal Host Controller Interface driver
[    0.834895] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.834915] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.834925] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.835056] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.835106] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
[    0.835414] usb usb2: configuration #1 chosen from 1 choice
[    0.835504] hub 2-0:1.0: USB hub found
[    0.835528] hub 2-0:1.0: 2 ports detected
[    0.835666] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.835683] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.835692] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.835821] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.835891] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
[    0.836169] usb usb3: configuration #1 chosen from 1 choice
[    0.836255] hub 3-0:1.0: USB hub found
[    0.836278] hub 3-0:1.0: 2 ports detected
[    0.836435] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.836456] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.836465] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.836580] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.836645] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
[    0.836924] usb usb4: configuration #1 chosen from 1 choice
[    0.837046] hub 4-0:1.0: USB hub found
[    0.837069] hub 4-0:1.0: 2 ports detected
[    0.837216] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.837233] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.837243] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.837356] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.837419] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
[    0.837691] usb usb5: configuration #1 chosen from 1 choice
[    0.837778] hub 5-0:1.0: USB hub found
[    0.837800] hub 5-0:1.0: 2 ports detected
[    0.838083] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.860076] Freeing initrd memory: 13969k freed
[    0.863312] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.863413] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.864549] mice: PS/2 mouse device common for all mice
[    0.866728] rtc_cmos 00:03: RTC can wake from S4
[    0.867209] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.867335] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.868422] device-mapper: uevent: version 1.0.3
[    0.869925] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.878605] device-mapper: multipath: version 1.1.0 loaded
[    0.878674] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.879169] EISA: Probing bus 0 at eisa.0
[    0.879184] Cannot allocate resource for EISA slot 1
[    0.879190] Cannot allocate resource for EISA slot 2
[    0.879196] Cannot allocate resource for EISA slot 3
[    0.879203] Cannot allocate resource for EISA slot 4
[    0.879209] Cannot allocate resource for EISA slot 5
[    0.879215] Cannot allocate resource for EISA slot 6
[    0.879234] EISA: Detected 0 cards.
[    0.879629] cpuidle: using governor ladder
[    0.879891] cpuidle: using governor menu
[    0.881380] TCP cubic registered
[    0.881894] NET: Registered protocol family 10
[    0.883184] lo: Disabled Privacy Extensions
[    0.884137] NET: Registered protocol family 17
[    0.886722] Using IPI No-Shortcut mode
[    0.887020] PM: Resume from disk failed.
[    0.887050] registered taskstats version 1
[    0.887722]   Magic number: 14:90:428
[    0.887886] rtc_cmos 00:03: setting system clock to 2010-10-07 11:24:45 UTC (1286450685)
[    0.887895] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.887900] EDD information not available.
[    0.900085] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.134290] isapnp: No Plug & Play device found
[    1.134325] Freeing unused kernel memory: 656k freed
[    1.134991] Write protecting the kernel text: 4684k
[    1.135072] Write protecting the kernel read-only data: 1840k
[    1.157105] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.179769] udev: starting version 151
[    1.436440] ACPI: Battery Slot [BAT0] (battery present)
[    1.472091] usb 1-2: configuration #1 chosen from 1 choice
[    1.513053] acpi device:27: registered as cooling_device3
[    1.513517] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.513633] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    2.038335] uvesafb: Intel Corporation, Intel(r) 82945GM Chipset Family Graphics Controller, Hardware Version 0.0, OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS, VBE v3.0
[    2.042497] uvesafb: VBIOS/hardware supports DDC2 transfers
[    2.054684] uvesafb: monitor limits: vf = 60 Hz, hf = 42 kHz, clk = 62 MHz
[    2.054793] uvesafb: scrolling: redraw
[    2.055521] uvesafb: framebuffer at 0x40000000, mapped to 0xf8080000, using 3750k, total 7872k
[    2.055529] fb0: VESA VGA frame buffer device
[    2.164133] Console: switching to colour frame buffer device 100x37
[    2.355434] Linux agpgart interface v0.103
[    2.384862] ahci 0000:00:1f.2: version 3.0
[    2.384908] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.384997]   alloc irq_desc for 28 on node -1
[    2.385005]   alloc kstat_irqs on node -1
[    2.385102] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    2.385189] ahci: SSS flag set, parallel bus scan disabled
[    2.385254] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    2.385268] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
[    2.385282] ahci 0000:00:1f.2: setting latency timer to 64
[    2.387934] scsi0 : ahci
[    2.402381] scsi1 : ahci
[    2.403428] scsi2 : ahci
[    2.403701] scsi3 : ahci
[    2.404433] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 28
[    2.404445] ata2: DUMMY
[    2.404453] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
[    2.404460] ata4: DUMMY
[    2.405516] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    2.405926] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.408882] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    2.512932] [drm] Initialized drm 1.1.0 20060810
[    2.724112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.725574] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.726034] ata1.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133
[    2.726050] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.727922] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.728462] ata1.00: configured for UDMA/133
[    2.744474] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    2.744840] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.745560] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.745708] sd 0:0:0:0: [sda] Write Protect is off
[    2.745715] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.745792] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.746195]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    2.843886] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.064111] ata3: SATA link down (SStatus 0 SControl 300)
[    3.150945] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.150957] i915 0000:00:02.0: setting latency timer to 64
[    3.164997] [drm] set up 7M of stolen space
[    3.268607] [drm] initialized overlay support
[    3.688434] fb1: inteldrmfb frame buffer device
[    3.688443] registered panic notifier
[    3.688463] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.869748] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.869768] EXT4-fs (sda6): write access will be enabled during recovery
[    4.089176] EXT4-fs (sda6): recovery complete
[    4.089860] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   19.021498] Adding 1943824k swap on /dev/sda5.  Priority:-1 extents:1 across:1943824k 
[   19.074688] udev: starting version 151
[   19.266644] lp: driver loaded but no devices found
[   19.842161] intel_rng: FWH not detected
[   19.968162] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.968188] atl1c 0000:03:00.0: setting latency timer to 64
[   20.054325] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   20.186055] cfg80211: Calling CRDA to update world regulatory domain
[   20.213368] cfg80211: World regulatory domain updated:
[   20.213378]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.213389]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.213398]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.213407]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.213416]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.213425]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.258112] Linux video capture interface: v2.00
[   20.402621] uvcvideo: Found UVC 1.00 device WebCam (064e:d101)
[   20.413408] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.413434] ath5k 0000:01:00.0: setting latency timer to 64
[   20.413527] ath5k 0000:01:00.0: registered as 'phy0'
[   20.555031] type=1505 audit(1286465105.164:2):  operation="profile_load" pid=666 name="/sbin/dhclient3"
[   20.555782] type=1505 audit(1286465105.164:3):  operation="profile_load" pid=666 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.556256] type=1505 audit(1286465105.168:4):  operation="profile_load" pid=666 name="/usr/lib/connman/scripts/dhclient-script"
[   20.567123] type=1505 audit(1286465105.176:5):  operation="profile_load" pid=674 name="/usr/sbin/ntpd"
[   20.604959] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
[   20.605113] usbcore: registered new interface driver uvcvideo
[   20.605122] USB Video Class driver (v0.1.0)
[   20.668750] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.753062] nf_conntrack version 0.5.0 (15885 buckets, 63540 max)
[   20.759041] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   20.759052] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   20.759058] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.867532] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   20.935668] ath: EEPROM regdomain: 0x65
[   20.935676] ath: EEPROM indicates we should expect a direct regpair map
[   20.935687] ath: Country alpha2 being used: 00
[   20.935692] ath: Regpair used: 0x65
[   20.978496] phy0: Selected rate control algorithm 'minstrel'
[   20.981408] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.253026] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.253308] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.340082] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   21.359037] hda_codec: ALC272: BIOS auto-probing.
[   21.360890] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   21.424191] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   21.584298] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   22.364027] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x022f000e
[   23.327898] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.344379]   alloc irq_desc for 29 on node -1
[   23.344388]   alloc kstat_irqs on node -1
[   23.344413] atl1c 0000:03:00.0: irq 29 for MSI/MSI-X
[   23.345284] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.087285] type=1505 audit(1286465108.697:6):  operation="profile_load" pid=1050 name="/usr/share/gdm/guest-session/Xsession"
[   24.092149] type=1505 audit(1286465108.701:7):  operation="profile_replace" pid=1051 name="/sbin/dhclient3"
[   24.118719] type=1505 audit(1286465108.729:8):  operation="profile_replace" pid=1051 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   24.119192] type=1505 audit(1286465108.729:9):  operation="profile_replace" pid=1051 name="/usr/lib/connman/scripts/dhclient-script"
[   24.133448] type=1505 audit(1286465108.745:10):  operation="profile_load" pid=1054 name="/usr/bin/evince"
[   24.144299] type=1505 audit(1286465108.753:11):  operation="profile_load" pid=1054 name="/usr/bin/evince-previewer"
[   24.595246] CPUFREQ: Per core ondemand sysfs interface is deprecated - ignore_nice_load
[   24.719023] ppdev: user-space parallel port driver
```

---

### Post by TBABill on 2010-10-07
Will the machine run longer if you start it from room temperature instead of an immediate reboot? This sounds like a heat sensor kicking the machine out, as stated by a previous user, and if the machine is not hot upon boot-up I wonder if it will hang in a little longer before overheating (if that's the issue)? 
 
Does it stay up long enough to get a response to typing "sensors" in a terminal? I believe you have to have lm-sensors utilities or something like that installed for it to work, but if it's already installed it could give you a temp reading before rebooting if you can get that far.
 
Does it work any longer if you try to safe boot using a vesa driver and lower resolution?

---

### Post by P4man on 2010-10-07
So its an Atom system. Probably Poulsbo (gma500) ?  Im guessing thats part of the reason, and the fact you are using BURG (in graphical mode I assume?) might explain why you have troubles even before the OS is booted. Support for that chipset isnt very good to put it mildly.

Not sure if this is much help:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by 416inversed on 2010-10-07
> **TBABill said:**
> Will the machine run longer if you start it from room temperature instead of an immediate reboot? This sounds like a heat sensor kicking the machine out, as stated by a previous user, and if the machine is not hot upon boot-up I wonder if it will hang in a little longer before overheating (if that's the issue)? 
 
Does it stay up long enough to get a response to typing "sensors" in a terminal? I believe you have to have lm-sensors utilities or something like that installed for it to work, but if it's already installed it could give you a temp reading before rebooting if you can get that far.
 
Does it work any longer if you try to safe boot using a vesa driver and lower resolution?

sensors outputs: ```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)   
```

I haven't tried safe booting yet (as I had disabled those entries in BURG)... but I'll give it a try.

---

### Post by 416inversed on 2010-10-07
> **P4man said:**
> So its an Atom system. Probably Poulsbo (gma500) ?  Im guessing thats part of the reason, and the fact you are using BURG (in graphical mode I assume?) might explain why you have troubles even before the OS is booted. Support for that chipset isnt very good to put it mildly.

Not sure if this is much help:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

EDIT: I meant to say GMA 950, full spec's here [http://support.acer.com/acerpanam/netbook/0000/Acer/AspireOneAOD250/AspireOneAOD250sp2.shtml](http://support.acer.com/acerpanam/netbook/0000/Acer/AspireOneAOD250/AspireOneAOD250sp2.shtml)

I've actually already uninstalled BURG and back to plain old boring GRUB, but I've still had reboots.

---

### Post by TBABill on 2010-10-07
...

---

### Post by P4man on 2010-10-07
Nah, definately Atom.
Googling around I see lots of success stories with this laptop and 10.04, like here:
[http://www.linlap.com/wiki/acer+aspire+one+d250](http://www.linlap.com/wiki/acer+aspire+one+d250)

Most serious issues ive seen are stuff like the microphone so Im still putting my money on a hardware issue. The harddrive perhaps? What does disk utility / smart status say about it?

---

### Post by 416inversed on 2010-10-07
So after several more reboots (including a couple in the middle of GRUB) I'm currently in XP.

Recovery mode doesn't seem to work, as that boots into a black screen that eventually just reboots the system, both in kernel -25 & -23.

I checked the HD last night from my 9.10 UNR thumb, green check marks across all the partitions.

I'll boot from the thumb again to be more precise.

---

### Post by 416inversed on 2010-10-07
I ran the self SMART test, Disk is healthy.

---

### Post by 416inversed on 2010-10-07
So it also random reboots on a 10.10RC thumb drive....

I'm growing increasingly frustrated.

To Recap:

My Acer AOD250 randomly reboots in Ubuntu (& Lubuntu) 10.04 in kernels -25 & -23, yet is stable in XP.

I've checked my RAM in Memtest86+ overnight, no errors. I flashed my BIOS. I've checked my hard drive, disk is healthy. I've checked my sensors, and it outputed +26.8°C. It occurs on both battery & on AC. I've removed BURG, but it still sometimes reboots during GRUB. Booting into recovery mode blacks out the screen, then reboots.

What now?

---

### Post by 416inversed on 2010-10-10
Bump? 

Not to jinx myself, but Failsafe GNOME seems to be stable.

EDIT: Yeah, I spoke too soon. It too rebooted.

Any ideas?

---

### Post by JohnRingo on 2010-10-11
I had a similar issue and it was a power supply.

---

### Post by 416inversed on 2010-10-11
Any way to diagnose a bad power supply?

My warranty literally ends in 4 days, so if it is a hardware issue, I need to act fast.

XP doesn't seem to be affected.

---

### Post by P4man on 2010-10-11
bad PSU is common cause on desktops, but on a laptop like here, it shouldnt matter, since there is a battery.

The only thing I can think off that you havent tried yet is a reinstall.

---

