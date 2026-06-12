---
title: "Help!!! Wireless Card Adapter"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by pedriyo on 2008-07-01
Ok, I've been going back and forth with my Wireless Card Adapter which is a Linksys WPC54G Version 3.  I've installed Xubuntu in my PC and the card is not recognized..I think.. I can say that during the instalation process I noticed some kind of error with the card...any help...I'm a real rookie in this stuff so if you can give precise details of what I should do, I will really appreciate it.

WPC54G Linksys Wireless Adapter Version 3
My PC: Compaq presario V2000

---

### Post by pytheas22 on 2008-07-01
Please post the output of:
```

lsusb
lspci
lshw -C Network
iwconfig
```

(I am assuming that you have a wired connection on the machine and can copy and paste the output from these commands easily; if that's not the case, let me know and we'll work around it so you don't have to copy all that output over by hand.)

Also please describe more specifically the error that you think you noticed during installation regarding the network card.

---

### Post by pedriyo on 2008-07-01
During the instalation process, which was several weeks ago, I remember that the wizard told me that network adapter could not be configured and that network was DISABLED. By the way sorry if my sintaxis suck, I'm from Puerto Rico and english is not my primary language.

I assumed you wanted me to submit in the terminal those commands and this was the output



  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:f0:59:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.103 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:b3:f1:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
pedro@aneses:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I'm real beginner in this so, please explain carefully

THANKS for your help

---

### Post by pedriyo on 2008-07-01
(I am assuming that you have a wired connection on the machine and can copy and paste the output from these commands easily; if that's not the case, let me know and we'll work around it so you don't have to copy all that output over by hand.)

Yeah the connection right now is wired and maybe because of my lazyness is that I did not seek for help earlier

---

### Post by pytheas22 on 2008-07-01
Thanks for the information.  Please try this.  I'm not positive that it's going to work but I think it will:

```
sudo -s
apt-get install b43-fwcutter
```

then reboot.  Hopefully your card will be working.  If not, please post the output of:

```
iwconfig
ls /lib/firmware
```

---

### Post by pedriyo on 2008-07-02
> **pytheas22 said:**
> Thanks for the information.  Please try this.  I'm not positive that it's going to work but I think it will:

```
sudo -s
apt-get install b43-fwcutter
```

then reboot.  Hopefully your card will be working.  If not, please post the output of:

```
iwconfig
ls /lib/firmware
```

All Right this was the output of the first imput

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 64 not upgraded.
Need to get 15.8kB of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main b43-fwcutter 1:011-1 [15.8kB]
Fetched 15.8kB in 1s (9884B/s)      
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 117112 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--16:43:00--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866       86.75K/s    ETA 00:00

16:43:10 (81.28 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--16:43:10--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072       89.82K/s    ETA 00:00

16:43:20 (86.47 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw

and now i'm gonna reboot

---

### Post by pedriyo on 2008-07-02
I think it did not work because when plug in the card it does not recognize anything.  Here is the output

pedro@aneses:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:5A:2A:1B   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=70/100  Signal level=-42 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pedro@aneses:~$ ls /lib/firmware
2.6.24-16-generic     bcm43xx_initval04.fw  bcm43xx_microcode11.fw
2.6.24-18-generic     bcm43xx_initval05.fw  bcm43xx_microcode2.fw
b43                   bcm43xx_initval06.fw  bcm43xx_microcode4.fw
b43legacy             bcm43xx_initval07.fw  bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw  bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw  bcm43xx_pcm5.fw
bcm43xx_initval03.fw  bcm43xx_initval10.fw

---

### Post by pytheas22 on 2008-07-02
> when plug in the card it does not recognize anything.

What do you mean exactly?  The card doesn't see any networks, the lights don't come on...?

The card *does* seem to be recognized.  What happens if you type:
```

iwlist scan
```

---

### Post by pedriyo on 2008-07-02
pedro@aneses:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by pytheas22 on 2008-07-02
Alright, I guess it's still not working.  Here is a second approach using a different version of the driver (if you're interested, I can explain in more detail why we have to switch to a new strategy).  Please run these commands:
```

sudo -s
apt-get rmmod b43
sed -i 's/bcm43xx/b43/g' /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

During that last command, you will be asked about automatically downloading firmware.  Say yes.

Then reboot your computer and the wireless should work.  If not, please post the output of these commands:
```

cat /etc/modprobe.d/blacklist
iwconfig
lshw -C Network
iwlist scan
dmesg
```

(the last one will be long, but please post it all).

---

### Post by pedriyo on 2008-07-03
All right here it is

pedro@aneses:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist b43

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ssb
pedro@aneses:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"RUMNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pedro@aneses:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:f0:59:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:b3:f1:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
^[[Dpedro@aneses:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pedro@aneses:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000def0000 (usable)
[    0.000000]  BIOS-e820: 000000000def0000 - 000000000deff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000deff000 - 000000000df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000df00000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 222MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8340
[    0.000000] Entering add_active_range(0, 0, 57072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    57072
[    0.000000]   HighMem     57072 ->    57072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    57072
[    0.000000] On node 0 totalpages: 57072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 413 pages used for memmap
[    0.000000]   Normal zone: 52563 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8290 checksum 0
[    0.000000] ACPI: RSDP 000F8290, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 0DEF8C06, 0034 (r1 HP     3097     20040804  LTP        0)
[    0.000000] ACPI: FACP 0DEFEE41, 0074 (r1 HP     3097     20040804 PTL        5F)
[    0.000000] ACPI: DSDT 0DEF8C3A, 6207 (r1 HP     3091     20040804 MSFT  100000E)
[    0.000000] ACPI: FACS 0DEFFFC0, 0040
[    0.000000] ACPI: SSDT 0DEFEEB5, 00B5 (r1 PTLTD  POWERNOW 20040804  LTP        1)
[    0.000000] ACPI: APIC 0DEFEF6A, 005A (r1 PTLTD  	 3097   20040804  LTP        0)
[    0.000000] ACPI: MCFG 0DEFEFC4, 003C (r1 PTLTD    MCFG   20040804  LTP        0)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56627
[    0.000000] Kernel command line: root=UUID=ab1c4d16-ad61-4114-8ef9-ef7fd99e1175 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1591.934 MHz processor.
[    8.868493] Console: colour VGA+ 80x25
[    8.868497] console [tty0] enabled
[    8.868625] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.868737] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    8.873879] Memory: 214276k/228288k available (2176k kernel code, 13460k reserved, 1006k data, 368k init, 0k highmem)
[    8.873889] virtual kernel memory layout:
[    8.873890]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.873891]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.873893]     vmalloc : 0xce800000 - 0xff7fe000   ( 783 MB)
[    8.873894]     lowmem  : 0xc0000000 - 0xcdef0000   ( 222 MB)
[    8.873895]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.873897]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[    8.873898]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[    8.873902] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.873938] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.953937] Calibrating delay using timer specific routine.. 3187.38 BogoMIPS (lpj=6374766)
[    8.953963] Security Framework initialized
[    8.953969] SELinux:  Disabled at boot.
[    8.953985] AppArmor: AppArmor initialized
[    8.953989] Failure registering capabilities with primary security module.
[    8.953999] Mount-cache hash table entries: 512
[    8.954114] Initializing cgroup subsys ns
[    8.954119] Initializing cgroup subsys cpuacct
[    8.954129] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[    8.954139] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    8.954142] CPU: L2 Cache: 256K (64 bytes/line)
[    8.954145] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[    8.954154] Compat vDSO mapped to ffffe000.
[    8.954166] Checking 'hlt' instruction... OK.
[    8.970254] SMP alternatives: switching to UP code
[    8.971616] Freeing SMP alternatives: 11k freed
[    8.971764] Early unpacking initramfs... done
[    9.353947] ACPI: Core revision 20070126
[    9.354028] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.358191] CPU0: AMD Mobile AMD Sempron(tm) Processor 2800+ stepping 02
[    9.358217] Total of 1 processors activated (3187.38 BogoMIPS).
[    9.358399] ENABLING IO-APIC IRQs
[    9.358595] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.398314] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    9.398362] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    9.398365] ...trying to set up timer as Virtual Wire IRQ... works.
[    9.545783] Brought up 1 CPUs
[    9.545811] CPU0 attaching sched-domain:
[    9.545814]  domain 0: span 01
[    9.545816]   groups: 01
[    9.546019] net_namespace: 64 bytes
[    9.546028] Booting paravirtualized kernel on bare hardware
[    9.546540] Time: 22:33:41  Date: 07/03/08
[    9.546571] NET: Registered protocol family 16
[    9.546773] EISA bus registered
[    9.546803] ACPI: bus type pci registered
[    9.547059] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[    9.547062] PCI: Using configuration type 1
[    9.547065] Setting up standard PCI resources
[    9.549656] ACPI: EC: Look up EC in DSDT
[    9.551412] ACPI: Interpreter enabled
[    9.551416] ACPI: (supports S0 S3 S4 S5)
[    9.551430] ACPI: Using IOAPIC for interrupt routing
[    9.556217] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    9.556221] ACPI: EC: driver started in poll mode
[    9.556262] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.557460] PCI: Transparent bridge - 0000:00:14.4
[    9.557547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.557703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    9.557841] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.559793] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    9.559906] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    9.560015] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    9.560124] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    9.560232] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    9.560342] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    9.560450] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    9.560560] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    9.560683] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.560716] pnp: PnP ACPI init
[    9.560724] ACPI: bus type pnp registered
[    9.563452] pnp: PnP ACPI: found 10 devices
[    9.563456] ACPI: ACPI bus type pnp unregistered
[    9.563461] PnPBIOS: Disabled by ACPI PNP
[    9.564176] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.564431] PCI: Using ACPI for IRQ routing
[    9.564434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.593726] NET: Registered protocol family 8
[    9.593729] NET: Registered protocol family 20
[    9.593807] AppArmor: AppArmor Filesystem Enabled
[    9.597715] Time: tsc clocksource has been installed.
[    9.605756] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    9.605760] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    9.605764] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    9.605774] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    9.605778] system 00:08: ioport range 0x220-0x22f has been reserved
[    9.605781] system 00:08: ioport range 0x40b-0x40b has been reserved
[    9.605784] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    9.605787] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    9.605790] system 00:08: ioport range 0x530-0x537 has been reserved
[    9.605793] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    9.605796] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    9.605799] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    9.605802] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    9.605805] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    9.605808] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    9.605811] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    9.605815] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    9.605818] system 00:08: ioport range 0x8000-0x805f has been reserved
[    9.605821] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    9.605824] system 00:08: ioport range 0x87f-0x87f has been reserved
[    9.605831] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    9.605835] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[    9.605838] system 00:09: iomem range 0x0-0xfff could not be reserved
[    9.636265] PCI: Bridge: 0000:00:01.0
[    9.636267]   IO window: 9000-9fff
[    9.636272]   MEM window: d0100000-d01fffff
[    9.636275]   PREFETCH window: d4000000-d7ffffff
[    9.636286] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[    9.636288]   IO window: 0000a400-0000a4ff
[    9.636294]   IO window: 0000a800-0000a8ff
[    9.636300]   PREFETCH window: 20000000-23ffffff
[    9.636306]   MEM window: 24000000-27ffffff
[    9.636312] PCI: Bridge: 0000:00:14.4
[    9.636316]   IO window: a000-afff
[    9.636322]   MEM window: d0200000-d02fffff
[    9.636327]   PREFETCH window: disabled.
[    9.636370] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.636378] PCI: Setting latency timer of device 0000:05:09.0 to 64
[    9.636393] NET: Registered protocol family 2
[    9.673785] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    9.674032] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    9.674104] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    9.674174] TCP: Hash tables configured (established 8192 bind 8192)
[    9.674177] TCP reno registered
[    9.685833] checking if image is initramfs... it is
[   10.137529] Switched to high resolution mode on CPU 0
[   10.425093] Freeing initrd memory: 7327k freed
[   10.425765] audit: initializing netlink socket (disabled)
[   10.425780] audit(1215124422.412:1): initialized
[   10.427787] VFS: Disk quotas dquot_6.5.1
[   10.427864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.428018] io scheduler noop registered
[   10.428020] io scheduler anticipatory registered
[   10.428022] io scheduler deadline registered
[   10.428034] io scheduler cfq registered (default)
[   10.428043] PCI: MSI quirk detected. MSI deactivated.
[   11.093091] Boot video device is 0000:01:05.0
[   11.093393] isapnp: Scanning for PnP cards...
[   11.447950] isapnp: No Plug & Play device found
[   11.479117] Real Time Clock Driver v1.12ac
[   11.479226] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.479821] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   11.479833] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   11.480545] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.480623] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.480728] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   11.482675] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.482680] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.485183] mice: PS/2 mouse device common for all mice
[   11.485324] EISA: Probing bus 0 at eisa.0
[   11.485334] Cannot allocate resource for EISA slot 1
[   11.485364] Cannot allocate resource for EISA slot 8
[   11.485366] EISA: Detected 0 cards.
[   11.485371] cpuidle: using governor ladder
[   11.485373] cpuidle: using governor menu
[   11.485476] NET: Registered protocol family 1
[   11.485518] Using IPI No-Shortcut mode
[   11.485556] registered taskstats version 1
[   11.485667]   Magic number: 0:594:602
[   11.485760]   hash matches device ptyd6
[   11.485874] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.485877] EDD information not available.
[   11.486222] Freeing unused kernel memory: 368k freed
[   11.520899] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.722824] fuse init (API version 7.9)
[   12.744965] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.744972] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.747395] ACPI: Thermal Zone [THRM] (43 C)
[   13.444778] usbcore: registered new interface driver usbfs
[   13.444811] usbcore: registered new interface driver hub
[   13.456115] usbcore: registered new device driver usb
[   13.476094] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.477253] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.492078] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.492142] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   13.492159] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   13.492433] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   13.492458] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0000000
[   13.552150] usb usb1: configuration #1 chosen from 1 choice
[   13.552176] hub 1-0:1.0: USB hub found
[   13.552187] hub 1-0:1.0: 4 ports detected
[   13.552788] 8139too Fast Ethernet driver 0.9.28
[   13.656094] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   13.656113] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   13.656139] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   13.656158] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0001000
[   13.716135] usb usb2: configuration #1 chosen from 1 choice
[   13.716162] hub 2-0:1.0: USB hub found
[   13.716173] hub 2-0:1.0: 4 ports detected
[   13.820190] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   13.820210] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   13.820244] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   13.820306] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0002000
[   13.831895] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.832023] usb usb3: configuration #1 chosen from 1 choice
[   13.832048] hub 3-0:1.0: USB hub found
[   13.832055] hub 3-0:1.0: 8 ports detected
[   13.936093] ATIIXP: IDE controller (0x1002:0x4376 rev 0x00) at  PCI slot 0000:00:14.1
[   13.936117] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   13.936127] ATIIXP: not 100% native mode: will probe irqs later
[   13.936138]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   13.936155]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   13.936166] Probing IDE interface ide0...
[   14.895872] hda: ST9402113A, ATA DISK drive
[   14.895914] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   14.896145] hda: UDMA/100 mode selected
[   14.896479] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   14.899677] Probing IDE interface ide1...
[   15.971408] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
[   15.971451] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   15.972175] hdc: MWDMA2 mode selected
[   15.973208] ide1 at 0x170-0x177,0x376 on irq 15
[   15.984366] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[   15.985586] eth0: RealTek RTL8139 at 0xa000, 00:c0:9f:f0:59:dc, IRQ 19
[   15.985589] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   15.986303] SCSI subsystem initialized
[   15.998102] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.999188] libata version 3.00 loaded.
[   16.020564] hda: max request size: 512KiB
[   16.020570] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63
[   16.021766] hda: cache flushes supported
[   16.021804]  hda: hda1 hda2 < hda5 >
[   16.087643] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[   16.087652] Uniform CD-ROM driver Revision: 3.20
[   21.590987] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.590992] EXT3-fs: write access will be enabled during recovery.
[   26.287504] kjournald starting.  Commit interval 5 seconds
[   26.287528] EXT3-fs: hda1: orphan cleanup on readonly fs
[   26.287537] ext3_orphan_cleanup: deleting unreferenced inode 1966104
[   26.287566] EXT3-fs: hda1: 1 orphan inode deleted
[   26.287568] EXT3-fs: recovery complete.
[   26.290671] EXT3-fs: mounted filesystem with ordered data mode.
[   40.626201] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   41.739796] Linux agpgart interface v0.102
[   41.843790] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.891952] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.004734] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   42.274218] input: Power Button (FF) as /devices/virtual/input/input3
[   42.299608] ACPI: Power Button (FF) [PWRF]
[   42.299693] input: Power Button (CM) as /devices/virtual/input/input4
[   42.327621] ACPI: Power Button (CM) [PWRB]
[   42.327709] input: Sleep Button (CM) as /devices/virtual/input/input5
[   42.359586] ACPI: Sleep Button (CM) [SLPB]
[   42.359678] input: Lid Switch as /devices/virtual/input/input6
[   42.371851] ACPI: Lid Switch [LID]
[   42.675523] ACPI: WMI-Acer: Mapper loaded
[   42.851421] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[   42.851449] Yenta: Enabling burst memory read transactions
[   42.851457] Yenta: Using CSCINT to route CSC interrupts to PCI
[   42.851460] Yenta: Routing CardBus interrupts to PCI
[   42.851466] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x66
[   43.084035] Yenta: ISA IRQ mask 0x0ef0, PCI irq 16
[   43.084042] Socket status: 30000820
[   43.084046] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   43.084053] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   43.084057] cs: IO port probe 0xa000-0xafff: clean.
[   43.084379] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   43.261093] ACPI: AC Adapter [ACAD] (on-line)
[   43.563389] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   43.603688] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   43.834863] pccard: CardBus card inserted into slot 0
[   43.860201] ACPI: Battery Slot [BAT1] (battery present)
[   44.067227] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0e/LNXVIDEO:00/input/input8
[   44.090830] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.134578] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   44.346666] [fglrx] Maximum main memory to use for locked dma buffers: 170 MBytes.
[   44.346708] [fglrx] ASYNCIO init succeed!
[   44.346828] [fglrx] PAT is enabled successfully!
[   44.347749] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   44.630399] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[   44.738555] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 0 converters and GPIO not ready (0x1)
[   44.739321] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[   46.074050] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[   46.074063] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   46.074078] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   46.133945] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[   46.293777] cs: IO port probe 0x100-0x3af: clean.
[   46.296242] cs: IO port probe 0x3e0-0x4ff: clean.
[   46.297258] cs: IO port probe 0x820-0x8ff: clean.
[   46.298115] cs: IO port probe 0xc00-0xcf7: clean.
[   46.299015] cs: IO port probe 0xa00-0xaff: clean.
[   46.487302] b43-phy0: Broadcom 4318 WLAN found
[   46.554405] phy0: Selected rate control algorithm 'simple'
[   46.671963] input: b43-phy0 as /devices/virtual/input/input9
[   48.119137] Registered led device: b43-phy0:tx
[   48.119160] Registered led device: b43-phy0:rx
[   48.119180] Registered led device: b43-phy0:radio
[   48.126866] loop: module loaded
[   48.280192] lp: driver loaded but no devices found
[   48.425412] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   48.494394] usbcore: registered new interface driver ndiswrapper
[   48.635691] Adding 650592k swap on /dev/hda5.  Priority:-1 extents:1 across:650592k
[   49.559345] NET: Registered protocol family 17
[  124.464786] NET: Registered protocol family 10
[  124.465076] lo: Disabled Privacy Extensions
[  124.466041] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  144.027642] EXT3 FS on hda1, internal journal
[  145.477460] ip_tables: (C) 2000-2006 Netfilter Core Team
[  146.601645] No dock devices found.
[  147.112542] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 2800+ processors (1 cpu cores) (version 2.20.00)
[  147.112584] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0xa
[  147.112587] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x13
[  149.088882] apm: BIOS not found.
[  149.716492] ppdev: user-space parallel port driver
[  150.556285] audit(1215124563.018:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5083 profile="/usr/sbin/cupsd" namespace="default"
[  150.964309] APIC error on CPU0: 00(40)
[  302.454862] Marking TSC unstable due to: cpufreq changes.
[  302.456369] Time: acpi_pm clocksource has been installed.
[  302.800249] Clocksource tsc unstable (delta = -172853876 ns)
[  303.766134] eth0: link down
[  303.766401] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  303.952450] Bluetooth: Core ver 2.11
[  303.953568] NET: Registered protocol family 31
[  303.953576] Bluetooth: HCI device and connection manager initialized
[  303.953586] Bluetooth: HCI socket layer initialized
[  304.091911] Bluetooth: L2CAP ver 2.9
[  304.091921] Bluetooth: L2CAP socket layer initialized
[  304.187111] Bluetooth: RFCOMM socket layer initialized
[  304.187142] Bluetooth: RFCOMM TTY layer initialized
[  304.187147] Bluetooth: RFCOMM ver 1.8
[  306.646857] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[  155.245193] [fglrx] GART Table is not in FRAME_BUFFER range 
[  155.245206] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  155.245209] [fglrx] Reserve Block - 1 offset =  0X1ff5000 length = 0Xb000
[  155.380685] [fglrx] interrupt source 20008000 successfully enabled
[  155.380695] [fglrx] enable ID = 0x00000004
[  155.381081] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  970.497860] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  970.498195] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  984.997557] eth0: no IPv6 routers present

---

### Post by pytheas22 on 2008-07-03
Thanks for the information.  I don't know why but something went wrong with the blacklisting.  Please do this:

1. open the blacklist file:

```
sudo mousepad /etc/modprobe.d/blacklist
```

A file will open.  Add to the bottom of the file these lines:
```

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist b43 ssb
blacklist ndiswrapper
```

Save the file and reboot.  The wireless should work now.  Please let me know.

---

### Post by pedriyo on 2008-07-07
Didn't work but I got somebody in my university who helped me fix the problem.  I seriously got lost trying to figure out what he did but i can tell u that he used 

dmesg ...plugged in the adapter and then 

sudo iwconfig eth1 essid "network"
sudo dhclient eth1

..I supposed he ran somehow a program before doing this but it worked

anyway thanks for your help!!

---

### Post by Subrat Kumar Pradhan on 2009-02-06
hi i am subrat from india
can you help me to solve a problem?
i'm a new user of ubuntu and ubuntu forum also

---

### Post by pytheas22 on 2009-02-06
> hi i am subrat from india
can you help me to solve a problem?
i'm a new user of ubuntu and ubuntu forum also

Subrat: please first try [searching the forums]("http://ubuntuforums.org/search.php") to see if you can find a solution to your problem--chances are good that someone else has already had the same issue and resolved it.

If you can't find a solution by searching, please start a new thread in the appropriate section of the forums.  You can find a list of the main support categories [here]("http://ubuntuforums.org/forumdisplay.php?f=327").  Click on the section appropriate to your problem, then click "New Thread" to start a new thread.

If you need more help starting a thread, you can post here.

---

