---
title: "bcm4311 card not working on hp dv2416"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by vsanghvi on 2007-08-15
So i'm sure this comes up a lot and i'm sorry for posting another thread about this, but I've wasted waaay too much time, and i have a feeling i'm doing something wrong at this point. 

So I've tried just about every tutorial out there, and none seem to work. The ndiswrapper examples always seem to get rid of my card in iwconfig, and my wireless light goes off. 

The tutorial I like and wish would work is located here:[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

it gets my light to come on, but no wireless networks are deteted, and manually specifying a network doesn't work. Under iwlist scan, no access points can be found and iwconfig shows Access Point: Invalid.

btw unbuntu says my card is BCM4310 UART (rev 02)

and ideas (or hand holding) would be much appreciated

---

### Post by noob12 on 2007-08-15
Did you already try this one?  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by vsanghvi on 2007-08-15
I did try it earlier, but not on a clean install. I might as well try that later today and repost.

---

### Post by vsanghvi on 2007-08-16
So I tried using that method, and like with all ndiswrapper methods, when i reboot, network manager no longer shows any signs that it is even try to sense a wireless network, and iwconfig and iwlist scan no longer mention my wireless card anywhere. My laptop's wireless light does turn on though. Any ideas? 

Thanks,
Viraj

---

### Post by noob12 on 2007-08-16
Can you show me the output of these
```

sudo lshw -C network

ndiswrapper -v

ndiswrapper -l

cat /etc/modprobe.d/ndiswrapper

cat /etc/modules

cat /etc/network/interfaces

iwconfig

```

---

### Post by vsanghvi on 2007-08-16
Here you go. Thanks for your help on this.

[FONT="Courier New"]viraj@achilles:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:b3000000-b3003fff irq:21
viraj@achilles:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 
viraj@achilles:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
viraj@achilles:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
viraj@achilles:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
#ndiswrapper
ndiswrapper
ndiswrapper
viraj@achilles:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

viraj@achilles:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
[/FONT]

---

### Post by noob12 on 2007-08-16
You should take out the duplicate ndiswrapper lines from /etc/modules.

Make sure that a line **blacklist bcm43xx**  appears in /etc/modprobe.d/blacklist.  It may already; just check and add it if necessary.

The driver hasn't claimed the device yet. After taking the steps above, try probing it and seeing if it claims it.
Perhaps it just hasn't been probed.  Let's try that.

```

sudo modprobe ndiswrapper debug=15

```

Then lets look at the last part of the kernel log
```

dmesg | tail -50

```

---

### Post by vsanghvi on 2007-08-16
Here is the result of the dmesg command after doing what you've said:

[   17.688000] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: f8bcad7c
[   17.688000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[   17.688000] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   17.688000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   17.688000] ndiswrapper (mp_halt:258): device f782b400 is not initialized - not halting
[   17.688000] ndiswrapper: device eth%d removed
[   17.688000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[   17.688000] ndiswrapper: probe of 0000:01:00.0 failed with error -22
[   17.688000] usbcore: registered new interface driver ndiswrapper

---

### Post by noob12 on 2007-08-16
We should have got 50 lines of dmesg tail.  You seem to have chopped some of the previous stuff off.  Can you please include it.

We are seeing that the driver is having problems initializing.  I can't tell why at all.

Do you have BIOS settings on your laptop controlling the wireless?  There may be a setting that says put the wireless under Application Control (or OS control) or similar.  If you have that, make sure it is set (as well as wireless being enabled).

Can you also show me the output of
```

lspci -nn

```

Where did you get the Windows driver for your device?  Did you download it from HP?  Are you using the WinXP driver?

---

### Post by vsanghvi on 2007-08-16
I assumed the python script was grabbing a driver for the card. I'm dual booting w/ vista, so I do have the driver for the card, or could download it from hp. I've read that most people have found that the driver that works is the one from dell(same card) and from most howto's it seems that they are using that.

i haven't checked my bios settings for anything related to the wireless card, so i'll do that and report back.

Thanks again,
Viraj

Here is the output from the two commands
[   17.688000] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: f8bcad7c
[   17.688000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[   17.688000] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   17.688000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   17.688000] ndiswrapper (mp_halt:258): device f782b400 is not initialized - not halting
[   17.688000] ndiswrapper: device eth%d removed
[   17.688000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[   17.688000] ndiswrapper: probe of 0000:01:00.0 failed with error -22
[   17.688000] usbcore: registered new interface driver ndiswrapper
[   17.728000] Adding 1012024k swap on /dev/disk/by-uuid/63e7b2fb-7aa4-4933-a9fd-5b8f90bb5b52.  Priority:-1 extents:1 across:1012024k
[   18.008000] EXT3 FS on sda2, internal journal
[   19.524000] kjournald starting.  Commit interval 5 seconds
[   19.528000] EXT3 FS on sda7, internal journal
[   19.528000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.568000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   19.652000] NTFS volume version 3.1.
[   19.728000] NTFS volume version 3.1.
[   25.280000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.336000] ACPI: Battery Slot [BAT0] (battery present)
[   25.348000] No dock devices found.
[   25.448000] input: Power Button (FF) as /class/input/input4
[   25.448000] ACPI: Power Button (FF) [PWRF]
[   25.448000] input: Sleep Button (CM) as /class/input/input5
[   25.448000] ACPI: Sleep Button (CM) [SLPB]
[   25.448000] input: Power Button (CM) as /class/input/input6
[   25.448000] ACPI: Power Button (CM) [PWRB]
[   25.500000] ACPI: AC Adapter [ADP1] (on-line)
[   25.512000] Using specific hotkey driver
[   25.576000] ibm_acpi: ec object not found
[   25.644000] pcc_acpi: loading...
[   25.652000] wmi_add device=df88b800
[   25.652000] calling WQBA
[   25.892000] powernow-k8: Found 2 AMD Turion(tm) 64 X2  processors (version 2.00.00)
[   25.892000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   25.892000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   25.892000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   32.432000] ppdev: user-space parallel port driver
[   33.096000] apm: BIOS not found.
[   33.320000] Bluetooth: Core ver 2.11
[   33.320000] NET: Registered protocol family 31
[   33.320000] Bluetooth: HCI device and connection manager initialized
[   33.320000] Bluetooth: HCI socket layer initialized
[   33.344000] Bluetooth: L2CAP ver 2.8
[   33.344000] Bluetooth: L2CAP socket layer initialized
[   33.400000] Bluetooth: RFCOMM socket layer initialized
[   33.400000] Bluetooth: RFCOMM TTY layer initialized
[   33.400000] Bluetooth: RFCOMM ver 1.8
[   43.964000] NET: Registered protocol family 10
[   43.964000] lo: Disabled Privacy Extensions
[   43.964000] ADDRCONF(NETDEV_UP): eth0: link is not ready
viraj@achilles:/etc/modprobe.d$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 02)
05:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:09.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
05:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

---

### Post by vsanghvi on 2007-08-16
So i checked my bios, but saw nothing related to the wireless card at all. Should there be something?

---

### Post by noob12 on 2007-08-16
Usually there is some BIOS configuration, but if there isn't let's skip that.  I'm not familiar with your specific laptop.

Your last tail of dmesg was too late unfortunately.  It has to be done right after reloading the device to see the log messages covering that event.

The windows driver is saying it can't initialize the device.  The driver is at least trying to claim that device, but there may be something wrong with the specific driver you have installed or the conf files in the ndiswrapper directory.  We'll need to back up and verify those things.

I've used the Dell 32 bit WinXP drivers for the broadcom 43xx family successfully on some HP boxes in the past.  You're generally safest going back to your vendor's (HP in this case) download site and grabbing them there.  They'll have all of the right device ids in the inf files.

Can you confirm that you are running the 32 bit generic Ubuntu disribution?

Can you post
```

ls /etc/ndiswrapper/bcmwl5/

```
We'll probably want to examine the .inf file there and the .conf file beginning with 14e4:4312

---

### Post by maclenin on 2007-08-17
Folks, I am having the SAME issues with an HP 6910p / bcm4310 UART (rev 02) config. I am keeping my eyeballs riveted to your conversation - let me know if there is anything I can throw into the mix - I'll post breakthroughs, should I make any....

---

### Post by vsanghvi on 2007-08-18
sorry, i was unexpectedly busy the last few days, and probably most of today. I will post an update hwenever i get a chance

---

### Post by noob12 on 2007-08-18
I'm going to be gone from the forum for about a week, so you probably will want to seek help in the meantime from other forum readers.  Lots of competent help here.  Cheers.

---

### Post by maclenin on 2007-08-18
I have found a solution (with a little voodoo and good luck thrown in for good measure) - I am writing this note via my bcm4310 (rev 02) a.k.a. bcm4311....

Essentially, I used this [_guide_]("http://ubuntuforums.org/showthread.php?t=340689"), which I assembled (with the help of many others) and incorporated the suggested changes of these posters [_(1)_]("http://ubuntuforums.org/showpost.php?p=3189707&postcount=264") and [_(2)_]("http://ubuntuforums.org/showpost.php?p=3185868&postcount=7") - AFTER upgrading from Edgy to Feisty via the update manger.

Good luck and please post word, should you have any questions!

---

### Post by vsanghvi on 2007-08-22
maclenin, I tried your howto on a fresh install of feisty and i finally have my wireless working. I also followed the two changes from those other links. 

I actually originally tried to get the most updated driver from hp that works with my vista: sp3448, but that didn't work out at all. I then tried the one mentioned in those other posts, and I had immediate success. I never tried the howto straight up so i'm not sure if that would've worked, but I'd rather not mess with anything right now.

Anyway, thank you noob12 and maclenin! definitely couldn't have done it w/out the help

---

### Post by vsanghvi on 2007-08-22
also, just for anyone who might be wondering this worked on a dv2416us with a Broadcom 4311 (Broadcom 4310 UART (rev 02) in lspci) wireless card

---

