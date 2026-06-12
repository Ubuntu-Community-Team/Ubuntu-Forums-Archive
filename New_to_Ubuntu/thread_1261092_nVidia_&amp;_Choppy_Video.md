---
title: "nVidia &amp; Choppy Video"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by mapes12 on 2009-09-08
I've searched around for a fix for this but drawn a blank. I'm running 9.04 with a decent video card that has 256MB of onboard memory. The card worked fine in an XP box but on this Ubu box streaming web video like BBC iPlayer is quite choppy, so much so that it's unwatchable in full screen mode.

I've activated the recommended driver - see screenshot.

I've been into System>Admin>NVIDIA X Server Settings - see screenshot - but haven't a clue what, if anything, I need to change.

I have ubuntu-restricted-extras installed and the codecs from Medibuntu.

I've also attached a screenshot of the FF plugins installed.

Here's my video card:
 > *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidiaAny ideas??

---

### Post by DrMelon on 2009-09-08
Flash still has problems on Ubuntu, I'm afraid. :(
Nothing to do with the graphics card AFAIK.

---

### Post by Jazzy_Jeff on 2009-09-08
> **DrMelon said:**
> Flash still has problems on Ubuntu, I'm afraid. :(
Nothing to do with the graphics card AFAIK.

Flash runs great on my systems. No problems at all.

We need a little more info from you. What version of 9.04 are you running? 32 bit or 64 bit. Also what are your system specs..(ram, processor..etc.)

---

### Post by LowSky on 2009-09-08
try the newest driver (32BIT, 64 is available)
[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

it will require you to uninstall the ubuntu one first, and install the new one by way of the command line. If your not used to doing that this should help... please back up everything before hand

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by mapes12 on 2009-09-08
> **Jazzy_Jeff said:**
> Flash runs great on my systems. No problems at all.

We need a little more info from you. What version of 9.04 are you running? 32 bit or 64 bit. Also what are your system specs..(ram, processor..etc.)Here's the machine spec. It's 32 bit:

```
mark@ubuntu-desktop:~$ sudo lshw
[sudo] password for mark: 
ubuntu-desktop            
    description: Desktop Computer
    product: K7S41
    vendor: American Megatrends Inc.
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: K7S41
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P2.30 (05/23/2006)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket-A
          size: 1150MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 1002MiB
     *-pci
          description: Host bridge
          product: 741/741GX/M741 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
           *-disk:0
                description: ATA Disk
                product: ST3120022A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JT55RFM
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007ce1c
              *-volume
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 15GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 95GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 956MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVDR1628P1
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: Q1.1
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: ExcelStor Techno
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: V32O
                serial: VNR20EG2B2H3CB
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1bfd1bfc
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: af2b8a9e-c4ac-43c1-870f-65f285f11e73
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-07-27 16:55:40 filesystem=ext3 modified=2009-09-07 18:56:34 mounted=2009-09-07 16:23:10 state=clean
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:13:8f:a5:59:cc
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.71 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 5880B [AudioPCI]
             vendor: Ensoniq
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12 module=snd_ens1371
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:f1:c8:6c:3e:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
mark@ubuntu-desktop:~$ 
```

---

### Post by mapes12 on 2009-09-08
I installed the NVIDIA 185 driver using this easy guide: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

The keyring Terminal command failed so when the install said that it could not authenticate, proceed Y/n I just pressed Y and it installed. I've attached a screenshot.

Web streaming playback is better but not as good as when the video card was in an XP box.

---

### Post by NoaHall on 2009-09-08
I'd install the flash from the official website. If you have 64 bit, anyway, because there's a alpha which has better playback than the 32 bit release.

---

### Post by zhanglini on 2009-09-08
I used to have choppy videos on my 5 year old laptop when I was using XP, I finally fixed it by raising the priority of the program (say VLC).  Videos were very fluid!
You can try to do the samething here, by using "renice" to change the nice value of the app --- it hasn't worked as great for me though.

---

### Post by misfitpierce on 2009-09-08
Flash 10 works great on my Ubuntu Jaunty/9.04 system using ATI opensource driver so I'd say try one of the other Nvidia drivers possibly and see the outcome as well on those.

---

### Post by mud2005 on 2009-11-15
I had extremely choppy video in Hulu in fullscreen, but I found a fix that worked awesome for me.
I have Nvidia 8600gt video card
I found the fix on these forums from user named Normad, Thanks Normad!!
> It seems I just found out what was causing my problem.
The problem library was 'libglx'. Both xserver-xorg-core and nvidia driver have their own libglx.so and I was getting bad performance with native libgxl. I've reinstalled nvidia drivers and I'm back to happy days again.
I think I'll put xserver-xorg-core on hold until better solution arrives.

This worked perfectly for me, just goto synaptic click on nvidia-glx-180 and mark reinstall, then apply
Bam, now I can even watch in HD fullscreen in hulu with no choppiness at all.
cheers \\:D/
pass it on if it works for u

---

### Post by mud2005 on 2009-11-15
well I guess I posted too soon. Now my video is choppy again.
I'm not sure what happened, it does seem improved over what it was before, but it's still not perfect. I'm going to do further research and see if I can fix it.
Sorry for posting before testing enough :sad:

---

### Post by wojox on 2009-11-15
Hulu is all Flash. Try this 

```

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

```

```
gksudo gedit /etc/X11/xorg.conf
```

```
Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

---

### Post by clhsharky on 2009-11-15
HI mapes12

Are you still with us? If you are, I see your Athlon XP has under clocked itself and not running at full power. It will make your system slow and under powered. Battery or bad shut down,can make this happen.

>      *-cpu
          description: CPU
          product: AMD Athlon(tm) XP
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket-A
  >---->  size: 1150MHz   >--should be 1833–2333 MHz
          capacity: 3GHz
          width: 32 bits
  >---->  clock: 100MHz    >--should be 166/200 MHz

          
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
     >-----> size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified


cache:1 - tell me it a Barton
clock: 100MHz - is safe start up
size: 1150MHz - no XP Barton run at that speed

> Specifications:
Barton (130 nm)

    * L1-Cache: 64 + 64 KiB (Data + Instructions)
    * L2-Cache: 512 KiB, fullspeed
    * MMX, 3DNow!, SSE
    * Socket A (EV6)
    * Front side bus: 166/200 MHz (333/400 MT/s)
    * VCore: 1.65 V
    * First release: February 10, 2003
    * Clockrate: 1833–2333 MHz (2500+ to 3200+)
          o 166 MHz FSB: 1833–2333 MHz (2500+ to 3200+)
          o 200 MHz FSB: 2100, 2200 MHz (3000+, 3200+)



Don't worry, reset motherboard BIOs to default, and maybe replace system battery. Check memory to see if DDR333 or DDR400.

[http://en.wikipedia.org/wiki/Athlon](http://en.wikipedia.org/wiki/Athlon)

Good Luck

---

### Post by mud2005 on 2009-11-15
I just found out the same thing, my cpus were scaling and causing the choppiness. I added the cpu frequency scaling monitor to the panel and left clicked on it and selected "performance" now my cpus saty at 3.20 GHz and FLASH RUNS FLAWLESSLY
\\:D/
now to crash as I stayed up till almost 4am working on this

---

