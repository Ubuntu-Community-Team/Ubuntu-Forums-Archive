---
title: "Davicom DM9102F NIC not recognized in ubuntu 14.04 LTS"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by Jonathan Precise on 2014-08-09
Hello ubuntu forums community!

I had a PC with 512 MB RAM, which had Windows 8 (Yes, with 512 MB RAM it would work, but way too slow.......................................) and Ubuntu 12.04 LTS - based distro (Zorin OS 6 for the fact). The problem with the NIC can be found [here]("http://ubuntuforums.org/showthread.php?t=2154753").

However, I recently swapped a working NIC from one of my PCs and made a RAM upgrade. Now I have roughly 1 GB of RAM, and I wanted to put the computer to use as a Proxy server. I tried downloading ubuntu server on it, but it just didn't install correctly, so I ended up installing ubuntu desktop and Squid.

Squid requires for 2 NICs, so I decided to put the Davicom one to work. Unfortunately, now it doesn't even recognize my NIC as even existing:

```
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c5:ed:5a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:b800(size=256) memory:dfeffc00-dfeffcff
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# 
```

(Please see screenshot as well)

Any ideas on how to revive this card?

---

### Post by praseodym on 2014-08-09
Hi,

first: Reset the BIOS to default settings.

second: please show the outputs now of```

lspci -nnk
lsusb
pccardctl info
lsmod
iwconfig
rfkill list
```

---

### Post by Jonathan Precise on 2014-08-09
Hello!

I could not find the "Reset BIOS" options, but I found "Load optimal defaults". So after doing that, my BIOS started recognizing a floppy drive which doesn't even exist! Ubuntu also says now that there is a floppy drive, but when I mount it, an error says that I don't have permission to access it?!?!!???? [SIZE=1]My PC is weird...[/SIZE]

As for the network issue, it still doesn't recognize my NIC.

Outputs of the commands (I ran them all as ro):

```
ownerp@CASA-PROXY-SERVER-LINUX-UBUNTU:~$ sudo -i
[sudo] password for ownerp: 
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580]
	Subsystem: Intel Corporation Device [8086:474e]
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581]
	Kernel driver in use: pcieport
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
	Subsystem: Intel Corporation Device [8086:e203]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 03)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
	Subsystem: Intel Corporation Device [8086:474e]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
	Subsystem: Tul Corporation / PowerColor Device [148c:2089]
	Kernel driver in use: radeon
01:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE] [1002:5b70]
	Subsystem: Tul Corporation / PowerColor Device [148c:2088]
06:01.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
	Subsystem: D-Link System Inc DFE-538TX 10/100 Ethernet Adapter [1186:1300]
	Kernel driver in use: 8139too
06:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
	Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044]
	Kernel driver in use: firewire_ohci
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# pccardctl info
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342206  10 bnep,rfcomm
radeon               1420526  4 
snd_hda_codec_realtek    55125  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
ttm                    72698  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
drm_kms_helper         47182  1 radeon
drm                   244037  6 ttm,drm_kms_helper,radeon
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
gpio_ich               13229  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_algo_bit           13197  1 radeon
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
lpc_ich                16864  0 
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
tulip                  58400  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
btrfs                 822702  1 
xor                    26221  1 btrfs
raid6_pq               97455  1 btrfs
libcrc32c              12543  1 btrfs
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
8139too                32571  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 8139too
floppy                 55416  1 
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# rfkill list
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# 
```

I *think* this is the problem:
[COLOR="#FF0000"]```
lo        no wireless extensions.

eth0      no wireless extensions.

```[/COLOR]

What about eth1?

I'm totally confused by this. Someone please enlighten me on what to do next.

---

### Post by Jonathan Precise on 2014-08-09
Hello?

---

### Post by praseodym on 2014-08-09
Obviously, nothing detected. Does Win shut down the card?

---

### Post by Jonathan Precise on 2014-08-09
> **praseodym said:**
> Does Win shut down the card?

Sorry, I don't understand. Do you mean if windows  shutdown the card? I don't have windows anymore.

---

### Post by Jonathan Precise on 2014-08-09
> **praseodym said:**
> Obviously, nothing detected. Does Win shut down the card?

Sorry, I don't understand. Do you mean if windows shutdown the card? I don't have windows anymore.

---

### Post by Jonathan Precise on 2014-08-09
100 views, no answer. What other information do I have to provide?

Thanks in advance.

---

### Post by praseodym on 2014-08-10
Obviously, its not recognized. Do you have a chance to upgrade the BIOS?

---

### Post by Jonathan Precise on 2014-08-10
Hello!

I'll try to upgrade it ASAP, will post when done.

---

### Post by Jonathan Precise on 2014-08-10
Booting from the ISO results in ```
Interrupt, divide by zero, stack:
[COLOR="#FF0000"]abcd efgh ijkl mnop
qrst uvwx yzAB CDEF[/COLOR]
```

The items in [COLOR="#FF0000"]red[/COLOR] are some 4-character items that I can't understand or remember. Is there another way to fix this since update fails?

---

### Post by praseodym on 2014-08-10
Can you boot at all?

---

### Post by Jonathan Precise on 2014-08-10
I can't boot to the CD. However I can still boot normally to ubuntu.

---

### Post by praseodym on 2014-08-10
Sorry, I'm running out of ideas

---

### Post by Jonathan Precise on 2014-08-10
[NOPARSE]:([/NOPARSE]

---

### Post by Jonathan Precise on 2014-08-20
Ok. I [SIZE=5]FINALLY[/SIZE] got two NICs working!

On another PC, which has an integrated NIC, I disconnected the working NIC from the original server and connected them to them to the other PC. I swapped the HDDs so that the Ubuntu installed on the original server would be moved to the other PC. Now that PC is my new server now.

In other words, NEVER BUY DAVICOM NICs EVER AGAIN!!! They cause headaches.

Output of lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:7d:78:da:c0
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.110 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:9000(size=256) memory:db010000-db010fff memory:db000000-db00ffff memory:db020000-db02ffff
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c5:ed:5a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:a000(size=256) memory:db100000-db1000ff
```

*I have made another thread with squid3 setup to not post more than one problem in one thread. It can be found [here]("http://ubuntuforums.org/showthread.php?t=2240553&p=13103661#post13103661").*

*Marked as solved.*

---

