---
title: "Connect a USB card to 9.04"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Prism on 2009-07-28
Hi there,

I'm using Ubuntu 9.04 and a cell phone which has an external memory card support. The connection between the computer and the phone is done using a Mini-USB cable.

Windows XP shows the external memory just fine, as another FAT drive. Ubuntu, however, doesn't recognize the connection, and nothing happens. I can't see any new folder in "Computer" or in /mnt or in /media.

The "dmesg" output is:

```
[ 4108.768037] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 4108.949724] usb 4-2: configuration #1 chosen from 1 choice
[ 4108.979883] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4108.981690] usb-storage: device found at 2
[ 4108.981694] usb-storage: waiting for device to settle before scanning
[ 4113.981488] usb-storage: device scan complete
[ 4113.984474] scsi 4:0:0:0: Direct-Access     Motorola Motorola iDEN US B De PQ: 1 ANSI: 4 CCS
[ 4113.986398] scsi 4:0:0:0: Attached scsi generic sg3 type 0
```

Is there anything I can do to make this work under Ubuntu?

Thanks!

---

### Post by halitech on 2009-07-28
what does lsusb show?

---

### Post by Prism on 2009-07-31
lsusb shows:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0c44:4810 Motorola iDEN 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by ukripper on 2009-07-31
can you post output of the following:
```
lsusb -v
```


```
sudo mount
```

and 

```
df -h
```

---

### Post by LowSky on 2009-07-31
well its showing up, it just isn't mounting. make sure you are correctly unmounting the phone when using windows, dont just pull the cord out.


how to mount manually
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Prism on 2009-07-31
@LowSky: I don't understand how to mount it manually. I don't know the name of the device (like /dev/*).

@ukripper:

```

lsusb -v:

Bus 004 Device 003: ID 0c44:4810 Motorola iDEN 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0c44 Motorola iDEN
  idProduct          0x4810 
  bcdDevice            0.01
  iManufacturer           3 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

```

```

sudo mount:

/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sdb4 on /mnt/fat type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /mnt/otheros type ext3 (rw,relatime)
/dev/sda6 on /mnt/storagedisk type ext3 (rw,relatime)
/dev/sdb1 on /mnt/windows type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/home/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=home)

```

```

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              22G  3.5G   17G  18% /
tmpfs                 495M     0  495M   0% /lib/init/rw
varrun                495M   96K  495M   1% /var/run
varlock               495M     0  495M   0% /var/lock
udev                  495M  164K  495M   1% /dev
tmpfs                 495M  100K  495M   1% /dev/shm
lrm                   495M  2.5M  492M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5              11G  8.3G  1.5G  86% /home
/dev/sdb4              41G   35G  5.6G  87% /mnt/fat
/dev/sda2              14G  3.7G  8.9G  30% /mnt/otheros
/dev/sda6              49G   41G  5.6G  89% /mnt/storagedisk
/dev/sdb1              15G   12G  3.2G  79% /mnt/windows

```

---

### Post by Liolikas on 2009-07-31
How much gb phone has?
Phone contents maybe in?
/mnt/fat

> 
I don't know the name of the device (like /dev/*).

Disconnect phone. 
Look into /dev/ folder s letter. Or in commands:
ls /dev/s*
Connect phone repeat same: 
ls /dev/s*
New "file" will appear that is you phone memory name.

---

### Post by Prism on 2009-07-31
Well, I tried it. The only "file" added in /dev/s* is /dev/sg3.
Then what happened was:

```

$ sudo mkdir /media/phone
$ sudo mount -t vfat /dev/sg3 /media/phone
mount: /dev/sg3 is not a block device

```

---

### Post by Liolikas on 2009-07-31
/dev/sg* is card reader device.
```

sg_map 

```
Should show you real storage device name. Something like sdc (sd - storage device)

---

### Post by Prism on 2009-07-31
Hmm. That's interesting:
```

$ sg_map
Error opening /dev/sg0 : Permission denied
Error opening /dev/sg1 : Permission denied
Error opening /dev/sg3 : Permission denied
Error opening /dev/sda : Permission denied
Error opening /dev/sdb : Permission denied
/dev/sg0  some error
/dev/sg1  some error
/dev/sg2  /dev/scd0

$ sudo sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/sdb
/dev/sg2  /dev/scd0
/dev/sg3

```

---

### Post by Liolikas on 2009-07-31
Show kernel modules:
```

lsmod

```
Your Linux kernel finds drive, but fails to use it.

kernel should be loaded with (as found in google now):
usb-storage
usbcore
uhci-hcd
scsi_mod

For full job. If Not you can:
sudo modprobe things
ex.:
sudo modprobe usbcore

Also install **sg3-utils**.

---

### Post by Prism on 2009-07-31
```

$ lsmod
Module                  Size  Used by
xt_state               10624  1 
xt_tcpudp              11776  16 
ipt_REJECT             11776  1 
ipt_LOG                14468  3 
xt_limit               11140  4 
iptable_nat            14724  0 
nf_nat                 30100  1 iptable_nat
nf_conntrack_ipv4      24216  4 iptable_nat,nf_nat
nf_conntrack           84752  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
iptable_mangle         11520  0 
iptable_filter         11392  1 
ip_tables              28304  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               31624  7 xt_state,xt_tcpudp,ipt_REJECT,ipt_LOG,xt_limit,iptable_nat,ip_tables
binfmt_misc            18572  1 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  0 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
nls_iso8859_1          13440  2 
nls_cp437              15104  2 
vfat                   21120  2 
fat                    65592  1 vfat
usb_storage           115392  0 
lp                     19588  0 
snd_via82xx            36648  2 
gameport               21520  1 snd_via82xx
snd_mpu401_uart        16640  1 snd_via82xx
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_via82xx_modem      21644  0 
snd_rawmidi            33920  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_ac97_codec        133848  2 snd_via82xx,snd_via82xx_modem
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
psmouse                64028  0 
ppdev                  16904  0 
snd_timer              34064  2 snd_seq,snd_pcm
snd_page_alloc         18704  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    78920  16 snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_via82xx_modem,snd_rawmidi,snd_ac97_codec,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              16800  1 snd
k8temp                 13440  0 
i2c_viapro             17304  0 
serio_raw              14468  0 
pcspkr                 11136  0 
nvidia               8123768  36 
shpchp                 44572  0 
parport_pc             45096  1 
parport                49584  3 lp,ppdev,parport_pc
via_rhine              34568  0 
8139too                36608  0 
8139cp                 31488  0 
mii                    14464  3 via_rhine,8139too,8139cp
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

The last three modules you've mentioned don't exist. usb_storage is loaded as you can see. sg3-utils is already installed.

---

### Post by Liolikas on 2009-07-31
> 
The last three modules you've mentioned don't exist. 

oioi this suggests you will have to do big job:
 [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Reason wold be:
> 
You have hardware the stock Ubuntu kernel does not support. 

Others can confirm this for sure!?

And at all custom kernel will work much better.

Do: Alternate Build Method: The Old-Fashioned Debian Way and after make menuconfig do not forget to select what you need as modules (M) of course use chance to get rid of useless things.

This is hardest task in Linux. GL ;)

---

### Post by Prism on 2009-07-31
Could someone confirm this? I don't want to mess with kernel compilation.

---

### Post by Prism on 2009-08-01
Anyone, please?

---

### Post by Shig on 2009-08-01
This is quite strange...

I've read posts suggesting that this device works in Windows because the Linux kernel does not wait as long as Windows when scanning new USB devices. There are kernel patches to fix this, but to confirm, can you please plug the phone in, and post your entire "dmesg" output (attach as a text file or encase in a code section)

It would also be interesting to see the output of
```
cat /proc/scsi/scsi
```

---

### Post by Prism on 2009-08-01
Sure.

```

$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 (Ubuntu 2.6.28-14.47-generic)
[    0.000000] Command line: root=UUID=251d4dfd-acc4-4f7d-a834-41d7615751f7 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffa0000 - 000000003ffb0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3ffa0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  modified: 000000003ffa0000 - 000000003ffb0000 (ACPI data)
[    0.000000]  modified: 000000003ffb0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000003ffa0000
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003ffa0000 page 4k
[    0.000000] kernel direct mapping tables up to 3ffa0000 @ 10000-13000
[    0.000000] last_map_addr: 3ffa0000 end: 3ffa0000
[    0.000000] RAMDISK: 37858000 - 37fefbef
[    0.000000] ACPI: RSDP 000FAA00, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3FFA0100, 003C (r1 A M I  OEMXSDT   9000512 MSFT       97)
[    0.000000] ACPI: FACP 3FFA0290, 00F4 (r3 A M I  OEMFACP   9000512 MSFT       97)
[    0.000000] ACPI: DSDT 3FFA03E0, 42E1 (r1  A0310 A0310001        1 MSFT  100000D)
[    0.000000] ACPI: FACS 3FFB0000, 0040
[    0.000000] ACPI: APIC 3FFA0390, 004A (r1 A M I  OEMAPIC   9000512 MSFT       97)
[    0.000000] ACPI: OEMB 3FFB0040, 003F (r1 A M I  OEMBIOS   9000512 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003ffa0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
[    0.000000]   #3 [0037858000 - 0037fefbef]          RAMDISK ==> [0037858000 - 0037fefbef]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20000dfffff] PMD -> [ffff880001200000-ffff880001ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffa0
[    0.000000] On node 0 totalpages: 261935
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2529 pages reserved
[    0.000000]   DMA zone: 1398 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254425 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255823
[    0.000000] Kernel command line: root=UUID=251d4dfd-acc4-4f7d-a834-41d7615751f7 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1400.042 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] allocated 10485760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] AGP bridge at 00:00:00
[    0.004000] Aperture from AGP @ dc000000 old size 32 MB
[    0.004000] Aperture from AGP @ dc000000 size 64 MB (APSIZE f30)
[    0.004000] Node 0: aperture @ dc000000 size 64 MB
[    0.004000] Memory: 1003316k/1048192k available (4748k kernel code, 452k absent, 43784k reserved, 2524k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 2800.08 BogoMIPS (lpj=5600168)
[    0.004043] Security Framework initialized
[    0.004051] SELinux:  Disabled at boot.
[    0.004072] AppArmor: AppArmor initialized
[    0.004084] Mount-cache hash table entries: 256
[    0.004248] Initializing cgroup subsys ns
[    0.004252] Initializing cgroup subsys cpuacct
[    0.004255] Initializing cgroup subsys memory
[    0.004259] Initializing cgroup subsys freezer
[    0.004274] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004276] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004279] tseg: 0000000000
[    0.004311] SMP alternatives: switching to UP code
[    0.180028] Freeing SMP alternatives: 37k freed
[    0.180895] ACPI: Core revision 20080926
[    0.184523] ACPI: Checking initramfs for custom DSDT
[    0.594407] Setting APIC routing to flat
[    0.595368] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.635064] CPU0: AMD Sempron(tm) Processor 2500+ stepping 02
[    0.636002] Brought up 1 CPUs
[    0.636002] Total of 1 processors activated (2800.08 BogoMIPS).
[    0.636002] CPU0 attaching NULL sched-domain.
[    0.636002] net_namespace: 1400 bytes
[    0.636002] Booting paravirtualized kernel on bare hardware
[    0.636002] Time: 22:10:18  Date: 08/01/09
[    0.636002] regulator: core version 0.5
[    0.636002] NET: Registered protocol family 16
[    0.636002] node 0 link 0: io port [1000, ffffff]
[    0.636002] TOM: 0000000040000000 aka 1024M
[    0.636002] node 0 link 0: mmio [a0000, bffff]
[    0.636002] node 0 link 0: mmio [40000000, ffffffff]
[    0.636002] bus: [00,ff] on node 0 link 0
[    0.636002] bus: 00 index 0 io port: [0, ffff]
[    0.636002] bus: 00 index 1 mmio: [a0000, bffff]
[    0.636002] bus: 00 index 2 mmio: [40000000, fcffffffff]
[    0.636002] ACPI: bus type pci registered
[    0.636002] PCI: Using configuration type 1 for base access
[    0.636002] ACPI: EC: Look up EC in DSDT
[    0.643951] ACPI: Interpreter enabled
[    0.643955] ACPI: (supports S0 S1 S3 S4 S5)
[    0.643980] ACPI: Using IOAPIC for interrupt routing
[    0.652419] ACPI: No dock devices found.
[    0.652432] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.652503] pci 0000:00:00.0: reg 10 32bit mmio: [0xdc000000-0xdfffffff]
[    0.652751] pci 0000:00:01.0: supports D1
[    0.652790] pci 0000:00:0c.0: reg 10 io port: [0xe800-0xe8ff]
[    0.652797] pci 0000:00:0c.0: reg 14 32bit mmio: [0xf9e00000-0xf9e000ff]
[    0.652825] pci 0000:00:0c.0: supports D1 D2
[    0.652828] pci 0000:00:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.652833] pci 0000:00:0c.0: PME# disabled
[    0.652864] pci 0000:00:0f.0: reg 10 io port: [0xe400-0xe407]
[    0.652871] pci 0000:00:0f.0: reg 14 io port: [0xe000-0xe003]
[    0.652878] pci 0000:00:0f.0: reg 18 io port: [0xd800-0xd807]
[    0.652884] pci 0000:00:0f.0: reg 1c io port: [0xd400-0xd403]
[    0.652891] pci 0000:00:0f.0: reg 20 io port: [0xd000-0xd00f]
[    0.652898] pci 0000:00:0f.0: reg 24 io port: [0xc800-0xc8ff]
[    0.652955] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.653021] pci 0000:00:10.0: reg 20 io port: [0xb400-0xb41f]
[    0.653038] pci 0000:00:10.0: supports D1 D2
[    0.653040] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653044] pci 0000:00:10.0: PME# disabled
[    0.653087] pci 0000:00:10.1: reg 20 io port: [0xb800-0xb81f]
[    0.653104] pci 0000:00:10.1: supports D1 D2
[    0.653106] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653110] pci 0000:00:10.1: PME# disabled
[    0.653153] pci 0000:00:10.2: reg 20 io port: [0xc000-0xc01f]
[    0.653170] pci 0000:00:10.2: supports D1 D2
[    0.653172] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653177] pci 0000:00:10.2: PME# disabled
[    0.653219] pci 0000:00:10.3: reg 20 io port: [0xc400-0xc41f]
[    0.653236] pci 0000:00:10.3: supports D1 D2
[    0.653238] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653243] pci 0000:00:10.3: PME# disabled
[    0.653272] pci 0000:00:10.4: reg 10 32bit mmio: [0xf9c00000-0xf9c000ff]
[    0.653303] pci 0000:00:10.4: supports D1 D2
[    0.653306] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653310] pci 0000:00:10.4: PME# disabled
[    0.653368] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.653374] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.653414] pci 0000:00:11.5: reg 10 io port: [0xb000-0xb0ff]
[    0.653447] pci 0000:00:11.5: supports D1 D2
[    0.653477] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.653537] pci 0000:00:12.0: reg 10 io port: [0xa800-0xa8ff]
[    0.653544] pci 0000:00:12.0: reg 14 32bit mmio: [0xf9b00000-0xf9b000ff]
[    0.653573] pci 0000:00:12.0: supports D1 D2
[    0.653576] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653580] pci 0000:00:12.0: PME# disabled
[    0.653701] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.653708] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xefffffff]
[    0.653714] pci 0000:01:00.0: reg 18 32bit mmio: [0xfa000000-0xfaffffff]
[    0.653731] pci 0000:01:00.0: reg 30 32bit mmio: [0xf9f00000-0xf9f1ffff]
[    0.653770] pci 0000:00:01.0: bridge 32bit mmio: [0xf9f00000-0xfbffffff]
[    0.653775] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xf8ffffff]
[    0.653783] bus 00 -> node 0
[    0.653790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.654159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.666574] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.666726] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.666876] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.667024] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.667173] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.667322] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.667471] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.667620] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.667756] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - F2, should be E4 [20080926]
[    0.667779] ACPI: WMI: Mapper loaded
[    0.668017] SCSI subsystem initialized
[    0.668062] libata version 3.00 loaded.
[    0.668124] usbcore: registered new interface driver usbfs
[    0.668147] usbcore: registered new interface driver hub
[    0.668181] usbcore: registered new device driver usb
[    0.668300] PCI: Using ACPI for IRQ routing
[    0.668311] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.680010] Bluetooth: Core ver 2.13
[    0.680062] NET: Registered protocol family 31
[    0.680064] Bluetooth: HCI device and connection manager initialized
[    0.680068] Bluetooth: HCI socket layer initialized
[    0.680070] NET: Registered protocol family 8
[    0.680072] NET: Registered protocol family 20
[    0.680084] NetLabel: Initializing
[    0.680086] NetLabel:  domain hash size = 128
[    0.680087] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.680105] NetLabel:  unlabeled traffic allowed by default
[    0.680153] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[    0.682416] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xdc000000
[    0.682530] AppArmor: AppArmor Filesystem Enabled
[    0.692012] pnp: PnP ACPI init
[    0.692022] ACPI: bus type pnp registered
[    0.693838] pnp 00:09: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693843] pnp 00:09: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693847] pnp 00:09: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693850] pnp 00:09: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693854] pnp 00:09: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693857] pnp 00:09: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693861] pnp 00:09: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693865] pnp 00:09: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693868] pnp 00:09: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693872] pnp 00:09: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693875] pnp 00:09: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693879] pnp 00:09: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.693883] pnp 00:09: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.696355] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.696359] pnp 00:0d: mem resource (0xc0000-0xdffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.696363] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.696367] pnp 00:0d: mem resource (0x100000-0x3ffeffff) overlaps 0000:00:00.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.696829] pnp: PnP ACPI: found 14 devices
[    0.696832] ACPI: ACPI bus type pnp unregistered
[    0.696847] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.696854] system 00:09: ioport range 0x3e1-0x3e7 has been reserved
[    0.696857] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.696860] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.696863] system 00:09: ioport range 0x400-0x41f has been reserved
[    0.696870] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.696873] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.696876] system 00:0a: iomem range 0xfff80000-0xffffffff has been reserved
[    0.701600] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.701603] pci 0000:00:01.0:   IO window: disabled
[    0.701608] pci 0000:00:01.0:   MEM window: 0xf9f00000-0xfbffffff
[    0.701613] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000f8ffffff
[    0.701628] pci 0000:00:01.0: setting latency timer to 64
[    0.701633] bus: 00 index 0 io port: [0x00-0xffff]
[    0.701636] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.701639] bus: 01 index 0 mmio: [0x0-0x0]
[    0.701641] bus: 01 index 1 mmio: [0xf9f00000-0xfbffffff]
[    0.701644] bus: 01 index 2 mmio: [0xe0000000-0xf8ffffff]
[    0.701646] bus: 01 index 3 mmio: [0x0-0x0]
[    0.701662] NET: Registered protocol family 2
[    0.736065] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.736505] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.738026] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.738786] TCP: Hash tables configured (established 131072 bind 65536)
[    0.738790] TCP reno registered
[    0.748098] NET: Registered protocol family 1
[    0.748256] checking if image is initramfs... it is
[    1.204039] Switched to high resolution mode on CPU 0
[    1.582620] Freeing initrd memory: 7774k freed
[    1.589034] audit: initializing netlink socket (disabled)
[    1.589051] type=2000 audit(1249164618.588:1): initialized
[    1.600306] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.601914] VFS: Disk quotas dquot_6.5.1
[    1.601988] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.602721] fuse init (API version 7.10)
[    1.602826] msgmni has been set to 1976
[    1.603033] alg: No test for stdrng (krng)
[    1.603047] io scheduler noop registered
[    1.603049] io scheduler anticipatory registered
[    1.603051] io scheduler deadline registered
[    1.603110] io scheduler cfq registered (default)
[    1.603128] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.603234] pci 0000:01:00.0: Boot video device
[    1.607359] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.607370] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.607511] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.607515] ACPI: Power Button (FF) [PWRF]
[    1.607583] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.607591] ACPI: Power Button (CM) [PWRB]
[    1.607983] processor ACPI_CPU:00: registered as cooling_device0
[    1.628220] Linux agpgart interface v0.103
[    1.628232] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.628372] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.628701] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.629591] brd: module loaded
[    1.629978] loop: module loaded
[    1.630090] Fixed MDIO Bus: probed
[    1.630098] PPP generic driver version 2.4.2
[    1.630171] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.630212] Driver 'sd' needs updating - please use bus_type methods
[    1.630227] Driver 'sr' needs updating - please use bus_type methods
[    1.630409] sata_via 0000:00:0f.0: version 2.4
[    1.630432] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.630486] sata_via 0000:00:0f.0: routed to hard irq line 10
[    1.630613] scsi0 : sata_via
[    1.630729] scsi1 : sata_via
[    1.632687] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xd000 irq 20
[    1.632690] ata2: SATA max UDMA/133 cmd 0xd800 ctl 0xd400 bmdma 0xd008 irq 20
[    1.836011] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.000287] ata1.00: ATA-7: WDC WD800JD-00MSA1, 10.01E01, max UDMA/133
[    2.000290] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.008314] ata1.00: configured for UDMA/133
[    2.212009] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.376334] ata2.00: ATA-7: HDS728080PLA380, PF2OA60A, max UDMA/133
[    2.376338] ata2.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.392353] ata2.00: configured for UDMA/133
[    2.392387] isa bounce pool size: 16 pages
[    2.392477] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-00MS 10.0 PQ: 0 ANSI: 5
[    2.392609] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.392630] sd 0:0:0:0: [sda] Write Protect is off
[    2.392633] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.392664] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.392747] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.392765] sd 0:0:0:0: [sda] Write Protect is off
[    2.392768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.392798] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.392803]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.445743] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.445808] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.445906] scsi 1:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[    2.446021] sd 1:0:0:0: [sdb] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    2.446042] sd 1:0:0:0: [sdb] Write Protect is off
[    2.446045] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.446076] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.446148] sd 1:0:0:0: [sdb] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    2.446166] sd 1:0:0:0: [sdb] Write Protect is off
[    2.446169] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.446199] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.446204]  sdb: sdb1 sdb2 sdb4
[    2.452309] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.452361] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.452856] pata_via 0000:00:0f.1: version 0.3.3
[    2.452873] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.453082] scsi2 : pata_via
[    2.453152] scsi3 : pata_via
[    2.455146] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.455149] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.624406] ata3.01: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.02, max UDMA/66
[    2.640297] ata3.01: configured for UDMA/66
[    2.808412] scsi 2:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.02 PQ: 0 ANSI: 5
[    2.811726] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.811730] Uniform CD-ROM driver Revision: 3.20
[    2.811861] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    2.811920] sr 2:0:1:0: Attached scsi generic sg2 type 5
[    2.812111] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.812140] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.812166] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.812243] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.812316] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9c00000
[    2.824010] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.824090] usb usb1: configuration #1 chosen from 1 choice
[    2.824122] hub 1-0:1.0: USB hub found
[    2.824132] hub 1-0:1.0: 8 ports detected
[    2.824269] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.824291] uhci_hcd: USB Universal Host Controller Interface driver
[    2.824338] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.824347] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.824401] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.824425] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b400
[    2.824521] usb usb2: configuration #1 chosen from 1 choice
[    2.824549] hub 2-0:1.0: USB hub found
[    2.824558] hub 2-0:1.0: 2 ports detected
[    2.824653] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.824660] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.824707] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.824727] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b800
[    2.824821] usb usb3: configuration #1 chosen from 1 choice
[    2.824849] hub 3-0:1.0: USB hub found
[    2.824857] hub 3-0:1.0: 2 ports detected
[    2.824949] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.824955] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.825012] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.825033] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[    2.825123] usb usb4: configuration #1 chosen from 1 choice
[    2.825155] hub 4-0:1.0: USB hub found
[    2.825163] hub 4-0:1.0: 2 ports detected
[    2.825254] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.825260] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.825313] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.825336] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c400
[    2.825438] usb usb5: configuration #1 chosen from 1 choice
[    2.825470] hub 5-0:1.0: USB hub found
[    2.825479] hub 5-0:1.0: 2 ports detected
[    2.825635] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.826074] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.826083] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.836044] mice: PS/2 mouse device common for all mice
[    2.872059] rtc_cmos 00:02: RTC can wake from S4
[    2.872100] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.872151] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.872247] device-mapper: uevent: version 1.0.3
[    2.872383] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.872438] device-mapper: multipath: version 1.0.5 loaded
[    2.872441] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.872512] cpuidle: using governor ladder
[    2.872514] cpuidle: using governor menu
[    2.873045] TCP cubic registered
[    2.873142] NET: Registered protocol family 10
[    2.873600] lo: Disabled Privacy Extensions
[    2.873954] NET: Registered protocol family 17
[    2.873982] Bluetooth: L2CAP ver 2.11
[    2.873984] Bluetooth: L2CAP socket layer initialized
[    2.873987] Bluetooth: SCO (Voice Link) ver 0.6
[    2.873989] Bluetooth: SCO socket layer initialized
[    2.874039] Bluetooth: RFCOMM socket layer initialized
[    2.874049] Bluetooth: RFCOMM TTY layer initialized
[    2.874051] Bluetooth: RFCOMM ver 1.10
[    2.874081] powernow-k8: Power state transitions not supported
[    2.874209] registered taskstats version 1
[    2.874365]   Magic number: 5:38:198
[    2.874459] rtc_cmos 00:02: setting system clock to 2009-08-01 22:10:20 UTC (1249164620)
[    2.874463] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.874465] EDD information not available.
[    2.874508] Freeing unused kernel memory: 532k freed
[    2.874871] Write protecting the kernel read-only data: 6688k
[    2.902870] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.444360] Floppy drive(s): fd0 is 1.44M
[    3.463961] FDC 0 is a post-1991 82077
[    3.504565] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.504595] 8139cp 0000:00:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.507815] 8139too Fast Ethernet driver 0.9.28
[    3.507863] 8139too 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.508893] eth0: RealTek RTL8139 at 0xe800, 00:0e:2e:38:17:1d, IRQ 17
[    3.508896] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.624413] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.624466] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.625288] eth1: VIA Rhine II at 0xf9b00000, 00:13:d4:c7:36:1a, IRQ 23.
[    3.625998] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    4.253952] PM: Starting manual resume from disk
[    4.253958] PM: Resume from partition 8:1
[    4.253960] PM: Checking hibernation image.
[    4.254155] PM: Resume from disk failed.
[    4.268937] EXT4-fs: barriers enabled
[    4.278188] kjournald2 starting.  Commit interval 5 seconds
[    4.278206] EXT4-fs: delayed allocation enabled
[    4.278208] EXT4-fs: file extents enabled
[    4.282772] EXT4-fs: mballoc enabled
[    4.282778] EXT4-fs: mounted filesystem with ordered data mode.
[    7.993176] udev: starting version 141
[    8.233754] parport_pc 00:0c: reported by Plug and Play ACPI
[    8.233800] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.251779] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.969635] nvidia: module license 'NVIDIA' taints kernel.
[    9.235653] ACPI: I/O resource vt596_smbus [0x400-0x407] conflicts with ACPI region SMRG [0x400-0x40f]
[    9.235658] ACPI: Device needs an ACPI driver
[    9.302100] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.302583] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[    9.343805] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    9.475270] ppdev: user-space parallel port driver
[    9.534099] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.582913] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[    9.582926] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   10.340018] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   10.538391] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   10.844232] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   10.844249] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   10.845066] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   10.845227] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   11.358836] codec_read: codec 0 is not valid [0xfe0000]
[   11.365479] codec_read: codec 0 is not valid [0xfe0000]
[   11.372146] codec_read: codec 0 is not valid [0xfe0000]
[   11.378768] codec_read: codec 0 is not valid [0xfe0000]
[   11.566826] lp0: using parport0 (interrupt-driven).
[   11.632327] Initializing USB Mass Storage driver...
[   11.632379] usbcore: registered new interface driver usb-storage
[   11.632383] USB Mass Storage support registered.
[   11.760182] Adding 1052216k swap on /dev/sda1.  Priority:-1 extents:1 across:1052216k
[   12.543386] EXT4 FS on sdb2, internal journal on sdb2:8
[   13.623184] kjournald starting.  Commit interval 5 seconds
[   13.623371] EXT3 FS on sda5, internal journal
[   13.623377] EXT3-fs: mounted filesystem with ordered data mode.
[   13.745009] kjournald starting.  Commit interval 5 seconds
[   13.745231] EXT3 FS on sda2, internal journal
[   13.745237] EXT3-fs: mounted filesystem with ordered data mode.
[   13.761966] kjournald starting.  Commit interval 5 seconds
[   13.762180] EXT3 FS on sda6, internal journal
[   13.762186] EXT3-fs: mounted filesystem with ordered data mode.
[   14.067878] type=1505 audit(1249153831.689:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2041
[   14.135426] type=1505 audit(1249153831.757:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2045
[   14.135616] type=1505 audit(1249153831.757:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2045
[   14.135688] type=1505 audit(1249153831.757:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2045
[   14.135753] type=1505 audit(1249153831.757:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2045
[   14.323959] type=1505 audit(1249153831.945:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2050
[   14.325918] type=1505 audit(1249153831.949:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2050
[   14.336396] eth0: link down
[   14.336782] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.381620] type=1505 audit(1249153832.005:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2062
[   14.757474] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   20.427449] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   20.427468] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   20.427549] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   22.416799] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.522517] nf_conntrack version 0.5.0 (8189 buckets, 32756 max)
[   22.522754] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   22.522757] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   22.522760] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.188016] eth1: no IPv6 routers present
[  531.316017] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  531.495353] usb 4-2: configuration #1 chosen from 1 choice
[  531.523506] scsi4 : SCSI emulation for USB Mass Storage devices
[  531.525348] usb-storage: device found at 2
[  531.525352] usb-storage: waiting for device to settle before scanning
[  536.525204] usb-storage: device scan complete
[  536.528554] scsi 4:0:0:0: Direct-Access     Motorola Motorola iDEN US B De PQ: 1 ANSI: 4 CCS
[  536.530705] scsi 4:0:0:0: Attached scsi generic sg3 type 0
```

```

$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD800JD-00MS Rev: 10.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: HDS728080PLA380  Rev: PF2O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVD-RAM GH22NP20 Rev: 1.02
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Motorola Model: Motorola iDEN US Rev: B De
  Type:   Direct-Access                    ANSI  SCSI revision: 02

```

---

### Post by Prism on 2009-08-04
Someone, please?

---

### Post by Shig on 2009-08-05
Hi Prism

Thanks for the reminder via PM, I've had a hectic week and your polite PM has reminded me of this thread.

One thing that is very strange is that an sd (scsi disk) device is not being created, even though the USB device is being registered in the SCSI subsystem used to present usb mass storage devices (phones, pen drives, etc) as block devices (disks). This suggests that the Linux kernel does not think this is a disk.

I had originally found a kernel patch that can be used to use Motorola phones, but found a much, much easier solution:
[You can use MTP instead of USB mass storage to mount the phone as a disk]("http://www.modmymoto.com/forums/showthread.php?t=55424")

Give it a shot and let us know how you go

Good Luck

---

### Post by Prism on 2009-08-07
Unfortunately it doesn't seem to work. I think that my model (i876) doesn't support MTP, so basically all MTP tools aren't so helpful here.

I also double-checked this problem on my installation of ArchLinux. The problem exists there too.

---

### Post by Shig on 2009-08-07
Bummer.

In that case the only option is a kernel patch (modification to linux), there is a step-by-step guide [here]("http://www.modmymoto.com/forums/showthread.php?p=375393#post375393")

You would probably be better following the guide provided by Lolikas though, and including the steps from the guide linked above to modify the kernel files (step 8 only)

Unfortunately that seems to be the only way due to the way in which this phone operates over USB

---

