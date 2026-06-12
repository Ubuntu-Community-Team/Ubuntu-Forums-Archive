---
title: "Wireless is configered with ndiswrapper, but doesnt appear?"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by jojo21 on 2008-10-12
Edit: Ah damn. Forget it. Looks like its because I installed the 32bit drivers on a 64bit distro. I really hop SIS has 64bit drivers. I have a feeling I'm about to be screwed on this though. :(

Edit 2: Yup. No 64bit driver. 

Edit 3: So should I install 32bit Ubuntu? What do I lose by using it versus the 64bit one? Or can anyone reccomend a USB or EX card for WIFI that works natively with Linux. A cheap one?

Hi, I have a Fujitsu-Siemens Amilo Li 1818. After getting frustrated as hell with Vista that it came with and being unable to easily install XP I decided to give Linux another try and see if it had improved. (You may notice I registered almost exactly two years ago. Thats when I last tried and gave up on Linux within a day. Now I'm a little older, wiser and with more patience. :) )

So I've installed Ubuntu 8.04, and so far I love it. No lag or sluggish system resources that make my Core 2 Duo behave like a Pentium 2. A little pissed that it came without any codecs, as I dont have internet where I'm staying so I couldnt watch any video or listen to mp3's for a few days until I came to my parents and could download the codecs and VLC. 

Only major problem is the wireless. I followed the instructions in this page: [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLi1818](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLi1818)
and everything seemed to go smoothly, except that after following all the steps I dont have a wireless option in the Networking program. If I right click the icon on the taskbar I see "Edit Wireless Networks" but that provides no options to scan for access points. If I open the Terminal and type "ndiswrapper -l" it seems to show that the XP driver for the wireless is installed: 
```
sis163u : driver installed
	device (0BF8:100F) present

```
But "lshw" doesnt seem to show it:
```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1526MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1733MHz
          capacity: 1733MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: eth0
                version: 10
                serial: 00:03:0d:59:e1:b5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.4 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```
And if I try "sudo iwlist wlan0 scan" it just says ```
wlan0     Interface doesn't support scanning.
```

Basically, after following the instructions this step > 
Next we do the dependencies and load up the ndiswrapper kernel module. Run: sudo depmod -a followed by sudo modprobe ndiswrapper. This will load everything and allow you to use NetworkManager to check if any wireless networks are available. Note: Rebooting will drop the module.  Doesnt produce the desired result of showing a wireless option in Network Manager.

Help? Thanks!

---

### Post by parajuito on 2008-10-12
you should install build-essential first i think :S

sudo aptitude update
sudo aptitude install build-essential

---

### Post by caljohnsmith on 2008-10-12
According to your lshw output, Ubuntu is not seeing your wireless card, only your ethernet card, so I doubt installing 32-bit Ubuntu is going to help you. Did you have wireless working in Vista at all?

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> According to your lshw output, Ubuntu is not seeing your wireless card, only your ethernet card, so I doubt installing 32-bit Ubuntu is going to help you. Did you have wireless working in Vista at all?
Of course, it worked perfectly.

---

### Post by caljohnsmith on 2008-10-12
So your wifi is a PCI card and not USB, correct? How about posting:
```
lspci
```

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> So your wifi is a PCI card and not USB, correct? How about posting:
```
lspci
```

Right, its the mini-pci built into the laptop. (I assume its mini-pci. I havent actually opened it up to check.) Thanks for the help attempts by the way. :)

Here's my lspci output: Again, doesnt seem to exist, does it?
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by caljohnsmith on 2008-10-12
I don't know what to say, because lspci is not showing your wireless card either; I didn't really expect it to be different than lshw, but I just wanted to make sure. Do you have any Linux Live CDs other than the Ubuntu one? I would boot one of those and see if by chance another distro can see your wireless card, and try a 32-bit distro version to see if that is the issue. I'm wondering if the wireless card got jostled around or something and is no longer tightly connected, because I find it hard to believe that it worked in Vista and yet Ubuntu doesn't even think it exists.

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> I don't know what to say, because lspci is not showing your wireless card either; I didn't really expect it to be different than lshw, but I just wanted to make sure. Do you have any Linux Live CDs other than the Ubuntu one? I would boot one of those and see if by chance another distro can see your wireless card, and try a 32-bit distro version to see if that is the issue. I'm wondering if the wireless card got jostled around or something and is no longer tightly connected, because I find it hard to believe that it worked in Vista and yet Ubuntu doesn't even think it exists.
I have a Knoppix live cd and another distro on a bootable USB. I'll check both tonight and I'll reply with the answers tomorrow.

---

### Post by jojo21 on 2008-10-12
Well just to make sure, I opened the bottom, the wifi is a mini-usb and it is attatched correctly.

---

### Post by caljohnsmith on 2008-10-12
> **jojo21 said:**
> Well just to make sure, I opened the bottom, the wifi is a [COLOR="Blue"]mini-usb[/COLOR] and it is attatched correctly.
You said in post #6 that it was a mini-pci? How about for completeness post:
```
lsusb
```

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> You said in post #6 that it was a mini-pci? How about for completeness post:
```
lsusb
```
Sorry, slip of the finger. It is indeed mini-pci.

Also, I've found a blank cd so I'm downloading the latest Knoppix version now. Should have a full report in a few minutes. What commands should I be checking with?

---

### Post by caljohnsmith on 2008-10-12
> **jojo21 said:**
> 
Also, I've found a blank cd so I'm downloading the latest Knoppix version now. Should have a full report in a few minutes. What commands should I be checking with?
Probably in Knoppix you'll need to switch to root user first instead of using sudo, so do:
```
su -
lshw -C network
```
Or if lshw for some reason isn't available, just use "lspci" again.

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> Probably in Knoppix you'll need to switch to root user first instead of using sudo, so do:
```
su -
lshw -C network
```
Or if lshw for some reason isn't available, just use "lspci" again.
As you can see lshw didnt work, but heres the lspci results:
```
root@Knoppix:~# lshw -c network
-su: lshw: command not found
root@Knoppix:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

If I open the knoppix wireless utility it says "eth0 found!" and asks me how to install the drivers, including giving me ndiswrapper as an option. If I try that it disables the ethernet, and I have to reboot to get it back on. I dont know Knoppix very well, even less than I know Ubuntu.

---

### Post by caljohnsmith on 2008-10-12
> **jojo21 said:**
> 
```

[COLOR="Blue"]06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/COLOR]

```

If I open the knoppix wireless utility it says "eth0 found!" and asks me how to install the drivers, including giving me ndiswrapper as an option. If I try that it disables the ethernet, and I have to reboot to get it back on. I dont know Knoppix very well, even less than I know Ubuntu.
Unfortunately, like I suspected, "lspci" is only finding your ethernet card which would be eth0. I don't see any mention of a wireless card, so I don't know what else to say. For whatever reason your wireless card is not showing up at all (at least that I can tell).

---

### Post by jojo21 on 2008-10-12
> **caljohnsmith said:**
> Unfortunately, like I suspected, "lspci" is only finding your ethernet card which would be eth0. I don't see any mention of a wireless card, so I don't know what else to say. For whatever reason your wireless card is not showing up at all (at least that I can tell).
Surely I cant be the first to have this error? My card works perfectly under Vista but isnt even detected under Linux? Guess we're at a standstill. Thanks anyway.

---

### Post by Yellow Pasque on 2008-10-13
UniX IS CaSe SenSITiVe
```
sudo lshw -**C** network
```

---

### Post by jojo21 on 2008-10-13
> **Temüjin said:**
> UniX IS CaSe SenSITiVe
```
sudo lshw -**C** network
```
Moot point. Either way the card doesnt show.

---

### Post by Yellow Pasque on 2008-10-13
> **jojo21 said:**
> Moot point. Either way the card doesnt show.
True, but try to remember that for future use. ;)

---

### Post by Liametc on 2008-10-18
yeah im having the same problem. just tried to load the ralink drivers for my edimax wireless card. but as soon as i go to load the drivers, it says it cant find the interface and doesnt go any further. 

the card is not listed when i type in lspci or lshw -C network

---

### Post by Alonsus on 2008-10-18
Same problem here, the card is a D-Link DWA-552. Can others with this problem do...

dmesg | grep allocate

and see if the line "can't allocate mem resource" shows up?

---

### Post by jojo21 on 2008-10-26
I ended up installing the 32bit version, and now it works perfectly.

---

