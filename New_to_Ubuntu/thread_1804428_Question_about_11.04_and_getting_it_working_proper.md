---
title: "Question about 11.04 and getting it working properly."
date: 2011-07-14
forum: New to Ubuntu
---

### Post by zirgut on 2011-07-14
Question about 11.04 and getting it working properly. 
I upgraded to  11.04 sometime ago and it never has worked properly. In fact it would  not install the new look desk top. I also run Windows and have been  trying to sort things out, ha ha.  When I first started using ubuntu I  partitioned the hard drive. I presumed that I had installed  the old ubuntu on that. I also presumed that the 11.04 downloaded on to the  windows area of the hard drive. I have deleted the ubuntu installed on  Windows and on checking the partitions via windows find that the  partition designated for ubuntu has 100% free space. In short I have a  mystery. the new version of ubuntu is still running but I am not sure  where from. I would like to have ubuntu running properly, to be able to  play videos and have sound, non of which I can at the moment. I look  forward to hearing your suggestions. Thanks

---

### Post by MG&amp;TL on 2011-07-14
I hate to be disrespectful, but it helps if we can have more specifics, it also means you get your problem sorted faster.

What kind of error messages do you get?
What sort of problems do you have?
How exactly are you trying to sort things out on windows?
What graphics card do you have?

The bit about partitions...when you upgraded, did you use a disk, or did you upgrade via update manager? If you upgraded via update manager, it definitely shouldn't have installed over the windows partition. If you installed via disk, and selected the 'erase ubuntu <oldversion>' option, hen it shouldn't have done either.

Does windows still boot?

11.04 does have some bugs, but I'm hoping they'll be ironed out by 11.10 or 12.04 :D

---

### Post by zirgut on 2011-07-14
> **MG&TL said:**
> I hate to be disrespectful, but it helps if we can have more specifics, it also means you get your problem sorted faster.

What kind of error messages do you get?
What sort of problems do you have?
How exactly are you trying to sort things out on windows?
What graphics card do you have?

The bit about partitions...when you upgraded, did you use a disk, or did you upgrade via update manager? If you upgraded via update manager, it definitely shouldn't have installed over the windows partition. If you installed via disk, and selected the 'erase ubuntu <oldversion>' option, hen it shouldn't have done either.

Does windows still boot?

11.04 does have some bugs, but I'm hoping they'll be ironed out by 11.10 or 12.04 :D
Sorry I thought I was being specific. That is why I posted on absolute beginner. The main problem, well only problem so far is that there is no sound and videos don,t play and I don't get the new desk top. It is a while since I installed it and now cannot remember the wording given why the new look would not be used and I had to remain with the classic. I have a feeling it was something to do with available space but not certain. 
I thought about removing the partition on windows and attempting a reinstallation of ubuntu but did not because I have no idea whether that would sort the problem. I think the grapphics card is Nvidia but not certain. Second hand Dell computer off ebay you see.
I did make a disc when I upgraded but did not select erase ubuntu old version as far as I can remember. 
Windows still boots but very slowly

---

### Post by grahammechanical on 2011-07-14
Try going to Additional Drivers and activating the recommended drivers. Then restart then at the log in screen click your user name and look at the bottom panel. On the right there will be a menu. Select Ubuntu and that will be the new Unity user interface.

If after activating additional drivers you see a message that says the driver is activated but not in use. do not believe this message. The driver is in use. The message is wrong. A similar message that there are no proprietary drivers in use on the system is also wrong.

The install would have put an icon on the top panel with a message to indicate additional drivers are available. Ubuntu is open source and does not install proprietary drivers unless instructed by the user to do so. I have an Nvidia card and I had the same message as you and I am now running Unity.

Regards.

---

### Post by MG&amp;TL on 2011-07-15
Yep, install the drivers, and run update manager.

---

### Post by zirgut on 2011-07-15
> **grahammechanical said:**
> Try going to Additional Drivers and activating the recommended drivers. Then restart then at the log in screen click your user name and look at the bottom panel. On the right there will be a menu. Select Ubuntu and that will be the new Unity user interface.

If after activating additional drivers you see a message that says the driver is activated but not in use. do not believe this message. The driver is in use. The message is wrong. A similar message that there are no proprietary drivers in use on the system is also wrong.

The install would have put an icon on the top panel with a message to indicate additional drivers are available. Ubuntu is open source and does not install proprietary drivers unless instructed by the user to do so. I have an Nvidia card and I had the same message as you and I am now running Unity.

Regards.
Many thanks. I now have the unity desktop. Will now check for video and sound playing. 
Regards
Zirgut

---

### Post by zirgut on 2011-07-15
Ok still videos on yahoo are not playing and there is no sound. Solutions are still being sought.
Thanks

---

### Post by alphacrucis2 on 2011-07-15
> **zirgut said:**
> Ok still videos on yahoo are not playing and there is no sound. Solutions are still being sought.
Thanks

```
sudo apt-get install ubuntu-restricted-extras
```

See this: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

You may also want into install additional codecs from medibuntu

[http://medibuntu.org/]("http://medibuntu.org/")

Oh and don't forget - install the firefox addon called Flash-Aid.

---

### Post by zirgut on 2011-07-15
> **alphacrucis2 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

See this: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

You may also want into install additional codecs from medibuntu

[http://medibuntu.org/]("http://medibuntu.org/")

Oh and don't forget - install the firefox addon called Flash-Aid.
Hi,
Many thanks for all that help. I got there in the end and video and sound is present. While you are there I have one more issue which I fear is me being really obtuse. I have tried to play this teach yourself  French CD Rom. It has come up on the side menu as being loaded. Then when I click on it this box comes up with all the different elements of the software. How do I actually get it to play? How do I use it?
Regards
Zirgut

---

### Post by wildmanne39 on 2011-07-15
Hi, is this a program written for windows? if so you might can play it in wine, if not wine virtualbox.

---

### Post by Skizzigh on 2011-07-16
hi im pretty new at this ubuntu thing im wanting to use it more but having a problem installing my nvidia 9800gtx+ driver when i install the current driver from (sysmtem>admin>additional drivers) when i reboot i will just get my wallpaper ill have a little pop up show my wifi connects i can right click and get options, my friend said my unity isnt loading properly i was wondering if anyone knew of a fix please help!

---

### Post by wildmanne39 on 2011-07-16
> **Skizzigh said:**
> hi im pretty new at this ubuntu thing im wanting to use it more but having a problem installing my nvidia 9800gtx+ driver when i install the current driver from (sysmtem>admin>additional drivers) when i reboot i will just get my wallpaper ill have a little pop up show my wifi connects i can right click and get options, my friend said my unity isnt loading properly i was wondering if anyone knew of a fix please help!Hi, did you see a message that said loading classic because you can not run unity? Can you post a screenshot of the desktop?

Run these commands in a terminal
```
sudo lshw

```
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Skizzigh on 2011-07-18
> **wildmanne39 said:**
> Hi, did you see a message that said loading classic because you can not run unity? Can you post a screenshot of the desktop?
 
Run these commands in a terminal
```
sudo lshw

```
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
 
no i ddint get anymessage about loading classic when i first booted ubuntu i installed the recoommend driver for my nvida (it had 3 choices 173, current, and beta) then i made me reboot when i do all i see is my wallpaper a little pop up showing my wif connected and if i right click i get the normal options i just dont have the bar at the top or bottom so then i have to ctrl alt f1 and remove the driver i installed and i tried all the drivers but the beta one if i dont install the drives everythging works fine i just can utilize my 2nd monitor.
 
any more infor you have or anything u think i should try let me know im really desperate for help
thanks for your time in your reply i appreciate it

---

### Post by wildmanne39 on 2011-07-18
Hi, run those commands in my previous post it might help us to help you and post them here by following the directions in the previous post.

---

### Post by Skizzigh on 2011-07-18
sorry im on it should i try it before or after i install the driver?

---

### Post by wildmanne39 on 2011-07-18
> **Skizzigh said:**
> sorry im on it should i try it before or after i install the driver?
Hi, do it after and if you have installed more then one driver open synaptic and type in nvidia and make sure there is only one installed, if there is more then one right click on it and choose remove completely.

---

### Post by Skizzigh on 2011-07-18
> **wildmanne39 said:**
> Hi, do it after and if you have installed more then one driver open synaptic and type in nvidia and make sure there is only one installed, if there is more then one right click on it and choose remove completely.

maybe im stupid or confused, cause after i install the driver and i reboot i cant access anything after it reboots i dont have the "applications places or system" options at the top or should i not reboot?

---

### Post by Skizzigh on 2011-07-18
#[skyler@ubuntu:~$ sudo /usr/lib/nux/unity_support_test -p
```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GTX/9800 GTX+/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
skyler@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   336693  1 
binfmt_misc            17565  1 
nvidia              10709116  40 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_ca0106             44783  2 
snd_ac97_codec        134270  1 snd_ca0106
snd_hwdep              13604  1 snd_hda_codec
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  4 snd_hda_intel,snd_hda_codec,snd_ca0106,snd_ac97_codec
snd_seq_midi           13324  0 
ppdev                  17113  0 
snd_rawmidi            30486  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
rt61pci                27888  0 
psmouse                73535  0 
rt2x00pci              14322  1 rt61pci
rt2x00lib              49235  2 rt61pci,rt2x00pci
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
mac80211              294370  2 rt2x00pci,rt2x00lib
serio_raw              13166  0 
joydev                 17606  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt61pci
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  19 snd_hda_codec_realtek,snd_hda_intel,snd_ca0106,snd_hda_codec,snd_hwdep,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             36959  1 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_ca0106,snd_pcm
nv_tco                 13603  0 
i2c_nforce2            13058  0 
lp                     17825  0 
asus_atk0110           17976  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
usb_storage            53538  0 
firewire_core          62646  1 firewire_ohci
uas                    17996  0 
crc_itu_t              12707  2 rt61pci,firewire_core
ahci                   25951  0 
forcedeth              63555  0 
sata_nv                32054  1 
pata_amd               14130  0 
libahci                26642  1 ahci
skyler@ubuntu:~$ ]
```

well never mind i just rebooted in ubuntu normal and its working now

---

### Post by flabden on 2011-07-18
Hey wildmanne39 it looks like I am having the same problems as skizzigh.  Except that when booting to 11.04 it goes to a black screen with a blinking cursor in the upper left hand side.  I have been looking on several forums and I think it may have to do something to do with the driver for nvidia.  I was able to access grub and and go to recovery mode and run in failsafex.  I changed my log in from ubuntu to ubuntu classic, since there may be a bug with unity.  Still a black screen.  So, I switched to xubuntu, black screen.  Switch to xfce, black screen.  I like all the interfaces, but ubuntu classic the best.  I just can't boot.  I ran the commands you gave in a post and here is what I got

```
  description: Desktop Computer
    version: 0nB1211RE101EXPL410
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=6097F424-1BD6-D811-981D-F138A186D363
  *-core
       description: Motherboard
       product: Explorer4
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.xx
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.06
          date: 08/31/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP  3200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          capacity: 2333MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM 100 MHz (10.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 128 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM 100 MHz (10.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MiB
             width: 128 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:f4000000-f7ffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:10 ioport:ec00(size=32)
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fe700000-fe700fff
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:fe900000-fe900fff
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fea00000-fea000ff
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth1
             version: a1
             serial: 00:0e:a6:c1:7c:2f
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.3 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:22 memory:fe800000-fe800fff ioport:e880(size=8)
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fb700000-fb8fffff memory:eb000000-eb3fffff
           *-multimedia:0
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:d880(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:dc00(size=8)
           *-multimedia:1
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=bttv latency=64 maxlatency=40 mingnt=16
                resources: irq:19 memory:eb200000-eb200fff
           *-multimedia:2 UNCLAIMED
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: 7.1
                bus info: pci@0000:01:07.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
                resources: memory:eb300000-eb300fff
           *-network
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 00
                serial: 00:00:e8:66:05:6e
                width: 32 bits
                clock: 33MHz
                capabilities: rom ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
                resources: irq:18 ioport:d800(size=32) memory:fb800000-fb807fff
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi1
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800BB-22JH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM92606684
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00082456
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: af4046de-ffef-4ee3-b6e5-6e7e081bf513
                   size: 4767MiB
                   capacity: 4767MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 69GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H22L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-firewire
             description: FireWire (IEEE 1394)
             product: nForce2 FireWire (IEEE 1394) Controller
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fe500000-fe5007ff memory:fe400000-fe40003f
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fb900000-fdafffff memory:eb400000-f35fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV18 [GeForce4 MX - nForce GPU]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fc000000-fcffffff memory:ec000000-efffffff memory:f3500000-f357ffff memory:fda00000-fda1ffff
     *-scsi
          physical id: 1
          bus info: usb@2:3
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@0:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@0:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@0:0.0.3
             logical name: /dev/sde
jeremy@jeremy-desktop:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: unable to create the OpenGL context
jeremy@jeremy-desktop:~$ lsmod
Module                  Size  Used by
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78583  0 
qnx4                   13317  0 
hfsplus                79383  0 
hfs                    49504  0 
minix                  31481  0 
ntfs                  100098  0 
vfat                   17335  0 
msdos                  17133  0 
fat                    55505  2 vfat,msdos
jfs                   174783  0 
xfs                   735018  0 
exportfs               12870  1 xfs
reiserfs              234405  0 
snd_emu10k1_synth      12964  0 
snd_emux_synth         33506  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13482  1 snd_emux_synth
snd_emu10k1           137068  2 snd_emu10k1_synth
snd_ac97_codec        105614  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc         14073  2 snd_emu10k1,snd_pcm
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13274  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
bttv                  112771  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
i2c_algo_bit           13184  1 bttv
ppdev                  12849  0 
snd_seq                51291  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
v4l2_common            16757  1 bttv
snd_timer              28659  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14110  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  2 bttv,v4l2_common
videobuf_dma_sg        18747  1 bttv
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55295  12 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
videobuf_core          25193  2 bttv,videobuf_dma_sg
ir_nec_decoder         12490  0 
btcx_risc              13400  1 bttv
emu10k1_gp             12566  0 
parport_pc             32111  1 
rc_core                25760  7 bttv,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
soundcore              12600  1 snd
gameport               15027  2 emu10k1_gp
tveeprom               17009  1 bttv
shpchp                 32345  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
floppy                 60032  0 
pata_amd               13762  2 
firewire_core          56138  1 firewire_ohci
ne2k_pci               13389  0 
8390                   18429  1 ne2k_pci
forcedeth              58190  0 
crc_itu_t              12627  1 firewire_core
jeremy@jeremy-desktop:~$ 

```
So I hope all this gibberish helps out.  It's frustrating me.  I've tried getting the new drivers for nvidia, and everything else I can think of.  

Thank you,

Jeremy

---

### Post by wildmanne39 on 2011-07-18
Hi,
> maybe im stupid or confused, cause after i install the driver and i reboot i cant access anything after it reboots i dont have the "applications places or system" options at the top or should i not reboot?
move your mouse all the way to the left of the screen and see if the launcher comes out see unity desktop is totally different then classic. If it comes out I will give you some guides on using unity.

---

### Post by wildmanne39 on 2011-07-18
> **flabden said:**
> Hey wildmanne39 it looks like I am having the same problems as skizzigh.  Except that when booting to 11.04 it goes to a black screen with a blinking cursor in the upper left hand side.  I have been looking on several forums and I think it may have to do something to do with the driver for nvidia.  I was able to access grub and and go to recovery mode and run in failsafex.  I changed my log in from ubuntu to ubuntu classic, since there may be a bug with unity.  Still a black screen.  So, I switched to xubuntu, black screen.  Switch to xfce, black screen.  I like all the interfaces, but ubuntu classic the best.  I just can't boot.  I ran the commands you gave in a post and here is what I got

```
  description: Desktop Computer
    version: 0nB1211RE101EXPL410
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=6097F424-1BD6-D811-981D-F138A186D363
  *-core
       description: Motherboard
       product: Explorer4
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.xx
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.06
          date: 08/31/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP  3200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          capacity: 2333MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM 100 MHz (10.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 128 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM 100 MHz (10.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MiB
             width: 128 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:f4000000-f7ffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:10 ioport:ec00(size=32)
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fe700000-fe700fff
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:fe900000-fe900fff
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fea00000-fea000ff
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth1
             version: a1
             serial: 00:0e:a6:c1:7c:2f
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.3 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:22 memory:fe800000-fe800fff ioport:e880(size=8)
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fb700000-fb8fffff memory:eb000000-eb3fffff
           *-multimedia:0
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:d880(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:dc00(size=8)
           *-multimedia:1
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=bttv latency=64 maxlatency=40 mingnt=16
                resources: irq:19 memory:eb200000-eb200fff
           *-multimedia:2 UNCLAIMED
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: 7.1
                bus info: pci@0000:01:07.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
                resources: memory:eb300000-eb300fff
           *-network
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 00
                serial: 00:00:e8:66:05:6e
                width: 32 bits
                clock: 33MHz
                capabilities: rom ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
                resources: irq:18 ioport:d800(size=32) memory:fb800000-fb807fff
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi1
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800BB-22JH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM92606684
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00082456
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: af4046de-ffef-4ee3-b6e5-6e7e081bf513
                   size: 4767MiB
                   capacity: 4767MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 69GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H22L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-firewire
             description: FireWire (IEEE 1394)
             product: nForce2 FireWire (IEEE 1394) Controller
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fe500000-fe5007ff memory:fe400000-fe40003f
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fb900000-fdafffff memory:eb400000-f35fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV18 [GeForce4 MX - nForce GPU]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fc000000-fcffffff memory:ec000000-efffffff memory:f3500000-f357ffff memory:fda00000-fda1ffff
     *-scsi
          physical id: 1
          bus info: usb@2:3
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@0:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@0:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@0:0.0.3
             logical name: /dev/sde
jeremy@jeremy-desktop:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: unable to create the OpenGL context
jeremy@jeremy-desktop:~$ lsmod
Module                  Size  Used by
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78583  0 
qnx4                   13317  0 
hfsplus                79383  0 
hfs                    49504  0 
minix                  31481  0 
ntfs                  100098  0 
vfat                   17335  0 
msdos                  17133  0 
fat                    55505  2 vfat,msdos
jfs                   174783  0 
xfs                   735018  0 
exportfs               12870  1 xfs
reiserfs              234405  0 
snd_emu10k1_synth      12964  0 
snd_emux_synth         33506  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13482  1 snd_emux_synth
snd_emu10k1           137068  2 snd_emu10k1_synth
snd_ac97_codec        105614  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc         14073  2 snd_emu10k1,snd_pcm
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13274  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
bttv                  112771  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
i2c_algo_bit           13184  1 bttv
ppdev                  12849  0 
snd_seq                51291  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
v4l2_common            16757  1 bttv
snd_timer              28659  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14110  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  2 bttv,v4l2_common
videobuf_dma_sg        18747  1 bttv
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55295  12 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
videobuf_core          25193  2 bttv,videobuf_dma_sg
ir_nec_decoder         12490  0 
btcx_risc              13400  1 bttv
emu10k1_gp             12566  0 
parport_pc             32111  1 
rc_core                25760  7 bttv,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
soundcore              12600  1 snd
gameport               15027  2 emu10k1_gp
tveeprom               17009  1 bttv
shpchp                 32345  0 
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
floppy                 60032  0 
pata_amd               13762  2 
firewire_core          56138  1 firewire_ohci
ne2k_pci               13389  0 
8390                   18429  1 ne2k_pci
forcedeth              58190  0 
crc_itu_t              12627  1 firewire_core
jeremy@jeremy-desktop:~$ 

```
So I hope all this gibberish helps out.  It's frustrating me.  I've tried getting the new drivers for nvidia, and everything else I can think of.  

Thank you,

Jeremy
Hi, run 
```
lspci | grep VGA

```
When do you see the black screen right after grub loads?

---

### Post by flabden on 2011-07-19
Wildmanne39,
Ok, ran that code ```
 02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
``` That's what I got.

When my computer boots, I get the manufacturer splash screen, then it goes black and there is a blinking cursor in the upper left.  I press Ctrl+Alt+F1..F7, F1 to F6 brings me the tty0,1,2 etc. screens where I could log in.  I have done that but it basically brings up jeremy@jeremy-desktop:~$
But, when I get to F7 I get blinking cursor.  

I wonder if there's an Ubuntu for dummies book?

Thanks,
Jeremy

---

### Post by wildmanne39 on 2011-07-19
> **flabden said:**
> Wildmanne39,
Ok, ran that code ```
 02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
``` That's what I got.

When my computer boots, I get the manufacturer splash screen, then it goes black and there is a blinking cursor in the upper left.  I press Ctrl+Alt+F1..F7, F1 to F6 brings me the tty0,1,2 etc. screens where I could log in.  I have done that but it basically brings up jeremy@jeremy-desktop:~$
But, when I get to F7 I get blinking cursor.  

I wonder if there's an Ubuntu for dummies book?

Thanks,
JeremyHi, have you installed your driver for your video card? You can look at this link and it should allow you to boot up then go into additional drivers and activate the driver for your card, you will need to be connected to the internet first.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by flabden on 2011-07-21
I do have the nvidia drivers installed.  I have the 173 version and the 275 version.  The 275 in additional drivers is activated but not currently in use.  Could be because I am in restore mode/low graphics.  I added the nomodeset line like that link you posted said.  If I can't figure out something soon, I'm going to scrap the whole thing and reinstall either an older version of Ubuntu or something else.  Like Fedora or Debian.  I was running 10.04 for well since it came out.  Then 3 weeks ago I upgraded to 10.10 then 11.04.  I rebooted after install of 10.10 and no prob.  But, 11.04 just won't do it.  If you have any other thoughts I would appreciate them.  Thanks for all your help.  Jeremy

---

### Post by wildmanne39 on 2011-07-21
Hi, you can not have two drivers installed at the same time, if you have an older card like mine is a 6150 then the 173 driver is probably the best driver for it.

It saying that it is acvtive but currently is not in use it just a bug if you activated it, then it is being used.

You need to open synaptic and type in nvidia and remove one of the drivers then reboot and that will most likely fix your problem.

---

