---
title: "GRUB loading, Error 18"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by abnr on 2009-10-30
I installed Ubuntu 9.04 on my desktop yesterday. After the ejection of the CD, I pressed Enter. The  message showed "GRUB Loading Stage 1.5, GRUB loading, please wait....
Error 18.   The OS never opened. What have I done wrong? How can not correct the problem so that the Ubuntu opens? Any help is appreciated. I am a novice with Linux OS.

---

### Post by phidia on 2009-10-30
Probably you need to use the livecd to reinstall grub

> sudo grub-install /dev/hda
That should work as long as you are using your first hard drive to hold the MBR.
See the grub guide [here]("https://help.ubuntu.com/community/GrubHowto").

---

### Post by kansasnoob on 2009-10-30
Do you know what size your hard drive is?

This is a bit of a long read but should help you out:

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

If you need further assistance please boot the Live CD & post the output from terminal of:

```
lshw
```

(That's Lower case LSHW), and also:

```
sudo fdisk -lu
```

---

### Post by abnr on 2009-10-30
Thanks for the response. The PC does not boot so I can not use the terminal. I used the live CD when I installed the OS. The Ubuntu is installed on the HD. It just does not boot.

---

### Post by teward on 2009-10-30
no, they mean **use the terminal on the live CD.**

So load the Live CD, and do all the commands they said to do while running Ubuntu off the CD.

---

### Post by abnr on 2009-10-30
Thanks. The hard drive is 40 GB Western Digital. No software other than Ubuntu 9.04 is installed on the drive.

---

### Post by kansasnoob on 2009-10-30
Can you not boot the Live CD choosing to "Try Ubuntu with no changes to disc", and post the output of those two commands?

lshw will show us some of the motherboard specs and fdisk -lu will show us what your exact partitioning layout is.

---

### Post by primzi on 2009-11-24
I have the same problem:

can someone help?

P

ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MiB
     *-cpu
          product: Intel(R) Pentium(R) III Mobile CPU      1133MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 1130MHz
          capacity: 1130MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=9
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
           *-pcmcia
                description: CardBus bridge
                product: RL5c475
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00603020-b0060301f
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 42
                serial: 08:00:46:4d:df:8d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=83.84.159.186 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:13:b0:63:14:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12e0f221

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   307339514   153669726    7  HPFS/NTFS
/dev/sda2       307339515   312576704     2618595    5  Extended
/dev/sda5       307339578   312223274     2441848+  83  Linux
/dev/sda6       312223338   312576704      176683+  82  Linux swap / Solaris

---

### Post by kansasnoob on 2009-11-24
@ primzi,

Is yours a grub error 18? Whether or not that's correct please boot your Ubuntu Live CD choosing "Try without changes .......", run the Boot Info Script, and post the results as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That should give us the info we need to proceed.

---

