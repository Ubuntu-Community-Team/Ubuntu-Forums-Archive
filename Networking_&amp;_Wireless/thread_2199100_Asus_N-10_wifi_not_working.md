---
title: "Asus N-10 wifi not working"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by sayang1991 on 2014-01-12
Hi,

I am new to this forum so sorry for any mistakes in posting skills or anything.
But i'm having problems with my first linux ssh server i created.

I tried to install my Asus USB N-10 wifi but i can't seem to get it working properly
I don't know what i'm doing wrong but these are the steps i followed:

Check lsusb for device it shows:
[COLOR=#333333][FONT=Lucida Grande]Bus 001 Device 004: ID 0b05:17ba ASUSTek Computer, Inc.
[/FONT][/COLOR]
Install driver by placing it into /home/[user]/asus/ and running
cd /home/[user]/asus
make
make install
No errors came up

running modprobe r8712u
lsmod now shows r8712u is running

But now i check ifconfig/iwconfig and no wlan is shown, ifconfig wlan0 up gives:
[COLOR=#333333][FONT=Lucida Grande]wlan0: ERROR while getting interface flags: No such device

[/FONT][/COLOR]I already tried severel [SOLVED] forum threads that i found about this problem but nothing seems to work, 
i also tried installing driver with ndiswrapper but the driver didnt linked to the device and when i made it link it directly crashed.

Anybody knows where i made a mistake? Any help is greatly apreciated :)

---

### Post by tfrue on 2014-01-12
What OS are you using? Ubuntu Server, or Ubuntu Desktop?

---

### Post by sayang1991 on 2014-01-12
I tried the desktop but i originally started with the problem running debian: 3.2.0-4-686-pae,
Tonight if i have time i wanted to try out the server edition: 12.04.3 LTS
All are 32-bit editions

---

### Post by tfrue on 2014-01-12
I don't think the server editions come with the wireless drivers ready to use like the desktop versions do since most people would use a server over ethernet. But it isn't hard to compile and get one ready to use.

Good luck,
Chris

---

### Post by sayang1991 on 2014-01-12
Yes i know the server edition comes without some parts that are needed but the problem is that it doesn't work on either desktop and server editions (Installed build-essential then driver on server edition)

---

### Post by Iowan on 2014-01-12
Perhaps you could post results of:
```
sudo lshw -C network
ifconfig
cat /etc/network/interfaces
```

---

### Post by tfrue on 2014-01-12
Also post:
```
sudo nm-tool
```
Would be useful. Please and thanks!

Chris

---

### Post by tfrue on 2014-01-12
I also don't think you will need the build-essentials since we won't compile any drivers, we just need to download the appropriate driver and make sure that the kernel is using the right one.

---

### Post by tfrue on 2014-01-13
Ok, so I was wrong about compiling, but here a link to the driver I believe you should need, and I will post the instructions you should need to get you up and running. Type:
[http://dlm3cdnet.asus.com/pub/ASUS/wireless/USB-N10/Dr_USB_N10_10018_Linux.zip](http://dlm3cdnet.asus.com/pub/ASUS/wireless/USB-N10/Dr_USB_N10_10018_Linux.zip)
```
sudo apt-get install zip unzip (Or use the archive manager in GUI)
unzip Dr_USB_N10_10018_Linux.zip *
cd Linux
sudo install.sh

```
Try the install.sh first before we try and compile.

Good luck
Chris

---

### Post by sayang1991 on 2014-01-13
Hi again, thanks for the help btw,

I tried sudo sh install.sh but it failed, gave 147 errors because the make command was not recognized,
after installing build-essentials it only gave 2 errors:

```
/home/enigma1991/rtl8712/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.2012                                   ing: cast from pointer to integer of different size [-Wpointer-to-int-cast]
cc1: some warnings being treated as errors
```

After plugging in the device it still won't work, these are the results you guys asked for:

```
sudo lshw -C network:
*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:80:81:21
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff


ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1d:92:80:81:21
          inet addr:192.168.178.13  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe80:8121/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43792328 (43.7 MB)  TX bytes:1109104 (1.1 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


cat /etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


sudo nm-tool
sudo: nm-tool: command not found

```

Connecting the cable (eth0) does not make a difference b.t.w.

---

### Post by sayang1991 on 2014-01-16
Anyone have any idea's? I am currently running windows XP on the device and it works fine, but i prefer to run ubuntu if i can get the wifi working :)

---

### Post by tfrue on 2014-01-16
Try an update the computer, type:
```
sudo apt-get update
```

Unplug then plug back in the usb device, then type:
```
dmesg | tail 
```

Chris

---

### Post by praseodym on 2014-01-16
Do you know exactly which Win driver it is? Is it "SU"?

---

### Post by sayang1991 on 2014-01-16
Yes it is the SU driver, I will try the update first thing tommorow morning!

---

### Post by sayang1991 on 2014-01-16
Didnt feel like waiting.....
The command gave this as result, the update installed fine but it still doesn't work


dmesg | tail

```
[  118.759023] usb 1-3: USB disconnect, device number 3
[  125.592039] usb 1-3: new high-speed USB device number 4 using ehci-pci
[  125.725767] usb 1-3: New USB device found, idVendor=0b05, idProduct=17ba
[  125.725775] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  125.725780] usb 1-3: Product: 802.11n WLAN Adapter
[  125.725785] usb 1-3: Manufacturer: Realtek
[  125.725790] usb 1-3: SerialNumber: 00e04c000001

```

---

### Post by chili555 on 2014-01-16
Please get a temporary wired ethernet connection and do:

```
sudo apt-get install linux-headers-generic build-essential

```
I suggest you download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd ~/Desktop/backports-3.12.2-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8192cu
```

Your wireless should now be working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd ~/Desktop/backports-3.12.2-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8192cu
```Please compile as above and give us your report.

---

### Post by sayang1991 on 2014-01-16
I installed everything with no errors but it still does not work,

lsmod shows the module's running but ifconfig/iwconfig give no result for wlan

```
Module                  Size  Used by
rtl8192cu              72751  0
rtl8192c_common        49561  1 rtl8192cu
rtlwifi                81225  1 rtl8192cu
mac80211              630977  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              525244  2 rtlwifi,mac80211
radeon                960918  1
snd_hda_codec_hdmi     37434  1
ttm                    84051  1 radeon
snd_hda_intel          44339  0
snd_hda_codec         141716  2 snd_hda_codec_hdmi,snd_hda_intel
drm_kms_helper         49597  1 radeon
drm                   287564  3 radeon,ttm,drm_kms_helper
kvm_amd                60205  0
sp5100_tco             13870  0
kvm                   455932  1 kvm_amd
ext2                   73755  1
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29989  1 snd_pcm
amd64_edac_mod         24557  0
i2c_algo_bit           13564  1 radeon
i2c_piix4              13459  0
snd                    69533  6 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
edac_core              62724  2 amd64_edac_mod
soundcore              12680  1 snd
edac_mce_amd           23343  1 amd64_edac_mod
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
serio_raw              13215  0
k8temp                 13064  0
mac_hid                13253  0
lp                     17799  0
parport                46562  1 lp
usb_storage            61749  2
ahci                   25879  0
libahci                31606  1 ahci
pata_acpi              13038  0
r8169                  68716  0
pata_atiixp            13242  0



```

dmesg | tail now says:
```

[   19.441134] type=1400 audit(1389915264.664:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=896 comm="apparmor_parser"
[   19.445811] type=1400 audit(1389915264.668:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=898 comm="apparmor_parser"
[   21.170556] init: plymouth-upstart-bridge main process (602) killed by TERM signal
[   75.989605] cfg80211: Calling CRDA to update world regulatory domain
[   76.046564] usbcore: registered new interface driver rtl8192cu
[  117.590842] usb 1-3: USB disconnect, device number 3
[  121.020041] usb 1-3: new high-speed USB device number 4 using ehci-pci
[  126.154051] usb 1-3: New USB device found, idVendor=0b05, idProduct=17ba
[  126.154060] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  126.154067] usb 1-3: SerialNumber: 00e04c000001



```

---

### Post by chili555 on 2014-01-16
Please reboot so we have a clean slate and run and post:```
rfkill list all
dmesg | grep -e wlan -e rtl
```Firmware, I'd guess.

Thanks.

---

### Post by sayang1991 on 2014-01-17
The only result it gave was:
dmesg | grep -e wlan -e rtl



```
[  206.143554] usbcore: registered new interface driver rtl8192cu

```

---

### Post by chili555 on 2014-01-17
> **sayang1991 said:**
> The only result it gave was:
dmesg | grep -e wlan -e rtl



```
[  206.143554] usbcore: registered new interface driver rtl8192cu

```Wow! Was it all the way to 206.xx until the module loaded? That is roughly 3 1/2 minutes after you started the computer. Does the computer take that long to boot or did you have to modprobe the driver from the terminal. Please reboot with the USB inserted and the ethernet detached so we have clean slate and run:```
dmesg > wifi.txt
```Attach the ethernet, get a connection and find the file wifi.txt in your user directory and copy and paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Give us the link in your reply.

---

### Post by sayang1991 on 2014-01-17
I had to modprobe the module indeed, was planning on fixing that later tonight,

Here is the mesg you requested:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-29-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 (Ubuntu 3.8.0-29.42~precise1-generic 3.8.13.5)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.0-29-generic root=/dev/mapper/Enigmaminer--vg-root ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffcffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffd0000-0x000000007ffddfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ffde000-0x000000007fffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: MICRO-STAR INTERANTIONAL CO.,LTD MS-7367/MS-7367, BIOS V3.3 11/05/2007
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7ffd0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x7ffcffff]
[    0.000000]  [mem 0x00000000-0x7fdfffff] page 2M
[    0.000000]  [mem 0x7fe00000-0x7ffcffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x7ffcffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x36048000-0x3701bfff]
[    0.000000] ACPI: RSDP 00000000000f9b10 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ffd0000 0003C (v01 110507 RSDT1635 20071105 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ffd0200 00084 (v02 110507 FACP1635 20071105 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ffd0430 04271 (v01  1ADNC 1ADNCB33 00000B33 INTL 20051117)
[    0.000000] ACPI: FACS 000000007ffde000 00040
[    0.000000] ACPI: APIC 000000007ffd0390 0005C (v01 110507 APIC1635 20071105 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007ffd03f0 0003C (v01 110507 OEMMCFG  20071105 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ffde040 00071 (v01 110507 OEMB1635 20071105 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007ffd46b0 00038 (v01 110507 OEMHPET  20071105 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007ffd46f0 002CC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ffcffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ffcffff]
[    0.000000]   NODE_DATA [mem 0x7ffcb000-0x7ffcffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d600000-ffff88007f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffcffff]
[    0.000000] On node 0 totalpages: 524127
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8128 pages used for memmap
[    0.000000]   DMA32 zone: 512016 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s85056 r8192 d21440 u1048576
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515929
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-29-generic root=/dev/mapper/Enigmaminer--vg-root ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ f3c0000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 2031468k/2096960k available (7170k kernel code, 452k absent, 65040k reserved, 6073k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using HPET reference calibration
[    0.000000] tsc: Detected 2793.000 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.016007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5586.00 BogoMIPS (lpj=11172000)
[    0.016015] pid_max: default: 32768 minimum: 301
[    0.016044] Security Framework initialized
[    0.016059] AppArmor: AppArmor initialized
[    0.016062] Yama: becoming mindful.
[    0.016270] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.017519] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.020491] Mount-cache hash table entries: 256
[    0.020698] Initializing cgroup subsys cpuacct
[    0.020702] Initializing cgroup subsys memory
[    0.020714] Initializing cgroup subsys devices
[    0.020717] Initializing cgroup subsys freezer
[    0.020721] Initializing cgroup subsys blkio
[    0.020724] Initializing cgroup subsys perf_event
[    0.020728] Initializing cgroup subsys hugetlb
[    0.020752] tseg: 0000000000
[    0.020765] CPU: Physical Processor ID: 0
[    0.020768] CPU: Processor Core ID: 0
[    0.020772] mce: CPU supports 5 MCE banks
[    0.020780] LVT offset 0 assigned for vector 0xf9
[    0.020787] process: using AMD E400 aware idle routine
[    0.020792] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.020792] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.020792] tlb_flushall_shift: 4
[    0.020898] Freeing SMP alternatives: 24k freed
[    0.022341] ACPI: Core revision 20121018
[    0.024735] ftrace: allocating 29358 entries in 115 pages
[    0.036480] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078630] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (fam: 0f, model: 43, stepping: 03)
[    0.080000] Performance Events: AMD PMU driver.
[    0.080000] ... version:                0
[    0.080000] ... bit width:              48
[    0.080000] ... generic registers:      4
[    0.080000] ... value mask:             0000ffffffffffff
[    0.080000] ... max period:             00007fffffffffff
[    0.080000] ... fixed-purpose events:   0
[    0.080000] ... event mask:             000000000000000f
[    0.080000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080000] smpboot: Booting Node   0, Processors  #1 OK
[    0.168050] Brought up 2 CPUs
[    0.168053] smpboot: Total of 2 processors activated (11172.51 BogoMIPS)
[    0.168606] devtmpfs: initialized
[    0.169582] EVM: security.selinux
[    0.169585] EVM: security.SMACK64
[    0.169587] EVM: security.capability
[    0.169604] PM: Registering ACPI NVS region [mem 0x7ffde000-0x7fffffff] (139264 bytes)
[    0.169604] regulator-dummy: no parameters
[    0.169604] NET: Registered protocol family 16
[    0.169604] node 0 link 0: io port [1000, ffffff]
[    0.169604] TOM: 0000000080000000 aka 2048M
[    0.169604] node 0 link 0: mmio [e0000000, efffffff]
[    0.169604] node 0 link 0: mmio [80000000, dfffffff]
[    0.169604] node 0 link 0: mmio [a0000, bffff]
[    0.169604] node 0 link 0: mmio [f0000000, ffffffff]
[    0.169604] bus: [bus 00-ff] on node 0 link 0
[    0.169604] bus: 00 [io  0x0000-0xffff]
[    0.169604] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.169604] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.169604] ACPI: bus type pci registered
[    0.169604] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169604] PCI: not using MMCONFIG
[    0.169604] PCI: Using configuration type 1 for base access
[    0.172577] bio: create slab <bio-0> at 0
[    0.172577] ACPI: Added _OSI(Module Device)
[    0.172577] ACPI: Added _OSI(Processor Device)
[    0.172577] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172577] ACPI: Added _OSI(Processor Aggregator Device)
[    0.172649] ACPI: EC: Detected MSI hardware, enabling workarounds.
[    0.172652] ACPI: EC: Look up EC in DSDT
[    0.173432] ACPI: Executed 3 blocks of module-level executable AML code
[    0.174884] ACPI: Interpreter enabled
[    0.174884] ACPI: (supports S0 S1 S4 S5)
[    0.174884] ACPI: Using IOAPIC for interrupt routing
[    0.174884] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.176661] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.188100] ACPI: No dock devices found.
[    0.188107] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.188186] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.188190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.188405] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.188407] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.188409] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.188411] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.188413] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.188416] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.188418] PCI: root bus 00: hardware-probed resources
[    0.188441] PCI host bridge to bus 0000:00
[    0.188446] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.188450] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.188453] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
[    0.188457] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.188467] pci 0000:00:00.0: [1002:7910] type 00 class 0x060000
[    0.188498] pci 0000:00:02.0: [1002:7913] type 01 class 0x060400
[    0.188534] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.188554] pci 0000:00:07.0: [1002:7917] type 01 class 0x060400
[    0.188588] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.188621] pci 0000:00:12.0: [1002:4380] type 00 class 0x01018f
[    0.188640] pci 0000:00:12.0: reg 10: [io  0xc000-0xc007]
[    0.188651] pci 0000:00:12.0: reg 14: [io  0xb000-0xb003]
[    0.188662] pci 0000:00:12.0: reg 18: [io  0xa000-0xa007]
[    0.188673] pci 0000:00:12.0: reg 1c: [io  0x9000-0x9003]
[    0.188683] pci 0000:00:12.0: reg 20: [io  0x8000-0x800f]
[    0.188694] pci 0000:00:12.0: reg 24: [mem 0xfe9ff800-0xfe9ffbff]
[    0.188717] pci 0000:00:12.0: set SATA to AHCI mode
[    0.188758] pci 0000:00:13.0: [1002:4387] type 00 class 0x0c0310
[    0.188773] pci 0000:00:13.0: reg 10: [mem 0xfe9fe000-0xfe9fefff]
[    0.188845] pci 0000:00:13.1: [1002:4388] type 00 class 0x0c0310
[    0.188860] pci 0000:00:13.1: reg 10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.188932] pci 0000:00:13.2: [1002:4389] type 00 class 0x0c0310
[    0.188947] pci 0000:00:13.2: reg 10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.189019] pci 0000:00:13.3: [1002:438a] type 00 class 0x0c0310
[    0.189034] pci 0000:00:13.3: reg 10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.189105] pci 0000:00:13.4: [1002:438b] type 00 class 0x0c0310
[    0.189120] pci 0000:00:13.4: reg 10: [mem 0xfe9fa000-0xfe9fafff]
[    0.189198] pci 0000:00:13.5: [1002:4386] type 00 class 0x0c0320
[    0.189219] pci 0000:00:13.5: reg 10: [mem 0xfe9ff000-0xfe9ff0ff]
[    0.189311] pci 0000:00:13.5: supports D1 D2
[    0.189313] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.189553] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.190434] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.196453] pci 0000:00:14.1: [1002:438c] type 00 class 0x01018a
[    0.196467] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.196478] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.196489] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.196500] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.196510] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.196550] pci 0000:00:14.3: [1002:438d] type 00 class 0x060100
[    0.196632] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.196684] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.196706] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.196724] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.196742] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.196806] pci 0000:01:00.0: [1002:6818] type 00 class 0x030000
[    0.196821] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.196834] pci 0000:01:00.0: reg 18: [mem 0xfeac0000-0xfeafffff 64bit]
[    0.196842] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.196857] pci 0000:01:00.0: reg 30: [mem 0xfeaa0000-0xfeabffff pref]
[    0.196903] pci 0000:01:00.0: supports D1 D2
[    0.196905] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    0.196943] pci 0000:01:00.1: [1002:aab0] type 00 class 0x040300
[    0.196958] pci 0000:01:00.1: reg 10: [mem 0xfea9c000-0xfea9ffff 64bit]
[    0.197036] pci 0000:01:00.1: supports D1 D2
[    0.204011] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.204017] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.204020] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.204024] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.204067] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.204082] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.204107] pci 0000:02:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
[    0.204137] pci 0000:02:00.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    0.204202] pci 0000:02:00.0: supports D1 D2
[    0.204204] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.204226] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.204235] pci 0000:00:07.0: PCI bridge to [bus 02]
[    0.204240] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.204243] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.204309] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.204320] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.204322] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xfcffffffff] (subtractive decode)
[    0.204325] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.204350] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.204383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.204415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.204481]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.204485]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.205279] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.205317] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.205354] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.205391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.205428] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.205467] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.205506] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.205545] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.205623] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205623] vgaarb: loaded
[    0.205623] vgaarb: bridge control possible 0000:01:00.0
[    0.205623] SCSI subsystem initialized
[    0.205623] ACPI: bus type scsi registered
[    0.205623] libata version 3.00 loaded.
[    0.205623] ACPI: bus type usb registered
[    0.205623] usbcore: registered new interface driver usbfs
[    0.205623] usbcore: registered new interface driver hub
[    0.205623] usbcore: registered new device driver usb
[    0.205623] PCI: Using ACPI for IRQ routing
[    0.215749] PCI: pci_cache_line_size set to 64 bytes
[    0.216243] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.216245] e820: reserve RAM buffer [mem 0x7ffd0000-0x7fffffff]
[    0.216330] NetLabel: Initializing
[    0.216333] NetLabel:  domain hash size = 128
[    0.216335] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216347] NetLabel:  unlabeled traffic allowed by default
[    0.216361] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.216361] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.218065] Switching to clocksource hpet
[    0.222776] AppArmor: AppArmor Filesystem Enabled
[    0.222814] pnp: PnP ACPI init
[    0.222830] ACPI: bus type pnp registered
[    0.222921] pnp 00:00: [dma 4]
[    0.222946] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.222983] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.223003] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.223030] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.223256] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.223336] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.223340] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.223346] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223487] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.223491] system 00:06: [io  0x040b] has been reserved
[    0.223494] system 00:06: [io  0x04d6] has been reserved
[    0.223498] system 00:06: [io  0x0c00-0x0c01] has been reserved
[    0.223502] system 00:06: [io  0x0c14] has been reserved
[    0.223505] system 00:06: [io  0x0c50-0x0c51] has been reserved
[    0.223509] system 00:06: [io  0x0c52] has been reserved
[    0.223512] system 00:06: [io  0x0c6c] has been reserved
[    0.223516] system 00:06: [io  0x0c6f] has been reserved
[    0.223519] system 00:06: [io  0x0cd0-0x0cd1] has been reserved
[    0.223523] system 00:06: [io  0x0cd2-0x0cd3] has been reserved
[    0.223527] system 00:06: [io  0x0cd4-0x0cd5] has been reserved
[    0.223531] system 00:06: [io  0x0cd6-0x0cd7] has been reserved
[    0.223535] system 00:06: [io  0x0cd8-0x0cdf] has been reserved
[    0.223539] system 00:06: [io  0x0800-0x089f] has been reserved
[    0.223542] system 00:06: [io  0x0b10-0x0b1f] has been reserved
[    0.223549] system 00:06: [io  0x0900-0x090f] has been reserved
[    0.223553] system 00:06: [io  0x0910-0x091f] has been reserved
[    0.223557] system 00:06: [io  0xfe00-0xfefe] has been reserved
[    0.223561] system 00:06: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.223565] system 00:06: [mem 0xfff00000-0xffffffff] has been reserved
[    0.223569] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223615] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.223719] system 00:08: [io  0x0600-0x06df] has been reserved
[    0.223723] system 00:08: [io  0x0ae0-0x0aef] has been reserved
[    0.223728] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223778] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.223783] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223953] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.223958] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.223962] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.223966] system 00:0a: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.223970] system 00:0a: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.223975] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.224087] pnp: PnP ACPI: found 11 devices
[    0.224089] ACPI: ACPI bus type pnp unregistered
[    0.230918] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.230923] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.230928] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.230932] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.230938] pci 0000:00:07.0: PCI bridge to [bus 02]
[    0.230942] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.230946] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.230952] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.230977] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.230979] pci_bus 0000:00: resource 5 [mem 0x80000000-0xfcffffffff]
[    0.230981] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.230984] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.230986] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.230988] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.230990] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.230992] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.230995] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.230997] pci_bus 0000:03: resource 5 [mem 0x80000000-0xfcffffffff]
[    0.230999] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.231034] NET: Registered protocol family 2
[    0.231182] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.231315] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.231427] TCP: Hash tables configured (established 16384 bind 16384)
[    0.231495] TCP: reno registered
[    0.231501] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.231526] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.231590] NET: Registered protocol family 1
[    0.632068] pci 0000:01:00.0: Boot video device
[    0.632076] PCI: CLS 64 bytes, default 64
[    0.632123] Trying to unpack rootfs image as initramfs...
[    0.904122] Freeing initrd memory: 16208k freed
[    0.913472] Initialise module verification
[    0.913520] audit: initializing netlink socket (disabled)
[    0.913534] type=2000 audit(1389969773.912:1): initialized
[    0.941411] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.942931] VFS: Disk quotas dquot_6.5.2
[    0.942978] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.943477] fuse init (API version 7.20)
[    0.943571] msgmni has been set to 3999
[    0.944154] Key type asymmetric registered
[    0.944159] Asymmetric key parser 'x509' registered
[    0.944195] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.944233] io scheduler noop registered
[    0.944236] io scheduler deadline registered (default)
[    0.944241] io scheduler cfq registered
[    0.944374] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.944450] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.944507] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.944525] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.944637] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.944646] ACPI: Power Button [PWRB]
[    0.944681] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.944686] ACPI: Power Button [PWRF]
[    0.944729] ACPI: duty_cycle spans bit 4
[    0.946841] GHES: HEST is not enabled!
[    0.946905] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.948423] Linux agpgart interface v0.103
[    0.949676] brd: module loaded
[    0.950345] loop: module loaded
[    0.950704] libphy: Fixed MDIO Bus: probed
[    0.950766] tun: Universal TUN/TAP device driver, 1.6
[    0.950769] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.950813] PPP generic driver version 2.4.2
[    0.950853] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.950856] ehci-pci: EHCI PCI platform driver
[    0.950887] ehci-pci 0000:00:13.5: EHCI Host Controller
[    0.950895] ehci-pci 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.950905] ehci-pci 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.950922] ehci-pci 0000:00:13.5: debug port 1
[    0.950965] ehci-pci 0000:00:13.5: irq 19, io mem 0xfe9ff000
[    0.960020] ehci-pci 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.960043] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.960047] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.960051] usb usb1: Product: EHCI Host Controller
[    0.960054] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.960057] usb usb1: SerialNumber: 0000:00:13.5
[    0.960155] hub 1-0:1.0: USB hub found
[    0.960161] hub 1-0:1.0: 10 ports detected
[    0.960321] ehci-platform: EHCI generic platform driver
[    0.960334] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960368] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.960377] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.960403] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe9fe000
[    1.020019] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.020023] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.020027] usb usb2: Product: OHCI Host Controller
[    1.020030] usb usb2: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.020034] usb usb2: SerialNumber: 0000:00:13.0
[    1.020122] hub 2-0:1.0: USB hub found
[    1.020129] hub 2-0:1.0: 2 ports detected
[    1.020212] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.020219] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.020241] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe9fd000
[    1.080016] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.080020] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.080024] usb usb3: Product: OHCI Host Controller
[    1.080027] usb usb3: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.080030] usb usb3: SerialNumber: 0000:00:13.1
[    1.080110] hub 3-0:1.0: USB hub found
[    1.080117] hub 3-0:1.0: 2 ports detected
[    1.080197] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    1.080206] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    1.080228] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe9fc000
[    1.140016] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.140021] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.140024] usb usb4: Product: OHCI Host Controller
[    1.140028] usb usb4: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.140031] usb usb4: SerialNumber: 0000:00:13.2
[    1.140115] hub 4-0:1.0: USB hub found
[    1.140122] hub 4-0:1.0: 2 ports detected
[    1.140202] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    1.140209] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.140224] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe9fb000
[    1.200015] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.200019] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.200023] usb usb5: Product: OHCI Host Controller
[    1.200026] usb usb5: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.200030] usb usb5: SerialNumber: 0000:00:13.3
[    1.200110] hub 5-0:1.0: USB hub found
[    1.200119] hub 5-0:1.0: 2 ports detected
[    1.200198] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.200207] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.200224] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe9fa000
[    1.260015] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.260019] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.260023] usb usb6: Product: OHCI Host Controller
[    1.260026] usb usb6: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.260029] usb usb6: SerialNumber: 0000:00:13.4
[    1.260111] hub 6-0:1.0: USB hub found
[    1.260119] hub 6-0:1.0: 2 ports detected
[    1.260183] uhci_hcd: USB Universal Host Controller Interface driver
[    1.260247] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.260250] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.260966] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.261062] mousedev: PS/2 mouse device common for all mice
[    1.261203] rtc_cmos 00:01: RTC can wake from S4
[    1.261323] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.261352] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.261439] device-mapper: uevent: version 1.0.3
[    1.261496] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.261506] cpuidle: using governor ladder
[    1.261509] cpuidle: using governor menu
[    1.261513] ledtrig-cpu: registered to indicate activity on CPUs
[    1.261515] EFI Variables Facility v0.08 2004-May-17
[    1.261716] ashmem: initialized
[    1.261828] TCP: cubic registered
[    1.261923] NET: Registered protocol family 10
[    1.262089] NET: Registered protocol family 17
[    1.262102] Key type dns_resolver registered
[    1.262311] Loading module verification certificates
[    1.263224] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 38550890b1fce75cc801d8fb942703db919b9386'
[    1.263238] registered taskstats version 1
[    1.265344] Key type trusted registered
[    1.266768] Key type encrypted registered
[    1.268586] rtc_cmos 00:01: setting system clock to 2014-01-17 14:42:55 UTC (1389969775)
[    1.268689] powernow-k8: fid 0x14 (2800 MHz), vid 0xa
[    1.268697] powernow-k8: fid 0x12 (2600 MHz), vid 0xc
[    1.268700] powernow-k8: fid 0x10 (2400 MHz), vid 0xe
[    1.268703] powernow-k8: fid 0xe (2200 MHz), vid 0x10
[    1.268705] powernow-k8: fid 0xc (2000 MHz), vid 0x10
[    1.268708] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    1.268711] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.268739] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (2 cpu cores) (version 2.20.00)
[    1.268755] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.268758] EDD information not available.
[    1.270414] Freeing unused kernel memory: 1012k freed
[    1.270759] Write protecting the kernel read-only data: 12288k
[    1.272044] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.273854] Freeing unused kernel memory: 1012k freed
[    1.277285] Freeing unused kernel memory: 1008k freed
[    1.284534] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.293276] udevd[94]: starting version 175
[    1.345204] Disabling lock debugging due to kernel taint
[    1.345556] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.345776] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.345950] r8169 0000:02:00.0 eth0: RTL8168b/8111b at 0xffffc90000306000, 00:1d:92:80:81:21, XID 18000000 IRQ 42
[    1.345956] r8169 0000:02:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.351038] ahci 0000:00:12.0: version 3.0
[    1.351094] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.351189] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.351195] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.354071] scsi0 : ahci
[    1.355228] scsi1 : ahci
[    1.355610] scsi2 : ahci
[    1.356447] scsi3 : ahci
[    1.356532] ata1: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ff900 irq 22
[    1.356538] ata2: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ff980 irq 22
[    1.356543] ata3: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa00 irq 22
[    1.356548] ata4: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa80 irq 22
[    1.357853] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.359657] scsi4 : pata_atiixp
[    1.360088] scsi5 : pata_atiixp
[    1.360321] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.360326] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.413923] usb 1-1: New USB device found, idVendor=1970, idProduct=0000
[    1.413932] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.413937] usb 1-1: Product: Z Mate 16GB
[    1.413940] usb 1-1: Manufacturer: DaneElec
[    1.413943] usb 1-1: SerialNumber: 928B190B0B3A
[    1.524018] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    1.657577] usb 1-3: New USB device found, idVendor=0b05, idProduct=17ba
[    1.657582] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.657585] usb 1-3: Product: 802.11n pter Adapter
[    1.657588] usb 1-3: Manufacturer: Realtek
[    1.657591] usb 1-3: SerialNumber: 00e04c000001
[    1.660756] Initializing USB Mass Storage driver...
[    1.660939] scsi6 : usb-storage 1-1:1.0
[    1.661039] usbcore: registered new interface driver usb-storage
[    1.661043] USB Mass Storage support registered.
[    1.676044] ata2: SATA link down (SStatus 0 SControl 300)
[    1.676081] ata1: SATA link down (SStatus 0 SControl 300)
[    1.680036] ata3: SATA link down (SStatus 0 SControl 300)
[    1.680066] ata4: SATA link down (SStatus 0 SControl 300)
[    2.661237] scsi 6:0:0:0: Direct-Access     DaneElec Z Mate 16GB      PMAP PQ: 0 ANSI: 0 CCS
[    2.661825] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    2.663095] sd 6:0:0:0: [sda] 31326208 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    2.663717] sd 6:0:0:0: [sda] Write Protect is off
[    2.663721] sd 6:0:0:0: [sda] Mode Sense: 23 00 00 00
[    2.664348] sd 6:0:0:0: [sda] No Caching mode page present
[    2.664351] sd 6:0:0:0: [sda] Assuming drive cache: write through
[    2.669973] sd 6:0:0:0: [sda] No Caching mode page present
[    2.669978] sd 6:0:0:0: [sda] Assuming drive cache: write through
[    2.672848]  sda: sda1 sda2 < sda5 >
[    2.675847] sd 6:0:0:0: [sda] No Caching mode page present
[    2.675856] sd 6:0:0:0: [sda] Assuming drive cache: write through
[    2.677973] sd 6:0:0:0: [sda] Attached SCSI removable disk
[    2.806568] bio: create slab <bio-1> at 1
[    2.965062] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    2.965071] EXT4-fs (dm-0): write access will be enabled during recovery
[    8.652639] EXT4-fs (dm-0): recovery complete
[    8.670151] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    9.003928] init: ureadahead main process (277) terminated with status 5
[    9.207334] Adding 2097148k swap on /dev/mapper/Enigmaminer--vg-swap_1.  Priority:-1 extents:1 across:2097148k 
[    9.383960] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.441846] udevd[356]: starting version 175
[    9.625052] lp: driver loaded but no devices found
[    9.696437] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   12.150812] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMOV 1 (20121018/utaddress-251)
[   12.150821] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.175761] MCE: In-kernel MCE decoding enabled.
[   12.177396] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   12.192279] EDAC MC: Ver: 3.0.0
[   12.199840] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   12.199903] sp5100_tco: PCI Revision ID: 0x14
[   12.199922] sp5100_tco: failed to find MMIO address, giving up.
[   12.201567] AMD64 EDAC driver v3.4.0
[   12.201603] EDAC amd64: DRAM ECC enabled.
[   12.201610] EDAC amd64: K8 revF or later detected (node 0).
[   12.201625] EDAC MC: DCT0 chip selects:
[   12.201627] EDAC amd64: MC: 0:   512MB 1:   512MB
[   12.201628] EDAC amd64: MC: 2:   512MB 3:   512MB
[   12.201630] EDAC amd64: MC: 4:     0MB 5:     0MB
[   12.201631] EDAC amd64: MC: 6:     0MB 7:     0MB
[   12.201647] EDAC amd64: CS0: Unbuffered DDR2 RAM
[   12.201649] EDAC amd64: CS1: Unbuffered DDR2 RAM
[   12.201650] EDAC amd64: CS2: Unbuffered DDR2 RAM
[   12.201651] EDAC amd64: CS3: Unbuffered DDR2 RAM
[   12.201798] EDAC MC0: Giving out device to 'amd64_edac' 'K8': DEV 0000:00:18.2
[   12.203825] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
[   12.204166] microcode: AMD CPU family 0xf not supported
[   12.288770] [drm] Initialized drm 1.1.0 20060810
[   12.330166] kvm: Nested Virtualization enabled
[   12.360486] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   12.360491] hda-intel 0000:01:00.1: Force to non-snoop mode
[   12.360565] snd_hda_intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   12.381115] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input3
[   12.381262] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input4
[   12.381357] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input5
[   12.381447] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   12.381535] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   12.381625] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   12.469536] [drm] radeon defaulting to kernel modesetting.
[   12.469540] [drm] radeon kernel modesetting enabled.
[   12.469809] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6818 0x1458:0x2554).
[   12.469830] [drm] register mmio base: 0xFEAC0000
[   12.469831] [drm] register mmio size: 262144
[   12.469865] radeon 0000:01:00.0: Invalid ROM contents
[   12.470352] ATOM BIOS: GV
[   12.470393] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   12.470396] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[   12.470803] [drm] Detected VRAM RAM=2048M, BAR=256M
[   12.470809] [drm] RAM width 256bits DDR
[   12.470895] [TTM] Zone  kernel: Available graphics memory: 1025366 kiB
[   12.470896] [TTM] Initializing pool allocator
[   12.470908] [TTM] Initializing DMA pool allocator
[   12.470937] [drm] radeon: 2048M of VRAM memory ready
[   12.470939] [drm] radeon: 512M of GTT memory ready.
[   12.470959] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.472443] [drm] Loading PITCAIRN Microcode
[   12.606223] type=1400 audit(1389969786.834:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=524 comm="apparmor_parser"
[   12.606645] type=1400 audit(1389969786.834:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=524 comm="apparmor_parser"
[   12.606881] type=1400 audit(1389969786.834:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=524 comm="apparmor_parser"
[   12.607356] type=1400 audit(1389969786.834:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=525 comm="apparmor_parser"
[   12.607774] type=1400 audit(1389969786.834:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=525 comm="apparmor_parser"
[   12.608034] type=1400 audit(1389969786.838:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=525 comm="apparmor_parser"
[   12.959543] r8169 0000:02:00.0 eth0: link down
[   12.959615] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.999862] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   12.999992] radeon 0000:01:00.0: WB enabled
[   13.000031] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88007adc7c00
[   13.000033] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88007adc7c04
[   13.000035] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88007adc7c08
[   13.000038] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88007adc7c0c
[   13.000040] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88007adc7c10
[   13.000045] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.000047] [drm] Driver supports precise vblank timestamp query.
[   13.000104] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   13.000119] radeon 0000:01:00.0: radeon: using MSI.
[   13.000154] [drm] radeon: irq initialized.
[   13.018652] [drm] ring test on 0 succeeded in 3 usecs
[   13.018659] [drm] ring test on 1 succeeded in 1 usecs
[   13.018664] [drm] ring test on 2 succeeded in 1 usecs
[   13.018730] [drm] ring test on 3 succeeded in 2 usecs
[   13.018742] [drm] ring test on 4 succeeded in 1 usecs
[   13.028869] [drm] ib test on ring 0 succeeded in 0 usecs
[   13.028934] [drm] ib test on ring 1 succeeded in 0 usecs
[   13.028997] [drm] ib test on ring 2 succeeded in 0 usecs
[   13.029028] [drm] ib test on ring 3 succeeded in 0 usecs
[   13.029059] [drm] ib test on ring 4 succeeded in 1 usecs
[   13.030808] [drm] Radeon Display Connectors
[   13.030809] [drm] Connector 0:
[   13.030811] [drm]   DP-1
[   13.030812] [drm]   HPD4
[   13.030814] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   13.030815] [drm]   Encoders:
[   13.030816] [drm]     DFP1: INTERNAL_UNIPHY2
[   13.030817] [drm] Connector 1:
[   13.030818] [drm]   DP-2
[   13.030819] [drm]   HPD5
[   13.030821] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   13.030822] [drm]   Encoders:
[   13.030823] [drm]     DFP2: INTERNAL_UNIPHY2
[   13.030824] [drm] Connector 2:
[   13.030825] [drm]   HDMI-A-1
[   13.030826] [drm]   HPD1
[   13.030828] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[   13.030829] [drm]   Encoders:
[   13.030830] [drm]     DFP3: INTERNAL_UNIPHY1
[   13.030831] [drm] Connector 3:
[   13.030832] [drm]   DVI-I-1
[   13.030833] [drm]   HPD6
[   13.030834] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[   13.030835] [drm]   Encoders:
[   13.030837] [drm]     DFP4: INTERNAL_UNIPHY
[   13.030838] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.030909] [drm] Internal thermal controller with fan control
[   13.030961] [drm] radeon: power management initialized
[   13.128279] [drm] fb mappable at 0xD114B000
[   13.128282] [drm] vram apper at 0xD0000000
[   13.128283] [drm] size 8294400
[   13.128284] [drm] fb depth is 24
[   13.128285] [drm]    pitch is 7680
[   13.128368] fbcon: radeondrmfb (fb0) is primary device
[   13.145825] Console: switching to colour frame buffer device 240x67
[   13.152682] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   13.152684] radeon 0000:01:00.0: registered panic notifier
[   13.152690] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[  136.559843] type=1400 audit(1389969910.787:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=869 comm="apparmor_parser"
[  136.560376] type=1400 audit(1389969910.791:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=869 comm="apparmor_parser"
[  136.560626] type=1400 audit(1389969910.791:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=869 comm="apparmor_parser"
[  136.565597] type=1400 audit(1389969910.795:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=871 comm="apparmor_parser"
[  138.289621] init: plymouth-upstart-bridge main process (668) killed by TERM signal
[  202.980430] cfg80211: Calling CRDA to update world regulatory domain
[  203.048483] usbcore: registered new interface driver rtl8192cu



```

---

### Post by chili555 on 2014-01-17
My apologies. I read this: [http://wikidevi.com/wiki/Asus_USB-N10_Nano](http://wikidevi.com/wiki/Asus_USB-N10_Nano)> rtl8192cu (in backports) or Realtek's vendor driverI assumed, without checking carefully, that the backports suite contains the driver for your device. It does not. 

I have learned my lesson and carefully checked this solution: [http://askubuntu.com/questions/364972/realtek-8188cus-doesnt-work](http://askubuntu.com/questions/364972/realtek-8188cus-doesnt-work) Here is what I see: ```
$ modinfo 8192cu.ko | grep 17BA
alias:          usb:v[COLOR="#FF0000"]0B05[/COLOR]p[COLOR="#FF0000"]17BA[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```...and there is your device! 

Before you proceed, uninstall the incorrect backports:```
cd ~/Desktop/backports-3.12.2-1/
sudo make uninstall
sudo modprobe -r rtl8192cu
cd ~
```Then proceed as I've linked and you should be all set. There is no need to install linux-headers-generic or build-essential; you already have them.

---

### Post by sayang1991 on 2014-01-17
You my friend, i thank you! 
It works!

iwconfig>

```
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

Setting the wifi up will work just fine now ;)
But i have to ask, what exactly did go wrong with my first driver?

---

### Post by chili555 on 2014-01-17
> But i have to ask, what exactly did go wrong with my first driver? If you mean r8712u, it just is too old to cover your relatively new device.

Glad it's working!

---

