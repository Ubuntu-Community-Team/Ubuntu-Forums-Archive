---
title: "sylvania g netbook cpu scaling"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-03-31
hey all,

i have a sylvania g netbook (running gOS 3.0, based on Hardy Heron)... i've read a lot about the cpu scaling issues with this model (speed is 600Mhz tops, though it has a 1.2Ghz capability), though I haven't found anything describing how to fix this... can anyone help me figure this out?

by the way, i've tried:

```
jmd9qs@jmd9qs-laptop:~$ sudo cpufreq-selector -f 1200
 
```

and it returns:

```
jmd9qs@jmd9qs-laptop:~$ sudo cpufreq-selector -f 1200
No cpufreq support
```

any help is appreciated

---

### Post by jmd9qs on 2009-04-01
here's some more information:

```
jmd9qs@jmd9qs-laptop:~$ procinfo -a
Linux 2.6.24-23-generic (buildd@vernadsky) (gcc 4.2.3 ) #1 1CPU [jmd9qs-laptop]

Memory:      Total        Used        Free      Shared     Buffers      
Mem:        969244      678660      290584           0       21612
Swap:      1253028           0     1253028

Bootup: Tue Mar 31 20:53:44 2009    Load average: 0.65 0.40 0.39 3/163 10053

user  :       0:11:00.98  17.1%  page in :   248839  disk 1:    12612r   16324w
nice  :       0:00:00.00   0.0%  page out:   404228
system:       0:02:18.40   3.6%  page act:    58239
IOwait:       0:09:26.69  14.7%  page dea:        0
hw irq:       0:00:01.80   0.0%  page flt:  3676506
sw irq:       0:00:04.60   0.1%  swap in :        0
idle  :       0:41:26.48  64.4%  swap out:        0
uptime:       1:04:18.98         context :  1366699

irq  0:    217656 timer                 irq 16:     16347 uhci_hcd:usb1        
irq  1:      6448 i8042                 irq 17:         0 uhci_hcd:usb2        
irq  8:         3 rtc                   irq 18:         0 uhci_hcd:usb3        
irq 10:        34 acpi                  irq 19:    140335 ehci_hcd:usb4        
irq 12:    158298 i8042                 irq 20:    228204 eth0, via@pci:0000:0 
irq 14:         0 libata                irq 21:     10544 HDA Intel            
irq 15:     28943 libata               

Kernel Command Line:
  root=UUID=7d555828-1f2f-4a17-bba8-931f001c1fc6 ro quiet splash loglevel=0

Modules:
  5  snd_rtctimer    23 *af_packet       43 *via             81 *drm            
 13 *binfmt_misc     10  ppdev          262 *ipv6            15  sbs            
  8 *sbshc           11  dock             6  container        5  cpufreq_usersp 
  9  cpufreq_conser   7  cpufreq_stats    3  cpufreq_powers  10  cpufreq_ondema 
  5 *freq_table       6 *ipt_REJECT       4 *xt_tcpudp        4 *iptable_filter 
 14 *ip_tables       16 *x_tables        35  parport_pc      12  lp             
 37 *parport         13  joydev         162  mac80211        15 *cfg80211       
  3  eeprom_93cx6   338 *snd_hda_intel   41  snd_pcm_oss     18 *snd_mixer_oss  
 77 *snd_pcm         11 *snd_page_alloc  10 *snd_hwdep        5  snd_seq_dummy  
 13 *evdev           35  snd_seq_oss      4  pcspkr           9  snd_seq_midi   
 25 *snd_rawmidi     57  uvcvideo        39  psmouse          2 *compat_ioctl32 
 92  r8187            8 *snd_seq_midi_e  29 *videodev        15 *v4l1_compat    
 18 *v4l2_common      8  serio_raw       53 *snd_seq         79 *ieee80211_rtl  
  8 *ieee80211_cryp  11 *ieee80211_cryp   6 *ieee80211_cryp   7 *ieee80211_cryp 
 24 *snd_timer        9 *snd_seq_device  56 *snd              9 *soundcore      
 19  video            5 *output          14  battery          7  ac             
  9  button          10  i2c_viapro      24 *i2c_core        11 *via_agp        
 34 *agpgart         34  shpchp          30 *pci_hotplug    134 *ext3           
 47 *jbd              9 *mbcache         36  sg              31  usbhid         
 38 *hid             72  usb_storage     19 *libusual        30 *sd_mod         
 24  8139cp          27  8139too          6 *mii              8  pata_acpi      
 13 *pata_via         8  ata_generic     37  ehci_hcd        26  uhci_hcd       
156 *libata         143 *usbcore        148 *scsi_mod        16  thermal        
 36 *processor        6  fan             42  fbcon            3 *tileblit       
  9 *font             7 *bitblit          3 *softcursor      50 *fuse           

Character Devices:                      Block Devices:
  1 mem              14 sound             1 ramdisk         132 sd              
  2 pty              21 sg                8 sd              133 sd              
  3 ttyp             29 fb               65 sd              134 sd              
  4 /dev/vc/0        81 video4linux      66 sd              135 sd              
  4 tty              99 ppdev            67 sd              
  4 ttyS            116 alsa             68 sd              
  5 /dev/tty        128 ptm              69 sd              
  5 /dev/console    136 pts              70 sd              
  5 /dev/ptmx       180 usb              71 sd              
  6 lp              189 usb_device      128 sd              
  7 vcs             226 drm             129 sd              
 10 misc            253 hidraw          130 sd              
 13 input           254 usb_endpoint    131 sd              

File Systems:
[sysfs]             [rootfs]            [bdev]              [proc]              
[cgroup]            [cpuset]            [debugfs]           [securityfs]        
[sockfs]            [pipefs]            [anon_inodefs]      [futexfs]           
[tmpfs]             [inotifyfs]         [devpts]            cramfs              
[ramfs]             [mqueue]            [fuse]              fuseblk             
[fusectl]           [usbfs]             ext3                [binfmt_misc]       

```


```
jmd9qs@jmd9qs-laptop:~$ lshw 
WARNING: you should run this program as super-user.
PCI (sysfs)  
jmd9qs@jmd9qs-laptop:~$ sudo !!
sudo lshw 
jmd9qs-laptop             
    description: Computer
    product: CX700
    vendor: VIA/Phoenix
    version: VT8380D
    serial: 000009
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: VIA Demo Board
       vendor: VIA
       physical id: 0
       version: VT8380D
       serial: 1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00 (06/13/2008)
          size: 92KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int9keyboard int10video acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: VIA C7-M Processor 1200MHz
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: 6.13.0
          slot: uFCBGA
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst internal write-back
     *-memory:0
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          capacity: 1GiB
        *-bank
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 16
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: TSOP FLASH Non-volatile
             physical id: 0
             slot: U3
             size: 512KiB
             width: 8 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci:0
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci:0
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CX700M2 UniChrome PRO II Graphics
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=16 mingnt=2
        *-ide
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64 module=pata_via
           *-disk
                description: ATA Disk
                product: ST730212DE
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 3.01
                serial: 9QS09GFK
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=dd6cdd6c
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 7d555828-1f2f-4a17-bba8-931f001c1fc6
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-30 19:32:36 filesystem=ext3 modified=2009-03-31 20:53:23 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-03-31 20:10:36 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 1223MiB
                   capacity: 1223MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1223MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: CX700 PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: CX700 Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Audio device
                product: VIA High Definition Audio Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:2
             description: PCI bridge
             product: CX700 PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@0000:03:09.0
                logical name: eth0
                version: 10
                serial: 00:14:0b:48:5d:d0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
     *-pci:1
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CX700 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CX700 Internal Module Bus
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=8
     *-scsi
          physical id: 3
          bus info: usb@4:6
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Multi-Card
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:15:af:bf:f3:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.8 multicast=yes wireless=802.11b/g linked

```

another problem I'm having:

1) Cheese doesn't see my webcam
2) there is NO sound at all, even w/ headphones plugged in


sorry for the long post, any and all help is appreciated

jmd9qs

---

### Post by jmd9qs on 2009-04-05
**UPDATE**


I've been working pretty much nonstop to figure out this problem, and I have been able to enable cpu scaling on the Sylvania g Netbook. In case any others have this little comp (and are having the same problem) I'll detail some of the steps I've gone through to get this to work:

1. First thing's first: get rid of that crappy gOS! I absolutely abhor this little P.O.S. version of Ubuntu, so I decided to install several different linux distro's to test which works the best (**REMEMBER**: this is the "g Netbook", not the "Meso"; I don't know if this will work on the Meso!). So far, I've tried:

--Knoppix (6.0)
--U.N.R. (Ubuntu Netbook Remix)
--Debian (Lenny)
--Moblin
--Vector Linux (5.0-6.0RC)

All had their advantages/disadvantages, but none worked as well as I had hoped on this platform. Luckily, I have found a distro that seems to work pretty well:

--Cruncbang Linux - can be found/downloaded at:   
[http://crunchbanglinux.org](http://crunchbanglinux.org)

**NOTE**:Crunchbang is basically Ubuntu 8.10 (Intrepid), but trimmed down for performance (not to mention size: my / was about 2.5 GB after install!)

On that site, if you dig around a little, you'll find info on how to install the Crunchbang ISO onto a bootable USB stick. From there you'll be able to install Crunchbang onto the g Netbook (**NOTE**: you may want to do a separate partition for your /home... it certainly came in handy for me with my several installs! That way you won't lose your data after installing...).

2. Update the OS! You need to make sure (after installation) that you have the latest Ubuntu Kernel by running these commands:

```
sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
```

(**NOTE**: I know, this is kind of sloppy, but it's what I did to get this to work...)

After updating, install cpufreq like this:

```
sudo apt-get install cpufreqd cpufrequtils
```

Once that's done, were ready to get to work!

3. Download and install the e_powersaver module. 

This step confused me a little bit... it seems like the *newest* kernel already has e_powersaver enabled, but I had to grab it online anyways... Here's what you do:

A) go to your "working directory" (for me it was /home/jmd9qs)
B) get the cpufreq .tar.bz2 (I know, you're thinking, "I just installed that!"; you are right, but bear with me, we're almost done).

```
wget http://www.a110wiki.de/wiki/images/6/65/Cpufreq-2.6.25_backport.tar.bz2
```

C) unpack the archive

```
tar xfvj Cpufreq-2.6.25_backport.tar.bz2
```

D) compile

```
cd cpufreq/
make
```

E) start the module (a few steps here)

```
sudo mkdir /lib/module/`uname -r`/cpu/
sudo cp e_powersaver.ko /lib/module/`uname -r`/cpu/
sudo depmod -ae
sudo modprobe e_powersaver
echo >> e_powersaver /etc/modules
```

Now, after these steps have been completed, the new module should be enabled and start at bootup. To check and see if it is working, run:

```
cat /proc/cpuinfo | grep cpu
```

which should return something like this:

```
jmd9qs@jmd9qs-laptop:~$ cat /proc/cpuinfo | grep cpu
cpu family	: 6
cpu MHz		: 1199.952
cpuid level	: 1

```

If it returns another value for "cpu MHz", this hasn't worked and you should retry. (Run the above command after a reboot, too. It should come back as "cpu MHz 1199.952"; again, if not, retry the steps detailed above).

O.K. Now, hopefully, your cpu supports scaling (by default, this guide enables "on-demand" scaling... I'm not sure how do do anything else yet). Unfortunately, I still haven't come up with a fix for the webcam, though I will probably write a wiki when I do (and include this fix, too!). The only other issue I've found on this little netbook is this: the sound will work through the laptop's speakers, but it will not come through the headphones if they are plugged in. 

Barring those two *little* problems, I am REALLY happy so far with Crunchbangs performance! Try this out, if you have a g Netbook; I think you'll be happy!

**NOTE**: The info used to work this out comes from these sites:

[https://lists.ubuntu.com/archives/ubuntu-ar/2009-January/016136.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-January/016136.html)

[http://forum.netbookuser.com/viewtopic.php?id=668](http://forum.netbookuser.com/viewtopic.php?id=668)

---

