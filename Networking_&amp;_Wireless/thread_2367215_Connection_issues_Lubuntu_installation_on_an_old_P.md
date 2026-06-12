---
title: "Connection issues Lubuntu installation on an old PC"
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by abovethecloud on 2017-07-27
**Introduction**
I am new to the Linux world, so I apologise in advance if I am not explaining myself well or if I am doing something wrong.
I just recently managed to install the latest Ubuntu version (17.04, 64 bit) on a Lenovo PC just a couple years old.

I then decided to try and revive an old PC my parents had [I believe a MS-1012 with 2 GB of RAM and 1.6 GHz processor] by installing the latest compatible Lubuntu version (17.04, 32 bit). And that's where I encountered the most serious problems.


**The problems**

[LIST=1]
[*]Ethernet doesn’t work
[*]Wi-Fi, too, doesn’t work
[/LIST]
But Wi-Fi at least didn’t work under Windows too, so I bought a Wireless adapter [a TP-LINK TL-WN725N] which worked under Windows.


**The complications**
_On this old PC I am completely offline_ (this is the problem I want to solve), so I cannot download anything or install packages using apt-get.
Some essential (or so I think) commands are apparently not included in the latest Lubuntu installation, such as *make* or *ifconfig*.


**What I tried**

[LIST]
[*]Regarding Ethernet:
I tried a bunch of stuff I found using the magic of Google and Ubuntu forums, but ultimately I accomplished nothing, in part because many solutions required apt-get (remember: I am offline) and I think I miss many useful terminal commands.
[*]Regarding the not working Wi-Fi:
I tried installing the wireless adapter's manufacturer's drivers (by downloading them on the other PC and transferring them using an USB stick), but I needed the make command. Then I started searching for a way to install the make command (e.g. installing the build-essential package), but it is [s]impossible[/s] _probably incredibly difficult to do so while offline_. I tried following guides like this: [http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html](http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html) to download the .deb packages needed on the other Ubuntu laptop, but since the architecture is different (I also tried downloading the i386 packages) I could not install them (I got an “error while processing gdb”)
[/LIST]
I also tried other linux distributions (such as Puppy Linux, LXLE..), but they all had the same problems regarding Ethernet and Wi-Fi and many of them failed to install at all.


**Conclusion**
I am starting to lose hopes about being able to connect to the internet on this laptop using Linux. Any help would be greatly appreciated.
Thanks in advance!


Here the lshw (without the wireless adapter inserted into a USB port. Should I change that?):
```
computer    description: Hand Held Computer
    product: MS-1012
    vendor: MICRO-STAR INT'L CO.,LTD
    version: 0121
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: chassis=handheld cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: A1012IMS V2.50
          date: 02/22/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: CPU 1
          size: 798MHz
          capacity: 1596MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fbe80000-fbefffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fbe40000-fbe7ffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fbd80000-fbdfffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-19-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-19-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-19-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-19-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:01:03.0
                logical name: enp1s3
                version: 10
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:22 ioport:e800(size=256) memory:fbfffc00-fbfffcff memory:fbfe0000-fbfeffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4
                bus info: pci@0000:01:04.0
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=131
                resources: iomemory:b00202010-b0020200f irq:19 memory:80000000-80000fff ioport:e000(size=256) ioport:e400(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4.1
                bus info: pci@0000:01:04.1
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603010-b0060300f irq:20 memory:8c000000-8c000fff ioport:ec00(size=256) ioport:1000(size=256) memory:90000000-93ffffff memory:94000000-97ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:21 memory:fbfff000-fbfff7ff
           *-network:1 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: wlp1s9
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:fbffe000-fbffefff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:d000(size=256) ioport:cc00(size=64) memory:fbe3bc00-fbe3bdff memory:fbe3b800-fbe3b8ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:c800(size=256) ioport:c480(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MP0402H
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0-14
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=6a236583
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 37GiB
                capacity: 37GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2016-11-04 10:36:09 filesystem=ext4 lastmountpoint=/ modified=2016-11-04 17:54:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-11-04 11:03:19 state=mounted
        *-cdrom
             description: DVD writer
             product: DVDRW SOSW-852S
             vendor: Slimtype
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PES2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc

```

---

### Post by Autodave on 2017-07-27
16.04 is a long term service release. 17.04 has a service life of 6 months. So, I would get hold of 16.04 and try running a live session and see if the internet works there. I am betting it will. If it does, then install 16.04 and you'll be good for a few more years rather than a few more months.

I have 16.04 (Xubuntu) running on some real old machines with no issues. (And they are slower than your's and have less memory.) I am not that familiar with Lubuntu.

---

### Post by abovethecloud on 2017-07-27
Thanks for the reply!
In the meantime I did exactly try 16.04, but it gave me exactly the same issues.
Luckily I also found somewhere an Ethernet>USB adapter and manged to get the wired connection working (so, apparently, at least for the Ethernet it could be a mulfunctioning physical port), and then I could install the drivers for the TP-LINK device and (after some ordeal) I manged to get the Wi-Fi working.

Now I have a different problem: I try to connect to my home Wi-Fi but it keeps prompting me for the password every 30 seconds or so, never connecting in a loop.
Any ideas about that?

On a unrelated note, should I mark this thread as solved and open a new one specifically for this new problem, which is related even though not directly?

Thanks in advance.

---

### Post by BenginM on 2017-07-27
Salutations! and welcome to the forums.

you'll have a better chance receiving assistance if this post is on the Networking & Wireless section .. so lets wait for a forum staff to move this thread over there. or they may ask you to open a new one .. either way.. you'll need to run the wireless info script in this sticky [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) , and paste the result in the thread in a [CODE] tag .

---

### Post by wildmanne39 on 2017-07-27
*Thread moved to **Networking & Wireless**.*

---

### Post by BenginM on 2017-07-27
Thank you wildmanne39 :) 

So we're here now , looking at the output of lshw , we see

```

*-network:1 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
logical name: wlp1s9
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27

```

the card is shown as 'disabled' when the wireless switch or key combination is set to turn off the wireless .. but everything else is in place looks fine  driver's loaded, no missing firmware ,, what need to do now is to make sure the laptop wifi physical swtich is ON , or if the laptop doesn't have a physical one , look in the laptop's manual for a WiFi enable/disable function key/button.

then check with fkill to see if the wireless card is hardware/software blocked , in terminal run ~$ rfkill list all  , then you'll have to run: ran :~$ rfkill unblock all .. to unblock .

---

### Post by BenginM on 2017-07-27
as for the TP-LINK, it's the wireless N Nano USB adapter  ...

[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1)
[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2)

 one of these two , is in it !

while the usb adapter plugged in , run lsusb , and lsmod , uname -r .. 

 and post the result here in a [CODE] tag ..thanks!

---

### Post by abovethecloud on 2017-07-28
Thanks to wildmanne39 for moving the thread to a more appropriate location!

And thanks a lot to BeginM for the help.

Here we go:
[LIST]
[*]The result of the wireless info script: [http://paste.ubuntu.com/25189095/](http://paste.ubuntu.com/25189095/) 
[*]The output of *lsusb*: ```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``` 
[*]The output of *lsmod*: ```
Module                  Size  Used by
btrfs                1101824  0
xor                    28672  1 btrfs
raid6_pq              106496  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus                98304  0
hfs                    57344  0
minix                  36864  0
ntfs                  102400  0
msdos                  20480  0
jfs                   176128  0
xfs                  1085440  0
libcrc32c              16384  1 xfs
cfg80211              532480  0
8188eu                675840  0
snd_intel8x0           36864  1
snd_ac97_codec        106496  1 snd_intel8x0
ac97_bus               16384  1 snd_ac97_codec
snd_pcm                94208  2 snd_ac97_codec,snd_intel8x0
input_leds             16384  0
joydev                 20480  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
serio_raw              16384  0
pcmcia                 61440  0
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
yenta_socket           40960  0
snd_timer              28672  2 snd_seq,snd_pcm
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 yenta_socket,pcmcia,pcmcia_rsrc
snd                    65536  9 snd_seq,snd_ac97_codec,snd_timer,snd_rawmidi,snd_intel8x0,snd_seq_device,snd_pcm
soundcore              16384  1 snd
mac_hid                16384  0
cdc_ether              16384  0
usbnet                 36864  1 cdc_ether
r8152                  45056  0
autofs4                40960  2
i915                 1187840  5
i2c_algo_bit           16384  1 i915
drm_kms_helper        139264  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
firewire_ohci          36864  0
8139too                32768  0
drm                   303104  7 i915,drm_kms_helper
psmouse               122880  0
firewire_core          61440  1 firewire_ohci
8139cp                 28672  0
pata_acpi              16384  0
crc_itu_t              16384  1 firewire_core
mii                    16384  4 usbnet,8139cp,8139too,r8152
fjes                   61440  0
video                  40960  1 i915
``` 
[*]And, finally, of* uname -r*: ```
4.10.0-27-generic
``` 
[/LIST]

I should add the following:
[LIST]
[*]My system experienced a (non fatal) internal error while running sudo apt dist-upgrade 
[*]After getting the Wi-Fi running I tried connecting also to my personal hotspot using my phone and it worked. So the problem is only with my home Wi-Fi? No other device has ever had such problems 
[/LIST]

Thank you all!

P.S. I might be unable to answer promptly in the next few days, but I'll get back to try your suggestions as soon as I can

---

### Post by praseodym on 2017-07-28
The driver ipw2200 is blacklisted
```

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist [COLOR="#FF0000"]ipw2200[/COLOR]
```
Open the file with an editor as root
```

gksudo leafpad /etc/modprobe.d/blacklist.conf
```
remove that line, save, close the editor and reboot.

Edit: Change ipw2200 with 8139cp in that line. The LAN card loads two drivers.

---

### Post by abovethecloud on 2017-07-28
> **praseodym said:**
> The driver ipw2200 is blacklisted
Well, it was me who blacklisted it.
I followed a guide to get the TP-Link working: I installed the driver (*8188eu*), but the device still didn't work, so I searched and found a solution in a thread suggesting to disable the integrated driver (so I added the blacklist line) and it worked! The Wi-Fi started working (in the sense that I could finally see nearby Wireless networks and could connect to my personal hotspot) BUT I still was unable to connect to my home Wi-Fi due to the repeated request for the password.

> **praseodym said:**
> Change ipw2200 with 8139cp in that line. The LAN card loads two drivers.
Do you think this is an improvement over the solution above? In that case I would try that, but I now have another problem (sigh).

**New problem:**
When the TP-Link didn't work I followed that: [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8188EU-chipset-0bda:8179-](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8188EU-chipset-0bda:8179-). Then I blacklisted the *ipw2200* and the Wi-Fi situation improved. After some some reboots, though, I find that the *8188eu* driver is no more installed on my system, it just disappeared! And consequently the Wi-Fi stopped working. Any ideas why?(In the meantime I'll see if I can install it again)

Thanks in advance!

---

### Post by abovethecloud on 2017-07-28
Update:
It's worth mentioning that the battery of this PC doesn't work anymore: if it is disconnected form the power cable, the computer immediately shuts down. Since I left the computer for some hours without power, I believe that's what caused the loss of the driver in some way, also the clock was reset to default time. I still don't know the precise cause. Is there any way to prevent it in the future?

---

