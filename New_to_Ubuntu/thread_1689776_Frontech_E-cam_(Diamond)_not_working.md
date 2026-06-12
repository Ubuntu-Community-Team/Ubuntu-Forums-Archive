---
title: "Frontech E-cam (Diamond) not working"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by idom on 2011-02-17
Hi

I am running  10.04 LTS - the Lucid Lynx since last 6-8 months and just bought a webcame
Frontech E-Cam (Diamond)
Make JIL -2232 
and it is not working

I typed gstreamer-properties in terminal 
click video try v4l1 and v4l2
click the bottom test button for each 1
it gave following error  
 Cannot identify device '/dev/video0'


Terminal output is as follows 

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline3/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src2:
system error: No such file or directory]

---

### Post by no2498 on 2011-02-17
type this dmesg in a terminal click enter

after that type lsusb click enter

---

### Post by idom on 2011-02-17
> **no2498 said:**
> type this dmesg in a terminal click enter

after that type lsusb click enter

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0c45:612f Microdia PC Camera (SN9C110)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg gave a very long output 

I do not know what both them do ?

first part is 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-27-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 (Ubuntu 2.6.32-27.49-generic 2.6.32.26+drm33.12)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007c912000 (usable)
[    0.000000]  BIOS-e820: 000000007c912000 - 000000007c934000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007c934000 - 000000007ca46000 (reserved)
[    0.000000]  BIOS-e820: 000000007ca46000 - 000000007ca5a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ca5a000 - 000000007cb59000 (reserved)
[    0.000000]  BIOS-e820: 000000007cb59000 - 000000007cb5a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007cb5a000 - 000000007cb62000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007cb62000 - 000000007cb6c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007cb6c000 - 000000007cb8a000 (reserved)
[    0.000000]  BIOS-e820: 000000007cb8a000 - 000000007cb90000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007cb90000 - 000000007cd00000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7cd00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07CD00000 mask FFFF00000 write-through
[    0.000000]   2 base 07CE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07D000000 mask FFF000000 uncachable
[    0.000000]   4 base 07E000000 mask FFE000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007c912000 (usable)
[    0.000000]  modified: 000000007c912000 - 000000007c934000 (ACPI NVS)
[    0.000000]  modified: 000000007c934000 - 000000007ca46000 (reserved)
[    0.000000]  modified: 000000007ca46000 - 000000007ca5a000 (ACPI NVS)
[    0.000000]  modified: 000000007ca5a000 - 000000007cb59000 (reserved)
[    0.000000]  modified: 000000007cb59000 - 000000007cb5a000 (ACPI NVS)
[    0.000000]  modified: 000000007cb5a000 - 000000007cb62000 (ACPI data)
[    0.000000]  modified: 000000007cb62000 - 000000007cb6c000 (ACPI NVS)
[    0.000000]  modified: 000000007cb6c000 - 000000007cb8a000 (reserved)
[    0.000000]  modified: 000000007cb8a000 - 000000007cb90000 (ACPI NVS)
[    0.000000]  modified: 000000007cb90000 - 000000007cd00000 (usable)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37854000 - 37fef491
[    0.000000] Allocated new RAMDISK: 008e1000 - 0107c491
[    0.000000] Move RAMDISK from 0000000037854000 - 0000000037fef490 to 008e1000 - 0107c490
[    0.000000] ACPI: RSDP 000f03c0 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 7cb60e18 0004C (v01 INTEL  DG45ID   00000061 MSFT 00010013)
[    0.000000] ACPI: FACP 7cb5fd98 000F4 (v04  INTEL    A M I 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20090903/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 7CB63F40/000000007CB69E40, using 32 (20090903/tbfadt-486)
[    0.000000] ACPI: DSDT 7cb5a018 04923 (v01 INTEL  DG45ID   00000061 INTL 20051117)
[    0.000000] ACPI: FACS 7cb63f40 00040
[    0.000000] ACPI: APIC 7cb5ff18 0006C (v02 INTEL  DG45ID   00000061 MSFT 00010013)
[    0.000000] ACPI: MCFG 7cb6ad98 0003C (v01 INTEL  DG45ID   00000061 MSFT 00000097)
[    0.000000] ACPI: ASF! 7cb69c18 000A0 (v32 INTEL  DG45ID   00000061 TFSM 000F4240)
[    0.000000] ACPI: SPCR 7cb6ac98 00050 (v01 INTEL  DG45ID   00000061 AMI. 00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1109MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e019c]              BRK ==> [00008dd000 - 00008e019c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e1000 - 000107c491]      NEW RAMDISK ==> [00008e1000 - 000107c491]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007cd00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007c912
[    0.000000]     0: 0x0007cb90 -> 0x0007cd00
[    0.000000] On node 0 totalpages: 510481

---

### Post by idom on 2011-02-17
dmesg outputs is arranged in files and attached.

other two files will be attached in next reply

---

### Post by idom on 2011-02-17
the other two files are attached 
dmesg outputs was 700 hundred lines long I split it according to line numbers an put int files.

idom

---

### Post by no2498 on 2011-02-17
this does not look good

sonixj	0c45:612f	Microdia	sn9c110 icm105 	not coded

from this page im not sure its up to date tho

[http://www.danielogawa.com/webcam.html](http://www.danielogawa.com/webcam.html)

---

### Post by no2498 on 2011-02-17
you on a lap top
if yes try clicking fn+f2 at the same time then run dmesg in a terminal
do not post it
just see if it finds your cam

---

### Post by idom on 2011-02-17
> **no2498 said:**
> you on a lap top
if yes try clicking fn+f2 at the same time then run dmesg in a terminal
do not post it
just see if it finds your cam

I am not on laptop.
It is quad core desktop.

So now what am I supposed to do?
do I need to update my system? I have not updated it since last month or two ? 

idom

---

### Post by no2498 on 2011-02-18
see if this helps you 
[http://handsley.com/USB_devices_in_Linux](http://handsley.com/USB_devices_in_Linux)

---

### Post by idom on 2011-02-18
> **no2498 said:**
> see if this helps you 
[http://handsley.com/USB_devices_in_Linux](http://handsley.com/USB_devices_in_Linux)

I am out of town for a few days.
I will try this out and see.
Thanks .

idom

---

### Post by rajeev1204 on 2011-02-18
Hi

I would advice you to stay away from frontech brand as much as you can.Their quality is suspect.But you can check here to see  if your microdia chip inside the cam is supported.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)


I had a tv tuner which i returned as it would be a pain to run on linux.

---

### Post by idom on 2011-02-26
> **idom said:**
> I am out of town for a few days.
I will try this out and see.
Thanks .

idom

unable to run this 
Installing drivers

Check Linux kernel version

 [root@localhost ~]# uname -r


Ensure that you have the kernel source before proceeding, you can install it with yum.

 [root@localhost ~]# yum install kernel-source-'uname -r'
 OR
 [root@localhost ~]# yum install kernel-source


Usually the build script of the downloaded tar file would include the process of loading the driver. If it does not you can load the driver file manually. The .ko file is the compiled driver.

[root@localhost]# insmod driver_name.ko


[edit]

---

