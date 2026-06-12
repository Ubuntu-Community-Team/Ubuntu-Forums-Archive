---
title: "Lost in the maintenance shell"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by seattle vic on 2010-03-27
I've been using 10.04 for about 5 days and today it booted up to the login screen, where I log in with my password, and it immediately goes to the maintenance shell.

Yes, I know it's a development issue, but I've had it happen in 9.10 as well.

What I'd like some help on is how did I get in there and how can I get it to return to the normal boot up process.

I've checked the X server log and the dmesg log for clues, but can't find any.  The boot log in /var/logs/boot apparently has been disabled for some time in software (I tried to enable it).

How can I find out why I got into the shell?

Thanks in advance.

---

### Post by duanedesign on 2010-03-27
Do you have any NFS mounts?

Is your /home using LVM?

Are any of your partitions encrypted?

Also try running fsck on next boot. You can do that with the following:

```
sudo touch /forcefsck
```

```
shutdown -r now
```

---

### Post by ibuclaw on 2010-03-27
Attaching the contents of /var/log/messages may most likely help, as there may be more eagle eyed people in here to spot problems. :)

Most common causes of maintenance shell are:
[LIST=1]
[*]Waiting for root filesystem to mount timeout
[*]Auto fsck failed.
[/LIST]

Typical things to run/check are:
[LIST=1]
[*]Manually run fsck on the root partition / affected partititons (ie: without the -a or -p switch).
[*]Ensure the contents of /etc/fstab is correct
[/LIST]

Regards
Iain

---

### Post by seattle vic on 2010-03-27
Guys, thanks for the responses.  Here's the story so far:

Do you have any NFS mounts?  ***I had one, but commented it out***

Is your /home using LVM?  ***I have no experience with LVM, but I think the answer is no.***

Are any of your partitions encrypted?  [B][I]No.
[/I][/B]
Also try running fsck on next boot. You can do that with the following:

Code:

sudo touch /forcefsck

Code:

shutdown -r now

[B][I]Did that with no errors.
[/I][/B]

I used a 9.1 boot CD (live) and ran fsck on the unmounted partition with no errors.

I checked xorg.conf for errors (none that I could see) and then just deleted in to see if it would make a difference.  No change.

I taught myself how to connect to wireless from the maint shell (not easy, but shutting down netowrk-manager seemed to be the key) and upgraded all my packages, also used apt-get dist-upgrade.  No change.

I checked the fstab file and it seemed to be OK; same as I'd used for 9.10 before I upgraded to 10.04.  I then ran mount -a and posted the results here.  There are a bunch of items that show "none on..." but I'm not smart enough to know if that's normal.

Below are the fstab file and results from mount -a.  I've also included the last boot up messages from /var/log/messages:

If anybody can see a clue here, I'd *love* to know it, thanks.

=====================================================
/etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=46d16122-2709-436f-9a46-4eee52f7a410 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e853933f-5373-4f45-b1f3-e0f95f28985f none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#Entry for the Vista OS on the 1st drive, which I think should be sda1

#/dev/sda1	/media/vista	 ntfs-3g defaults,locale=en_US.utf8 0 0

=============================================
output of mount -a:

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
============================================
/var/log/messages:

Mar 27 19:16:03 laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Mar 27 19:16:03 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] (re)start
Mar 27 19:16:03 laptop rsyslogd: rsyslogd's groupid changed to 102
Mar 27 19:16:03 laptop rsyslogd: rsyslogd's userid changed to 101
Mar 27 19:16:03 laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 27 19:16:03 laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 27 19:16:03 laptop kernel: [    0.000000] Linux version 2.6.32-17-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-3ubuntu3) ) #26-Ubuntu SMP Sat Mar 20 02:23:45 UTC 2010 (Ubuntu 2.6.32-17.26-generic 2.6.32.10+drm33.1)
Mar 27 19:16:03 laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-17-generic root=UUID=46d16122-2709-436f-9a46-4eee52f7a410 ro pci=use_crs quiet splash
Mar 27 19:16:03 laptop kernel: [    0.000000] KERNEL supported cpus:
Mar 27 19:16:03 laptop kernel: [    0.000000]   Intel GenuineIntel
Mar 27 19:16:03 laptop kernel: [    0.000000]   AMD AuthenticAMD
Mar 27 19:16:03 laptop kernel: [    0.000000]   Centaur CentaurHauls
Mar 27 19:16:03 laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000000e1000 - 0000000000100000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e800 (ACPI data)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000bff8e800 - 00000000bffe0000 (ACPI NVS)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000] DMI 2.5 present.
Mar 27 19:16:03 laptop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Mar 27 19:16:03 laptop kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Mar 27 19:16:03 laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 27 19:16:03 laptop kernel: [    0.000000] last_pfn = 0xbff80 max_arch_pfn = 0x400000000
Mar 27 19:16:03 laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Mar 27 19:16:03 laptop kernel: [    0.000000] modified physical RAM map:
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000000e1000 - 0000000000100000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bff80000 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000bff80000 - 00000000bff8e800 (ACPI data)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000bff8e800 - 00000000bffe0000 (ACPI NVS)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Mar 27 19:16:03 laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Mar 27 19:16:03 laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bff80000
Mar 27 19:16:03 laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Mar 27 19:16:03 laptop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Mar 27 19:16:03 laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Mar 27 19:16:03 laptop kernel: [    0.000000] RAMDISK: 37820000 - 37fef4e1
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: RSDP 00000000000f9390 00024 (v02 ACPIAM)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: XSDT 00000000bff80100 0007C (v01 _ASUS_ Notebook 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: FACP 00000000bff80290 000F4 (v03 072208 FACP2022 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: DSDT 00000000bff80680 0BD76 (v01  M70Vx M70Vx207 00000207 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: FACS 00000000bff8e800 00040
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: APIC 00000000bff80390 0005C (v01 072208 APIC2022 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: MCFG 00000000bff80430 0003C (v01 072208 OEMMCFG  20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: SLIC 00000000bff80470 00176 (v01 _ASUS_ Notebook 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: ECDT 00000000bff80620 00054 (v01 072208 OEMECDT  20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: DBGP 00000000bff803f0 00034 (v01 072208 DBGP2022 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: BOOT 00000000bff805f0 00028 (v01 072208 BOOT2022 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: OEMB 00000000bff8e840 00071 (v01 072208 OEMB2022 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: HPET 00000000bff8c400 00038 (v01 072208 OEMHPET  20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: ATKG 00000000bff8eac0 08024 (v01 072208  OEMATKG 20080722 MSFT 00000097)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: SSDT 00000000bff97610 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.000000] No NUMA configuration found
Mar 27 19:16:03 laptop kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Mar 27 19:16:03 laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Mar 27 19:16:03 laptop kernel: [    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
Mar 27 19:16:03 laptop kernel: [    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
Mar 27 19:16:03 laptop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #2 [0001000000 - 0001a27e64]    TEXT DATA BSS ==> [0001000000 - 0001a27e64]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #3 [0037820000 - 0037fef4e1]          RAMDISK ==> [0037820000 - 0037fef4e1]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #5 [0001a28000 - 0001a28292]              BRK ==> [0001a28000 - 0001a28292]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Mar 27 19:16:03 laptop kernel: [    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
Mar 27 19:16:03 laptop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Mar 27 19:16:03 laptop kernel: [    0.000000] Zone PFN ranges:
Mar 27 19:16:03 laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 27 19:16:03 laptop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar 27 19:16:03 laptop kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Mar 27 19:16:03 laptop kernel: [    0.000000] Movable zone start PFN for each node
Mar 27 19:16:03 laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Mar 27 19:16:03 laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Mar 27 19:16:03 laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bff80
Mar 27 19:16:03 laptop kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 27 19:16:03 laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 27 19:16:03 laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 27 19:16:03 laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Mar 27 19:16:03 laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bff80000 - 00000000bff8e000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bff8e000 - 00000000bff8f000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bff8f000 - 00000000bffe0000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Mar 27 19:16:03 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Mar 27 19:16:03 laptop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Mar 27 19:16:03 laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar 27 19:16:03 laptop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Mar 27 19:16:03 laptop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91480 r8192 d23208 u1048576
Mar 27 19:16:03 laptop kernel: [    0.000000] pcpu-alloc: s91480 r8192 d23208 u1048576 alloc=1*2097152
Mar 27 19:16:03 laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Mar 27 19:16:03 laptop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030310
Mar 27 19:16:03 laptop kernel: [    0.000000] Policy zone: Normal
Mar 27 19:16:03 laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-17-generic root=UUID=46d16122-2709-436f-9a46-4eee52f7a410 ro pci=use_crs quiet splash
Mar 27 19:16:03 laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Mar 27 19:16:03 laptop kernel: [    0.000000] Initializing CPU#0
Mar 27 19:16:03 laptop kernel: [    0.000000] Checking aperture...
Mar 27 19:16:03 laptop kernel: [    0.000000] No AGP bridge found
Mar 27 19:16:03 laptop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Mar 27 19:16:03 laptop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Mar 27 19:16:03 laptop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Mar 27 19:16:03 laptop kernel: [    0.000000] Memory: 4051152k/5242880k available (5407k kernel code, 1049544k absent, 142184k reserved, 2970k data, 876k init)
Mar 27 19:16:03 laptop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar 27 19:16:03 laptop kernel: [    0.000000] Hierarchical RCU implementation.
Mar 27 19:16:03 laptop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Mar 27 19:16:03 laptop kernel: [    0.000000] Extended CMOS year: 2000
Mar 27 19:16:03 laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Mar 27 19:16:03 laptop kernel: [    0.000000] console [tty0] enabled
Mar 27 19:16:03 laptop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Mar 27 19:16:03 laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 27 19:16:03 laptop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Mar 27 19:16:03 laptop kernel: [    0.000000] Fast TSC calibration using PIT
Mar 27 19:16:03 laptop kernel: [    0.000000] Detected 2527.307 MHz processor.
Mar 27 19:16:03 laptop kernel: [    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.61 BogoMIPS (lpj=25273070)
Mar 27 19:16:03 laptop kernel: [    0.010033] Security Framework initialized
Mar 27 19:16:03 laptop kernel: [    0.010052] AppArmor: AppArmor initialized
Mar 27 19:16:03 laptop kernel: [    0.010384] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Mar 27 19:16:03 laptop kernel: [    0.012482] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar 27 19:16:03 laptop kernel: [    0.013459] Mount-cache hash table entries: 256
Mar 27 19:16:03 laptop kernel: [    0.013592] Initializing cgroup subsys ns
Mar 27 19:16:03 laptop kernel: [    0.013598] Initializing cgroup subsys cpuacct
Mar 27 19:16:03 laptop kernel: [    0.013601] Initializing cgroup subsys memory
Mar 27 19:16:03 laptop kernel: [    0.013608] Initializing cgroup subsys devices
Mar 27 19:16:03 laptop kernel: [    0.013610] Initializing cgroup subsys freezer
Mar 27 19:16:03 laptop kernel: [    0.013612] Initializing cgroup subsys net_cls
Mar 27 19:16:03 laptop kernel: [    0.013631] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 27 19:16:03 laptop kernel: [    0.013633] CPU: L2 cache: 6144K
Mar 27 19:16:03 laptop kernel: [    0.013636] CPU 0/0x0 -> Node 0
Mar 27 19:16:03 laptop kernel: [    0.013638] CPU: Physical Processor ID: 0
Mar 27 19:16:03 laptop kernel: [    0.013640] CPU: Processor Core ID: 0
Mar 27 19:16:03 laptop kernel: [    0.013642] mce: CPU supports 6 MCE banks
Mar 27 19:16:03 laptop kernel: [    0.013653] using mwait in idle threads.
Mar 27 19:16:03 laptop kernel: [    0.013654] Performance Events: Core2 events, Intel PMU driver.
Mar 27 19:16:03 laptop kernel: [    0.013660] ... version:                2
Mar 27 19:16:03 laptop kernel: [    0.013661] ... bit width:              40
Mar 27 19:16:03 laptop kernel: [    0.013663] ... generic registers:      2
Mar 27 19:16:03 laptop kernel: [    0.013664] ... value mask:             000000ffffffffff
Mar 27 19:16:03 laptop kernel: [    0.013665] ... max period:             000000007fffffff
Mar 27 19:16:03 laptop kernel: [    0.013667] ... fixed-purpose events:   3
Mar 27 19:16:03 laptop kernel: [    0.013668] ... event mask:             0000000700000003
Mar 27 19:16:03 laptop kernel: [    0.016759] ACPI: Core revision 20090903
Mar 27 19:16:03 laptop kernel: [    0.040007] ftrace: converting mcount calls to 0f 1f 44 00 00
Mar 27 19:16:03 laptop kernel: [    0.040012] ftrace: allocating 22512 entries in 89 pages
Mar 27 19:16:03 laptop kernel: [    0.058567] Setting APIC routing to flat
Mar 27 19:16:03 laptop kernel: [    0.058910] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 27 19:16:03 laptop kernel: [    0.158369] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
Mar 27 19:16:03 laptop kernel: [    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
Mar 27 19:16:03 laptop kernel: [    0.020000] Initializing CPU#1
Mar 27 19:16:03 laptop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 27 19:16:03 laptop kernel: [    0.020000] CPU: L2 cache: 6144K
Mar 27 19:16:03 laptop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Mar 27 19:16:03 laptop kernel: [    0.020000] CPU: Physical Processor ID: 0
Mar 27 19:16:03 laptop kernel: [    0.020000] CPU: Processor Core ID: 1
Mar 27 19:16:03 laptop kernel: [    0.310029] CPU1: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
Mar 27 19:16:03 laptop kernel: [    0.310036] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 27 19:16:03 laptop kernel: [    0.320016] Brought up 2 CPUs
Mar 27 19:16:03 laptop kernel: [    0.320018] Total of 2 processors activated (10109.21 BogoMIPS).
Mar 27 19:16:03 laptop kernel: [    0.321078] devtmpfs: initialized
Mar 27 19:16:03 laptop kernel: [    0.321354] regulator: core version 0.5
Mar 27 19:16:03 laptop kernel: [    0.321381] Time: 19:15:51  Date: 03/27/10
Mar 27 19:16:03 laptop kernel: [    0.321417] NET: Registered protocol family 16
Mar 27 19:16:03 laptop kernel: [    0.321519] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Mar 27 19:16:03 laptop kernel: [    0.321521] ACPI: bus type pci registered
Mar 27 19:16:03 laptop kernel: [    0.321583] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 27 19:16:03 laptop kernel: [    0.321585] PCI: Not using MMCONFIG.
Mar 27 19:16:03 laptop kernel: [    0.321586] PCI: Using configuration type 1 for base access
Mar 27 19:16:03 laptop kernel: [    0.322285] Trying to unpack rootfs image as initramfs...
Mar 27 19:16:03 laptop kernel: [    0.330110] bio: create slab <bio-0> at 0
Mar 27 19:16:03 laptop kernel: [    0.351323] ACPI: EC: EC description table is found, configuring boot EC
Mar 27 19:16:03 laptop kernel: [    0.352595] ACPI: Executed 1 blocks of module-level executable AML code
Mar 27 19:16:03 laptop kernel: [    0.355517] ACPI: BIOS _OSI(Linux) query ignored
Mar 27 19:16:03 laptop kernel: [    0.372406] ACPI: Interpreter enabled
Mar 27 19:16:03 laptop kernel: [    0.372410] ACPI: (supports S0 S3 S4 S5)
Mar 27 19:16:03 laptop kernel: [    0.372432] ACPI: Using IOAPIC for interrupt routing
Mar 27 19:16:03 laptop kernel: [    0.372521] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 27 19:16:03 laptop kernel: [    0.375750] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Mar 27 19:16:03 laptop kernel: [    0.382867] PCI: Using MMCONFIG at e0000000 - efffffff
Mar 27 19:16:03 laptop kernel: [    0.392505] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
Mar 27 19:16:03 laptop kernel: [    0.395256] ACPI Warning: Incorrect checksum in table [ATKG] - 64, should be D7 (20090903/tbutils-314)
Mar 27 19:16:03 laptop kernel: [    0.395472] ACPI: No dock devices found.
Mar 27 19:16:03 laptop kernel: [    0.395969] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 27 19:16:03 laptop kernel: [    0.396347] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.396350] pci 0000:00:01.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.396817] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.396821] pci 0000:00:1a.7: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.396942] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.396947] pci 0000:00:1b.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.397040] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.397045] pci 0000:00:1c.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.397142] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.397147] pci 0000:00:1c.1: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.397245] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.397249] pci 0000:00:1c.2: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.397348] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.397352] pci 0000:00:1c.5: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.397797] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.397802] pci 0000:00:1d.7: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.398145] pci 0000:00:1f.2: PME# supported from D3hot
Mar 27 19:16:03 laptop kernel: [    0.398149] pci 0000:00:1f.2: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.398817] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.398831] pci 0000:03:00.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.399481] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.399495] pci 0000:06:00.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.399757] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.399761] pci 0000:07:01.0: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.399863] pci 0000:07:01.1: PME# supported from D0 D1 D2 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.399867] pci 0000:07:01.1: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.399968] pci 0000:07:01.2: PME# supported from D0 D1 D2 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.399972] pci 0000:07:01.2: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.400082] pci 0000:07:01.3: PME# supported from D0 D1 D2 D3hot D3cold
Mar 27 19:16:03 laptop kernel: [    0.400087] pci 0000:07:01.3: PME# disabled
Mar 27 19:16:03 laptop kernel: [    0.400150] pci 0000:00:1e.0: transparent bridge
Mar 27 19:16:03 laptop kernel: [    0.421157] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
Mar 27 19:16:03 laptop kernel: [    0.421290] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
Mar 27 19:16:03 laptop kernel: [    0.421420] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
Mar 27 19:16:03 laptop kernel: [    0.421548] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
Mar 27 19:16:03 laptop kernel: [    0.421677] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
Mar 27 19:16:03 laptop kernel: [    0.421806] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
Mar 27 19:16:03 laptop kernel: [    0.421936] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
Mar 27 19:16:03 laptop kernel: [    0.422065] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
Mar 27 19:16:03 laptop kernel: [    0.422215] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Mar 27 19:16:03 laptop kernel: [    0.422220] vgaarb: loaded
Mar 27 19:16:03 laptop kernel: [    0.422330] SCSI subsystem initialized
Mar 27 19:16:03 laptop kernel: [    0.430088] usbcore: registered new interface driver usbfs
Mar 27 19:16:03 laptop kernel: [    0.430099] usbcore: registered new interface driver hub
Mar 27 19:16:03 laptop kernel: [    0.430121] usbcore: registered new device driver usb
Mar 27 19:16:03 laptop kernel: [    0.430243] ACPI: WMI: Mapper loaded
Mar 27 19:16:03 laptop kernel: [    0.430245] PCI: Using ACPI for IRQ routing
Mar 27 19:16:03 laptop kernel: [    0.430509] NetLabel: Initializing
Mar 27 19:16:03 laptop kernel: [    0.430511] NetLabel:  domain hash size = 128
Mar 27 19:16:03 laptop kernel: [    0.430512] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 27 19:16:03 laptop kernel: [    0.430526] NetLabel:  unlabeled traffic allowed by default
Mar 27 19:16:03 laptop kernel: [    0.430557] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 27 19:16:03 laptop kernel: [    0.430562] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Mar 27 19:16:03 laptop kernel: [    0.440130] Switching to clocksource tsc
Mar 27 19:16:03 laptop kernel: [    0.441607] AppArmor: AppArmor Filesystem Enabled
Mar 27 19:16:03 laptop kernel: [    0.441618] pnp: PnP ACPI init
Mar 27 19:16:03 laptop kernel: [    0.441629] ACPI: bus type pnp registered
Mar 27 19:16:03 laptop kernel: [    0.444321] pnp: PnP ACPI: found 16 devices
Mar 27 19:16:03 laptop kernel: [    0.444323] ACPI: ACPI bus type pnp unregistered
Mar 27 19:16:03 laptop kernel: [    0.444333] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444340] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444343] system 00:08: ioport range 0x800-0x87f has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444345] system 00:08: ioport range 0x400-0x41f has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444347] system 00:08: ioport range 0x500-0x57f has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444350] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444352] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444355] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444357] system 00:08: iomem range 0xfed90000-0xfed90fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444360] system 00:08: iomem range 0xfed91000-0xfed91fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444362] system 00:08: iomem range 0xfed92000-0xfed92fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444365] system 00:08: iomem range 0xfed93000-0xfed93fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444367] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444370] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444375] system 00:0a: iomem range 0xffa00000-0xffbfffff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.444378] system 00:0a: iomem range 0xffe00000-0xffffffff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.444386] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444390] system 00:0c: ioport range 0x250-0x253 has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444393] system 00:0c: ioport range 0x256-0x25f has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444395] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.444398] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444400] system 00:0c: iomem range 0xfec10000-0xfec17fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444405] system 00:0c: iomem range 0xfec18000-0xfec1ffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444407] system 00:0c: iomem range 0xfec20000-0xfec27fff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444410] system 00:0c: iomem range 0xfec38000-0xfec3ffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444415] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444420] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.444422] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
Mar 27 19:16:03 laptop kernel: [    0.444424] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.444427] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
Mar 27 19:16:03 laptop kernel: [    0.449173] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Mar 27 19:16:03 laptop kernel: [    0.449176] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Mar 27 19:16:03 laptop kernel: [    0.449179] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
Mar 27 19:16:03 laptop kernel: [    0.449182] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Mar 27 19:16:03 laptop kernel: [    0.449186] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Mar 27 19:16:03 laptop kernel: [    0.449188] pci 0000:00:1c.0:   IO window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449193] pci 0000:00:1c.0:   MEM window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449197] pci 0000:00:1c.0:   PREFETCH window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449205] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Mar 27 19:16:03 laptop kernel: [    0.449207] pci 0000:00:1c.1:   IO window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449213] pci 0000:00:1c.1:   MEM window: 0xfdf00000-0xfdffffff
Mar 27 19:16:03 laptop kernel: [    0.449217] pci 0000:00:1c.1:   PREFETCH window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449224] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Mar 27 19:16:03 laptop kernel: [    0.449227] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
Mar 27 19:16:03 laptop kernel: [    0.449233] pci 0000:00:1c.2:   MEM window: 0xfe000000-0xfe9fffff
Mar 27 19:16:03 laptop kernel: [    0.449238] pci 0000:00:1c.2:   PREFETCH window: 0x000000f6000000-0x000000f8efffff
Mar 27 19:16:03 laptop kernel: [    0.449246] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
Mar 27 19:16:03 laptop kernel: [    0.449249] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Mar 27 19:16:03 laptop kernel: [    0.449255] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
Mar 27 19:16:03 laptop kernel: [    0.449260] pci 0000:00:1c.5:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
Mar 27 19:16:03 laptop kernel: [    0.449268] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Mar 27 19:16:03 laptop kernel: [    0.449269] pci 0000:00:1e.0:   IO window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449275] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
Mar 27 19:16:03 laptop kernel: [    0.449280] pci 0000:00:1e.0:   PREFETCH window: disabled
Mar 27 19:16:03 laptop kernel: [    0.449303] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 19:16:03 laptop kernel: [    0.449316] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 19:16:03 laptop kernel: [    0.449334] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 27 19:16:03 laptop kernel: [    0.449352] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 27 19:16:03 laptop kernel: [    0.449367] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 27 19:16:03 laptop kernel: [    0.449453] NET: Registered protocol family 2
Mar 27 19:16:03 laptop kernel: [    0.449607] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 27 19:16:03 laptop kernel: [    0.450711] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Mar 27 19:16:03 laptop kernel: [    0.454648] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar 27 19:16:03 laptop kernel: [    0.455182] TCP: Hash tables configured (established 524288 bind 65536)
Mar 27 19:16:03 laptop kernel: [    0.455185] TCP reno registered
Mar 27 19:16:03 laptop kernel: [    0.455304] NET: Registered protocol family 1
Mar 27 19:16:03 laptop kernel: [    0.455578] Simple Boot Flag at 0x51 set to 0x1
Mar 27 19:16:03 laptop kernel: [    0.455759] Scanning for low memory corruption every 60 seconds
Mar 27 19:16:03 laptop kernel: [    0.455881] audit: initializing netlink socket (disabled)
Mar 27 19:16:03 laptop kernel: [    0.455895] type=2000 audit(1269717351.449:1): initialized
Mar 27 19:16:03 laptop kernel: [    0.464459] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 27 19:16:03 laptop kernel: [    0.465639] VFS: Disk quotas dquot_6.5.2
Mar 27 19:16:03 laptop kernel: [    0.465682] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar 27 19:16:03 laptop kernel: [    0.466194] fuse init (API version 7.13)
Mar 27 19:16:03 laptop kernel: [    0.466269] msgmni has been set to 7912
Mar 27 19:16:03 laptop kernel: [    0.466441] alg: No test for stdrng (krng)
Mar 27 19:16:03 laptop kernel: [    0.466490] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Mar 27 19:16:03 laptop kernel: [    0.466493] io scheduler noop registered
Mar 27 19:16:03 laptop kernel: [    0.466495] io scheduler anticipatory registered
Mar 27 19:16:03 laptop kernel: [    0.466496] io scheduler deadline registered
Mar 27 19:16:03 laptop kernel: [    0.466528] io scheduler cfq registered (default)
Mar 27 19:16:03 laptop kernel: [    0.467376] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 27 19:16:03 laptop kernel: [    0.467708] pciehp 0000:00:01.0:pcie04: HPC vendor_id 8086 device_id 2a41 ss_vid 0 ss_did 0
Mar 27 19:16:03 laptop kernel: [    0.467760] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
Mar 27 19:16:03 laptop kernel: [    0.467802] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 27 19:16:03 laptop kernel: [    0.467942] ACPI: AC Adapter [AC0] (on-line)
Mar 27 19:16:03 laptop kernel: [    0.468011] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Mar 27 19:16:03 laptop kernel: [    0.468020] ACPI: Sleep Button [SLPB]
Mar 27 19:16:03 laptop kernel: [    0.468054] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Mar 27 19:16:03 laptop kernel: [    0.470207] ACPI: Lid Switch [LID]
Mar 27 19:16:03 laptop kernel: [    0.470244] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 27 19:16:03 laptop kernel: [    0.470247] ACPI: Power Button [PWRF]
Mar 27 19:16:03 laptop kernel: [    0.471025] ACPI: SSDT 00000000bff96bc0 00248 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.471584] ACPI: SSDT 00000000bff96ea0 00765 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.472290] Marking TSC unstable due to TSC halts in idle
Mar 27 19:16:03 laptop kernel: [    0.472333] processor LNXCPU:00: registered as cooling_device0
Mar 27 19:16:03 laptop kernel: [    0.472691] ACPI: SSDT 00000000bff96af0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.473058] ACPI: SSDT 00000000bff96e10 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Mar 27 19:16:03 laptop kernel: [    0.473403] Switching to clocksource hpet
Mar 27 19:16:03 laptop kernel: [    0.479752] processor LNXCPU:01: registered as cooling_device1
Mar 27 19:16:03 laptop kernel: [    0.486762] ACPI Warning for \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found Processor, expected Reference (20090903/nspredef-1012)
Mar 27 19:16:03 laptop kernel: [    0.486770] ACPI: Invalid passive threshold
Mar 27 19:16:03 laptop kernel: [    0.487239] thermal LNXTHERM:01: registered as thermal_zone0
Mar 27 19:16:03 laptop kernel: [    0.487246] ACPI: Thermal Zone [THRM] (56 C)
Mar 27 19:16:03 laptop kernel: [    0.488529] Linux agpgart interface v0.103
Mar 27 19:16:03 laptop kernel: [    0.488564] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Mar 27 19:16:03 laptop kernel: [    0.489718] brd: module loaded
Mar 27 19:16:03 laptop kernel: [    0.490138] loop: module loaded
Mar 27 19:16:03 laptop kernel: [    0.490207] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Mar 27 19:16:03 laptop kernel: [    0.490555] Fixed MDIO Bus: probed
Mar 27 19:16:03 laptop kernel: [    0.490581] PPP generic driver version 2.4.2
Mar 27 19:16:03 laptop kernel: [    0.490606] tun: Universal TUN/TAP device driver, 1.6
Mar 27 19:16:03 laptop kernel: [    0.490608] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar 27 19:16:03 laptop kernel: [    0.490676] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 27 19:16:03 laptop kernel: [    0.490699] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 27 19:16:03 laptop kernel: [    0.490717] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.490747] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Mar 27 19:16:03 laptop kernel: [    0.490778] ehci_hcd 0000:00:1a.7: debug port 1
Mar 27 19:16:03 laptop kernel: [    0.494667] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Mar 27 19:16:03 laptop kernel: [    0.503242] Freeing initrd memory: 7997k freed
Mar 27 19:16:03 laptop kernel: [    0.520031] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Mar 27 19:16:03 laptop kernel: [    0.520224] usb usb1: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.520250] hub 1-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.520259] hub 1-0:1.0: 6 ports detected
Mar 27 19:16:03 laptop kernel: [    0.520399] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 27 19:16:03 laptop kernel: [    0.520435] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.520473] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Mar 27 19:16:03 laptop kernel: [    0.520554] ehci_hcd 0000:00:1d.7: debug port 1
Mar 27 19:16:03 laptop kernel: [    0.524470] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
Mar 27 19:16:03 laptop kernel: [    0.536154] ACPI: Battery Slot [BAT0] (battery present)
Mar 27 19:16:03 laptop kernel: [    0.550013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Mar 27 19:16:03 laptop kernel: [    0.550069] usb usb2: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.550090] hub 2-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.550096] hub 2-0:1.0: 6 ports detected
Mar 27 19:16:03 laptop kernel: [    0.550153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 27 19:16:03 laptop kernel: [    0.550170] uhci_hcd: USB Universal Host Controller Interface driver
Mar 27 19:16:03 laptop kernel: [    0.550206] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 19:16:03 laptop kernel: [    0.550216] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.550242] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Mar 27 19:16:03 laptop kernel: [    0.550275] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
Mar 27 19:16:03 laptop kernel: [    0.550354] usb usb3: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.550377] hub 3-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.550383] hub 3-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.550427] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 27 19:16:03 laptop kernel: [    0.550436] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.550461] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Mar 27 19:16:03 laptop kernel: [    0.550493] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Mar 27 19:16:03 laptop kernel: [    0.550568] usb usb4: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.550594] hub 4-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.550600] hub 4-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.550644] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Mar 27 19:16:03 laptop kernel: [    0.550652] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.550684] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Mar 27 19:16:03 laptop kernel: [    0.550714] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
Mar 27 19:16:03 laptop kernel: [    0.550787] usb usb5: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.550807] hub 5-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.550813] hub 5-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.550853] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 27 19:16:03 laptop kernel: [    0.550862] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.550891] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Mar 27 19:16:03 laptop kernel: [    0.550915] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
Mar 27 19:16:03 laptop kernel: [    0.550997] usb usb6: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.551017] hub 6-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.551023] hub 6-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.551062] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 27 19:16:03 laptop kernel: [    0.551071] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.551096] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Mar 27 19:16:03 laptop kernel: [    0.551119] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Mar 27 19:16:03 laptop kernel: [    0.551192] usb usb7: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.551212] hub 7-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.551217] hub 7-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.551257] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 27 19:16:03 laptop kernel: [    0.551266] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 27 19:16:03 laptop kernel: [    0.551293] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Mar 27 19:16:03 laptop kernel: [    0.551317] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b080
Mar 27 19:16:03 laptop kernel: [    0.551389] usb usb8: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    0.551412] hub 8-0:1.0: USB hub found
Mar 27 19:16:03 laptop kernel: [    0.551420] hub 8-0:1.0: 2 ports detected
Mar 27 19:16:03 laptop kernel: [    0.551502] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Mar 27 19:16:03 laptop kernel: [    0.553815] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar 27 19:16:03 laptop kernel: [    0.555787] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 27 19:16:03 laptop kernel: [    0.555793] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar 27 19:16:03 laptop kernel: [    0.555815] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar 27 19:16:03 laptop kernel: [    0.555834] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar 27 19:16:03 laptop kernel: [    0.555857] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar 27 19:16:03 laptop kernel: [    0.555957] mice: PS/2 mouse device common for all mice
Mar 27 19:16:03 laptop kernel: [    0.556072] rtc_cmos 00:03: RTC can wake from S4
Mar 27 19:16:03 laptop kernel: [    0.556112] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Mar 27 19:16:03 laptop kernel: [    0.556139] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Mar 27 19:16:03 laptop kernel: [    0.556242] device-mapper: uevent: version 1.0.3
Mar 27 19:16:03 laptop kernel: [    0.556337] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Mar 27 19:16:03 laptop kernel: [    0.556394] device-mapper: multipath: version 1.1.0 loaded
Mar 27 19:16:03 laptop kernel: [    0.556397] device-mapper: multipath round-robin: version 1.0.0 loaded
Mar 27 19:16:03 laptop kernel: [    0.556569] cpuidle: using governor ladder
Mar 27 19:16:03 laptop kernel: [    0.556639] cpuidle: using governor menu
Mar 27 19:16:03 laptop kernel: [    0.556933] TCP cubic registered
Mar 27 19:16:03 laptop kernel: [    0.557037] NET: Registered protocol family 10
Mar 27 19:16:03 laptop kernel: [    0.557410] lo: Disabled Privacy Extensions
Mar 27 19:16:03 laptop kernel: [    0.557643] NET: Registered protocol family 17
Mar 27 19:16:03 laptop kernel: [    0.558351] registered taskstats version 1
Mar 27 19:16:03 laptop kernel: [    0.559013]   Magic number: 2:745:294
Mar 27 19:16:03 laptop kernel: [    0.559030] misc hpet: hash matches
Mar 27 19:16:03 laptop kernel: [    0.559036] tty tty27: hash matches
Mar 27 19:16:03 laptop kernel: [    0.559122] rtc_cmos 00:03: setting system clock to 2010-03-27 19:15:52 UTC (1269717352)
Mar 27 19:16:03 laptop kernel: [    0.559124] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 27 19:16:03 laptop kernel: [    0.559125] EDD information not available.
Mar 27 19:16:03 laptop kernel: [    0.559168] Freeing unused kernel memory: 876k freed
Mar 27 19:16:03 laptop kernel: [    0.559480] Write protecting the kernel read-only data: 7676k
Mar 27 19:16:03 laptop kernel: [    0.571624] udev: starting version 151
Mar 27 19:16:03 laptop kernel: [    0.602215] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Mar 27 19:16:03 laptop kernel: [    0.629851] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 27 19:16:03 laptop kernel: [    0.631072] ahci: SSS flag set, parallel bus scan disabled
Mar 27 19:16:03 laptop kernel: [    0.631111] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Mar 27 19:16:03 laptop kernel: [    0.631114] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
Mar 27 19:16:03 laptop kernel: [    0.668442] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Mar 27 19:16:03 laptop kernel: [    0.668485] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 27 19:16:03 laptop kernel: [    0.669287] eth0: RTL8168c/8111c at 0xffffc9000067e000, 00:23:54:2f:b2:e3, XID 1c4000c0 IRQ 30
Mar 27 19:16:03 laptop kernel: [    0.671154] ohci1394 0000:07:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 19:16:03 laptop kernel: [    0.690189] scsi0 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690307] scsi1 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690359] scsi2 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690408] scsi3 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690454] scsi4 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690515] scsi5 : ahci
Mar 27 19:16:03 laptop kernel: [    0.690848] ata1: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff100 irq 29
Mar 27 19:16:03 laptop kernel: [    0.690851] ata2: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff180 irq 29
Mar 27 19:16:03 laptop kernel: [    0.690853] ata3: DUMMY
Mar 27 19:16:03 laptop kernel: [    0.690854] ata4: DUMMY
Mar 27 19:16:03 laptop kernel: [    0.690856] ata5: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff300 irq 29
Mar 27 19:16:03 laptop kernel: [    0.690859] ata6: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff380 irq 29
Mar 27 19:16:03 laptop kernel: [    0.732124] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Mar 27 19:16:03 laptop kernel: [    0.850118] usb 1-1: new high speed USB device using ehci_hcd and address 2
Mar 27 19:16:03 laptop kernel: [    1.001077] usb 1-1: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    1.030088] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 27 19:16:03 laptop kernel: [    1.031234] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 27 19:16:03 laptop kernel: [    1.032101] ata1.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
Mar 27 19:16:03 laptop kernel: [    1.032103] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar 27 19:16:03 laptop kernel: [    1.033364] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 27 19:16:03 laptop kernel: [    1.034210] ata1.00: configured for UDMA/133
Mar 27 19:16:03 laptop kernel: [    1.050142] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
Mar 27 19:16:03 laptop kernel: [    1.050260] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 27 19:16:03 laptop kernel: [    1.050326] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Mar 27 19:16:03 laptop kernel: [    1.050363] sd 0:0:0:0: [sda] Write Protect is off
Mar 27 19:16:03 laptop kernel: [    1.050384] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 27 19:16:03 laptop kernel: [    1.050492]  sda: sda1
Mar 27 19:16:03 laptop kernel: [    1.077408] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 27 19:16:03 laptop kernel: [    1.480115] usb 2-5: new high speed USB device using ehci_hcd and address 3
Mar 27 19:16:03 laptop kernel: [    1.631202] usb 2-5: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    1.800109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 27 19:16:03 laptop kernel: [    1.804462] ata2.00: ATAPI: Optiarc BD ROM BC-5500S, 1.C0, max UDMA/100
Mar 27 19:16:03 laptop kernel: [    1.808880] ata2.00: configured for UDMA/100
Mar 27 19:16:03 laptop kernel: [    1.821073] scsi 1:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S  1.C0 PQ: 0 ANSI: 5
Mar 27 19:16:03 laptop kernel: [    1.823793] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 27 19:16:03 laptop kernel: [    1.823796] Uniform CD-ROM driver Revision: 3.20
Mar 27 19:16:03 laptop kernel: [    1.823898] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 27 19:16:03 laptop kernel: [    1.910102] usb 5-1: new full speed USB device using uhci_hcd and address 2
Mar 27 19:16:03 laptop kernel: [    2.088851] usb 5-1: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    2.360113] usb 5-2: new full speed USB device using uhci_hcd and address 3
Mar 27 19:16:03 laptop kernel: [    2.529833] usb 5-2: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    2.570109] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 27 19:16:03 laptop kernel: [    2.571248] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 27 19:16:03 laptop kernel: [    2.572112] ata5.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
Mar 27 19:16:03 laptop kernel: [    2.572114] ata5.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar 27 19:16:03 laptop kernel: [    2.573371] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 27 19:16:03 laptop kernel: [    2.574217] ata5.00: configured for UDMA/133
Mar 27 19:16:03 laptop kernel: [    2.590197] scsi 4:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
Mar 27 19:16:03 laptop kernel: [    2.590320] sd 4:0:0:0: Attached scsi generic sg2 type 0
Mar 27 19:16:03 laptop kernel: [    2.590336] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Mar 27 19:16:03 laptop kernel: [    2.590409] sd 4:0:0:0: [sdb] Write Protect is off
Mar 27 19:16:03 laptop kernel: [    2.590431] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 27 19:16:03 laptop kernel: [    2.590528]  sdb: sdb1 sdb2 < sdb5 >
Mar 27 19:16:03 laptop kernel: [    2.634100] sd 4:0:0:0: [sdb] Attached SCSI disk
Mar 27 19:16:03 laptop kernel: [    2.810104] usb 6-1: new full speed USB device using uhci_hcd and address 2
Mar 27 19:16:03 laptop kernel: [    2.940105] ata6: SATA link down (SStatus 0 SControl 300)
Mar 27 19:16:03 laptop kernel: [    2.989046] usb 6-1: configuration #1 chosen from 1 choice
Mar 27 19:16:03 laptop kernel: [    3.001196] usbcore: registered new interface driver hiddev
Mar 27 19:16:03 laptop kernel: [    3.003179] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5
Mar 27 19:16:03 laptop kernel: [    3.003251] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
Mar 27 19:16:03 laptop kernel: [    3.008056] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input6
Mar 27 19:16:03 laptop kernel: [    3.008141] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
Mar 27 19:16:03 laptop kernel: [    3.008158] usbcore: registered new interface driver usbhid
Mar 27 19:16:03 laptop kernel: [    3.008160] usbhid: v2.6:USB HID core driver
Mar 27 19:16:03 laptop kernel: [    3.270434] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar 27 19:16:03 laptop kernel: [    5.346029] Adding 9936160k swap on /dev/sdb5.  Priority:-1 extents:1 across:9936160k 
Mar 27 19:16:03 laptop kernel: [    5.790874] udev: starting version 151
Mar 27 19:16:03 laptop kernel: [    6.507857] type=1505 audit(1269742558.440:2):  operation="profile_load" pid=616 name="/sbin/dhclient3"
Mar 27 19:16:03 laptop kernel: [    6.508386] type=1505 audit(1269742558.440:3):  operation="profile_load" pid=616 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 27 19:16:03 laptop kernel: [    6.508671] type=1505 audit(1269742558.440:4):  operation="profile_load" pid=616 name="/usr/lib/connman/scripts/dhclient-script"
Mar 27 19:16:03 laptop kernel: [    7.090061] Bluetooth: Core ver 2.15
Mar 27 19:16:03 laptop kernel: [    7.090363] NET: Registered protocol family 31
Mar 27 19:16:03 laptop kernel: [    7.090365] Bluetooth: HCI device and connection manager initialized
Mar 27 19:16:03 laptop kernel: [    7.090367] Bluetooth: HCI socket layer initialized
Mar 27 19:16:03 laptop kernel: [    7.226187] cfg80211: Calling CRDA to update world regulatory domain
Mar 27 19:16:03 laptop kernel: [    7.363886] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar 27 19:16:03 laptop kernel: [    7.363985] usbcore: registered new interface driver btusb
Mar 27 19:16:03 laptop kernel: [    7.387963] acpi device:1d: registered as cooling_device2
Mar 27 19:16:03 laptop kernel: [    7.388076] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input7
Mar 27 19:16:03 laptop kernel: [    7.388123] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Mar 27 19:16:03 laptop kernel: [    7.523272] asus_laptop: Asus Laptop Support version 0.42
Mar 27 19:16:03 laptop kernel: [    7.525001] sdhci: Secure Digital Host Controller Interface driver
Mar 27 19:16:03 laptop kernel: [    7.525003] sdhci: Copyright(c) Pierre Ossman
Mar 27 19:16:03 laptop kernel: [    7.527223] asus_laptop:   M70Vm model detected
Mar 27 19:16:03 laptop kernel: [    7.627727] input: Asus Laptop extra buttons as /devices/virtual/input/input8
Mar 27 19:16:03 laptop kernel: [    7.628277] Registered led device: asus::mail
Mar 27 19:16:03 laptop kernel: [    7.628327] Registered led device: asus::touchpad
Mar 27 19:16:03 laptop kernel: [    7.628348] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
Mar 27 19:16:03 laptop kernel: [    8.069662] cfg80211: World regulatory domain updated:
Mar 27 19:16:03 laptop kernel: [    8.069664] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 27 19:16:03 laptop kernel: [    8.069667] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 27 19:16:03 laptop kernel: [    8.069669] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 27 19:16:03 laptop kernel: [    8.069670] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 27 19:16:03 laptop kernel: [    8.069672] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 27 19:16:03 laptop kernel: [    8.069674] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 27 19:16:03 laptop kernel: [    8.096411] [drm] Initialized drm 1.1.0 20060810
Mar 27 19:16:03 laptop kernel: [    8.108954] sdhci-pci 0000:07:01.1: SDHCI controller found [1180:0822] (rev 22)
Mar 27 19:16:03 laptop kernel: [    8.108972] sdhci-pci 0000:07:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 27 19:16:03 laptop kernel: [    8.110014] sdhci-pci 0000:07:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
Mar 27 19:16:03 laptop kernel: [    8.111058] Registered led device: mmc0::
Mar 27 19:16:03 laptop kernel: [    8.112087] mmc0: SDHCI controller on PCI [0000:07:01.1] using DMA
Mar 27 19:16:03 laptop kernel: [    8.239781] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 27 19:16:03 laptop kernel: [    8.242230] [drm] nouveau 0000:01:00.0: failed to evaluate _DSM: 5
Mar 27 19:16:03 laptop kernel: [    8.242348] Linux video capture interface: v2.00
Mar 27 19:16:03 laptop kernel: [    8.251516] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Mar 27 19:16:03 laptop kernel: [    8.251518] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Mar 27 19:16:03 laptop kernel: [    8.251622] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 27 19:16:03 laptop kernel: [    8.251733] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Mar 27 19:16:03 laptop kernel: [    8.298363] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar 27 19:16:03 laptop kernel: [    8.298465] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x096400a1)
Mar 27 19:16:03 laptop kernel: [    8.299210] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Mar 27 19:16:03 laptop kernel: [    8.306339] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x280b1, caps: 0xb04711/0x60040d
Mar 27 19:16:03 laptop kernel: [    8.342491] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam (04f2:b033)
Mar 27 19:16:03 laptop kernel: [    8.343616] input: USB2.0 1.3M UVC WebCam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
Mar 27 19:16:03 laptop kernel: [    8.343706] usbcore: registered new interface driver uvcvideo
Mar 27 19:16:03 laptop kernel: [    8.344001] USB Video Class driver (v0.1.0)
Mar 27 19:16:03 laptop kernel: [    8.347342] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
Mar 27 19:16:03 laptop kernel: [    8.406007] [drm] nouveau 0000:01:00.0: ... appears to be valid
Mar 27 19:16:03 laptop kernel: [    8.406010] [drm] nouveau 0000:01:00.0: BIT BIOS found
Mar 27 19:16:03 laptop kernel: [    8.406012] [drm] nouveau 0000:01:00.0: Bios version 62.94.35.00
Mar 27 19:16:03 laptop kernel: [    8.406015] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Mar 27 19:16:03 laptop kernel: [    8.406017] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Mar 27 19:16:03 laptop kernel: [    8.406020] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Mar 27 19:16:03 laptop kernel: [    8.406022] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
Mar 27 19:16:03 laptop kernel: [    8.406024] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
Mar 27 19:16:03 laptop kernel: [    8.406026] [drm] nouveau 0000:01:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
Mar 27 19:16:03 laptop kernel: [    8.406028] [drm] nouveau 0000:01:00.0:   3: 0x00000310: type 0x10 idx 3 tag 0xff
Mar 27 19:16:03 laptop kernel: [    8.406030] [drm] nouveau 0000:01:00.0:   4: 0x00000311: type 0x11 idx 3 tag 0xff
Mar 27 19:16:03 laptop kernel: [    8.406032] [drm] nouveau 0000:01:00.0:   5: 0x00000313: type 0x13 idx 3 tag 0xff
Mar 27 19:16:03 laptop kernel: [    8.406034] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034
Mar 27 19:16:03 laptop kernel: [    8.406036] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000028
Mar 27 19:16:03 laptop kernel: [    8.406037] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02022312 00020010
Mar 27 19:16:03 laptop kernel: [    8.406039] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
Mar 27 19:16:03 laptop kernel: [    8.406055] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD09E
Mar 27 19:16:03 laptop kernel: [    8.510180] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD4B3
Mar 27 19:16:03 laptop kernel: [    8.540066] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE4D3
Mar 27 19:16:03 laptop kernel: [    8.540088] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE61C
Mar 27 19:16:03 laptop kernel: [    8.560218] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE858
Mar 27 19:16:03 laptop kernel: [    8.560220] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE8BD
Mar 27 19:16:03 laptop kernel: [    8.590055] [drm] nouveau 0000:01:00.0: 0xE8BD: Condition still not met after 20ms, skipping following opcodes
Mar 27 19:16:03 laptop kernel: [    8.590070] [drm] nouveau 0000:01:00.0: 0xBC4A: parsing output script 0
Mar 27 19:16:03 laptop kernel: [    8.590073] [drm] nouveau 0000:01:00.0: 0xC06E: parsing output script 0
Mar 27 19:16:03 laptop kernel: [    8.745736] [TTM] Zone  kernel: Available graphics memory: 2030014 kiB.
Mar 27 19:16:03 laptop kernel: [    8.745754] [drm] nouveau 0000:01:00.0: 512 MiB VRAM
Mar 27 19:16:03 laptop kernel: [    8.769962] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Mar 27 19:16:03 laptop kernel: [    8.769969] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Mar 27 19:16:03 laptop kernel: [    8.770308] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Mar 27 19:16:03 laptop kernel: [    8.776059] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Mar 27 19:16:03 laptop kernel: [    8.776991] [drm] nouveau 0000:01:00.0: Detected a LVDS output
Mar 27 19:16:03 laptop kernel: [    8.777002] [drm] nouveau 0000:01:00.0: Detected a DAC output
Mar 27 19:16:03 laptop kernel: [    8.777004] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Mar 27 19:16:03 laptop kernel: [    8.777007] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
Mar 27 19:16:03 laptop kernel: [    8.890952] [drm] nouveau 0000:01:00.0: Detected a VGA connector
Mar 27 19:16:03 laptop kernel: [    8.891065] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
Mar 27 19:16:03 laptop kernel: [    9.944038] lp: driver loaded but no devices found
Mar 27 19:16:03 laptop kernel: [   10.000785] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x40250000, bo ffff880128f88200
Mar 27 19:16:03 laptop kernel: [   10.000862] fb0: nouveaufb frame buffer device
Mar 27 19:16:03 laptop kernel: [   10.000864] registered panic notifier
Mar 27 19:16:03 laptop kernel: [   10.000869] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
Mar 27 19:16:03 laptop kernel: [   10.355249] vga16fb: mapped to 0xffff8800000a0000
Mar 27 19:16:03 laptop kernel: [   10.355303] fb1: VGA16 VGA frame buffer device
Mar 27 19:16:03 laptop kernel: [   10.548335] [drm] nouveau 0000:01:00.0: 0xBC4E: parsing output script 1
Mar 27 19:16:03 laptop kernel: [   10.548373] [drm] nouveau 0000:01:00.0: 0xBB29: parsing clock script 0
Mar 27 19:16:03 laptop kernel: [   10.551111] Console: switching to colour frame buffer device 240x75
Mar 27 19:16:03 laptop kernel: [   10.810879] [drm] nouveau 0000:01:00.0: 0xBC45: parsing clock script 1
Mar 27 19:16:04 laptop kernel: [   12.085264] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 27 19:16:04 laptop kernel: [   12.472181] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Mar 27 19:16:04 laptop kernel: [   13.014459] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 27 19:16:06 laptop kernel: [   14.865369] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 27 19:16:06 laptop kernel: [   14.865713] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Mar 27 19:16:06 laptop kernel: [   14.865715] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Mar 27 19:16:06 laptop kernel: [   14.865716] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Mar 27 19:16:07 laptop kernel: [   15.182414] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
Mar 27 19:16:07 laptop kernel: [   15.606640] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
Mar 27 19:16:07 laptop kernel: [   15.757603] Registered led device: iwl-phy0::radio
Mar 27 19:16:07 laptop kernel: [   15.757673] Registered led device: iwl-phy0::assoc
Mar 27 19:16:07 laptop kernel: [   15.757844] Registered led device: iwl-phy0::RX
Mar 27 19:16:07 laptop kernel: [   15.757897] Registered led device: iwl-phy0::TX
Mar 27 19:16:07 laptop kernel: [   15.780818] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 27 19:16:07 laptop kernel: [   15.811513] r8169: eth0: link down
Mar 27 19:16:07 laptop kernel: [   15.811915] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 27 19:16:08 laptop kernel: [   16.840737] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
Mar 27 19:16:08 laptop kernel: [   16.846538] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
Mar 27 19:16:08 laptop kernel: [   17.047431] type=1505 audit(1269742568.980:5):  operation="profile_replace" pid=1092 name="/sbin/dhclient3"
Mar 27 19:16:08 laptop kernel: [   17.047944] type=1505 audit(1269742568.980:6):  operation="profile_replace" pid=1092 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Mar 27 19:16:08 laptop kernel: [   17.048219] type=1505 audit(1269742568.980:7):  operation="profile_replace" pid=1092 name="/usr/lib/connman/scripts/dhclient-script"
Mar 27 19:16:09 laptop kernel: [   17.071415] type=1505 audit(1269742569.010:8):  operation="profile_load" pid=1091 name="/usr/share/gdm/guest-session/Xsession"
Mar 27 19:16:09 laptop kernel: [   17.116885] type=1505 audit(1269742569.050:9):  operation="profile_load" pid=1093 name="/usr/bin/evince"
Mar 27 19:16:09 laptop kernel: [   17.123280] type=1505 audit(1269742569.060:10):  operation="profile_load" pid=1093 name="/usr/bin/evince-previewer"
Mar 27 19:16:09 laptop kernel: [   17.127210] type=1505 audit(1269742569.060:11):  operation="profile_load" pid=1093 name="/usr/bin/evince-thumbnailer"
Mar 27 19:16:09 laptop kernel: [   17.234890] type=1505 audit(1269742569.170:12):  operation="profile_load" pid=1096 name="/usr/lib/cups/backend/cups-pdf"
Mar 27 19:16:09 laptop kernel: [   17.235501] type=1505 audit(1269742569.170:13):  operation="profile_load" pid=1096 name="/usr/sbin/cupsd"
Mar 27 19:16:09 laptop kernel: [   17.260607] type=1505 audit(1269742569.200:14):  operation="profile_load" pid=1097 name="/usr/sbin/tcpdump"
Mar 27 19:16:13 laptop kernel: [   21.335429] Bluetooth: L2CAP ver 2.14
Mar 27 19:16:13 laptop kernel: [   21.335432] Bluetooth: L2CAP socket layer initialized
Mar 27 19:16:13 laptop kernel: [   21.649571] ppdev: user-space parallel port driver
Mar 27 19:16:13 laptop kernel: [   21.711533] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 27 19:16:13 laptop kernel: [   21.711535] Bluetooth: BNEP filters: protocol multicast
Mar 27 19:16:13 laptop kernel: [   21.739926] Bridge firewalling registered
Mar 27 19:16:14 laptop kernel: [   22.168126] Bluetooth: SCO (Voice Link) ver 0.6
Mar 27 19:16:14 laptop kernel: [   22.168128] Bluetooth: SCO socket layer initialized
Mar 27 19:16:14 laptop kernel: [   22.268567] Bluetooth: RFCOMM TTY layer initialized
Mar 27 19:16:14 laptop kernel: [   22.268570] Bluetooth: RFCOMM socket layer initialized
Mar 27 19:16:14 laptop kernel: [   22.268571] Bluetooth: RFCOMM ver 1.11
Mar 27 19:21:36 laptop kernel: Kernel logging (proc) stopped.
Mar 27 19:21:36 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] exiting on signal 15.

---

### Post by seattle vic on 2010-03-27
One thing I just noticed when scouring the /var/log directory for information.  Syslog ended with the following lines:
================================================
**Mar 27 19:16:17 laptop gdm-session-worker[1550]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory**
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Sucessfully called chroot.
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Sucessfully dropped privileges.
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Sucessfully limited resources.
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Running.
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Watchdog thread running.
Mar 27 19:16:17 laptop rtkit-daemon[1555]: Canary thread running.
Mar 27 19:16:18 laptop polkitd[1560]: started daemon version 0.96 using authority implementation `local' version `0.96'
Mar 27 19:16:18 laptop anacron[1619]: Anacron 2.3 started on 2010-03-27
Mar 27 19:16:18 laptop anacron[1619]: Normal exit (0 jobs run)
Mar 27 19:16:18 laptop rtkit-daemon[1555]: Sucessfully made thread 1553 of process 1553 (n/a) owned by '114' high priority at nice level -11.
Mar 27 19:16:18 laptop rtkit-daemon[1555]: Supervising 1 threads of 1 processes of 1 users.
**Mar 27 19:16:19 laptop init: plymouth-stop pre-start process (1637) terminated with status **
**Mar 27 19:16:19 laptop gdm-simple-greeter[1537]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow**
Mar 27 19:16:20 laptop rtkit-daemon[1555]: Sucessfully made thread 1665 of process 1553 (n/a) owned by '114' RT at priority 5.
Mar 27 19:16:20 laptop rtkit-daemon[1555]: Supervising 2 threads of 1 processes of 1 users.
Mar 27 19:16:20 laptop rtkit-daemon[1555]: Sucessfully made thread 1667 of process 1553 (n/a) owned by '114' RT at priority 5.
Mar 27 19:16:20 laptop rtkit-daemon[1555]: Supervising 3 threads of 1 processes of 1 users.
Mar 27 19:16:21 laptop acpid: client connected from 1684[107:114]
Mar 27 19:16:21 laptop acpid: 1 client rule loaded
**Mar 27 19:16:23 laptop gdm-session-worker[1550]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed**
Mar 27 19:17:01 laptop CRON[1768]: (vic) CMD (root    cd / && run-parts --report /etc/cron.hourly)
Mar 27 19:21:36 laptop kernel: Kernel logging (proc) stopped.
Mar 27 19:21:36 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="831" x-info="http://www.rsyslog.com"] exiting on signal 15.
==============================================================
There are two gdm warnings and a gdm failed.  Is that a clue?  Also, I did see a reference to the plymouth process when trying to boot up in recovery mode.

---

### Post by seattle vic on 2010-03-29
Well, just before giving up for the night, I was going through bug reports related to this and came across one that suggested to install gnome-session. I did not look to see if I already had it installed, but presume that I did.

Anyway, it worked.

---

