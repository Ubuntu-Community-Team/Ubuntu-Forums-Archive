---
title: "Screen freeze !!! Internet problem &gt;?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by Jag809 on 2011-07-16
Ok....First of all im a completely noob in ubuntu so be patience with me(btw my english isnt that good either)... 

My problem is the next .. I installed ubuntu 11.04 but the only way it seems to work is if i have my laptop connected "wired" to the internet, if not the SO wont even past from ubuntu screen when turn on ur pc... So i gotta have my laptop always connected to the dam wired... yesterday while watching a youtube video i disconnected the internet cable and i noticed that i could still pause and play the video while the screen was froze, i also was able to heard the video, but the screen always freeze at the moment i disconnected the cable ... and even tho i plug the Ethernet cable back to the laptop the screen will still be froze .....

So..Can any body help me .. Does this SO have to be always connected to the internet to work ? and BTW i can connected to any wireless network around but it only works if it is connected wired !!

---

### Post by LowSky on 2011-07-16
Hi welcome to the forums. I'm having a hard time understanding your exact problem but it sounds like you are saying that the computer freezes when you disconnect the Ethernet or is it the power cable?

This is not a normal issue to say the least. Can we have a few more pieces of information? What model computer is it?  How did you install Ubuntu? Was this problem happening when you first installed Ubuntu? Did it occur only after you installed some software?

If you need translation help Google offers great assistance here:
[http://translate.google.com/](http://translate.google.com/)

---

### Post by Jag809 on 2011-07-16
Yeah that: my computer screen freeze when the ethernet cable is disconnect...

What model computer is it?
acer aspire 5516
How did you install Ubuntu?
I dowloaded directly from the official web..and install it via USB
Was this problem happening when you first installed Ubuntu?
NO
Did it occur only after you installed some software?
Yes

---

### Post by wildmanne39 on 2011-07-17
Hi, do you know what software you installed just before this started happening?

---

### Post by Jag809 on 2011-07-17
do you know what software you installed just before this started happening?

This has been happening since the first day i installed ubuntu.... 

P.D: If the laptop doesnt have the ethernet cable connected it wont even start the SO through a live cd !!! or Usb in my case !!

---

### Post by amjjawad on 2011-07-17
Hello and Welcome :)

Are you saying that the LAN Cable MUST be connected so that your laptop works + your screen will not be frozen?

---

### Post by Jag809 on 2011-07-17
Are you saying that the LAN Cable MUST be connected so that your laptop works + your screen will not be frozen?

YES...the  LAN Cable MUST be connected to the laptop If not the screen will freeze

P.d: The laptop/SO will still work while the screen is frozen !!

---

### Post by amjjawad on 2011-07-17
Hello wildmanne39,

This is [the second case]("http://ubuntuforums.org/showthread.php?t=1805405") for today that user is reporting the same issue. You have seen the other thread, right?

Any idea how to sort it out?

---

### Post by amjjawad on 2011-07-17
> **Jag809 said:**
> P.d: The laptop/SO will still work while the screen is frozen !!

Sorry but what was that?

---

### Post by Jag809 on 2011-07-17
> **amjjawad said:**
> Sorry but what was that?
What i meant was, that even tho the screen is frozen i can still move the pointer, listen to music etc etc ....BTW I've install and re-install ubuntu several time and the same problem still happening

---

### Post by wildmanne39 on 2011-07-17
Hi amjjawad, yes I had seen that thread and I have seen other people having this issue lately but I have not seen one solved yet, you have?

---

### Post by mzycdth on 2011-07-17
Hi Jag809,  it sounds like you're experiencing similar issues to me with firefox+flash+ubuntu 11.04 when I first installed it.  Have you upgraded your video card drivers and flash? If not, do you know how?   Also I found that chrome was more stable with flash even after i upgraded  p.s. not sure on the wired ethernet cable issue, can't think of any reason for that. Ubuntu doesn't require any network connections to boot or stay functional.

---

### Post by wildmanne39 on 2011-07-17
> **Jag809 said:**
> What i meant was, that even tho the screen is frozen i can still move the pointer, listen to music etc etc ....BTW I've install and re-install ubuntu several time and the same problem still happening
Hi, you can have a look at this link and see if it helps. Let us know please if it fixes it and if it does mark the thread solved so it can help other people with this issue.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by amjjawad on 2011-07-17
> **wildmanne39 said:**
> Hi amjjawad, yes I had seen that thread and I have seen other people having this issue lately but I have not seen one solved yet, you have?

Hi my friend,

No, I haven't and trying to get some help from another friend who knows better than I do.

---

### Post by ercferret18 on 2011-07-17
Try posting the output of the command "dmesg" shortly after the computer freezes.

---

### Post by amjjawad on 2011-07-18
> **Jag809 said:**
> Ok....First of all im a completely noob in ubuntu so be patience with me(btw my english isnt that good either)... 

My problem is the next .. I installed ubuntu 11.04 but the only way it seems to work is if i have my laptop connected "wired" to the internet, if not the SO wont even past from ubuntu screen when turn on ur pc... So i gotta have my laptop always connected to the dam wired... yesterday while watching a youtube video i disconnected the internet cable and i noticed that i could still pause and play the video while the screen was froze, i also was able to heard the video, but the screen always freeze at the moment i disconnected the cable ... and even tho i plug the Ethernet cable back to the laptop the screen will still be froze .....

So..Can any body help me .. Does this SO have to be always connected to the internet to work ? and BTW i can connected to any wireless network around but it only works if it is connected wired !!


Hi again,

I have discussed with my friends about your case and hope we could help you and others to fix that weird issue :)

I know you are new so I'll take it easy and go step by step, deal? okay :)

First thing to check is:

1- Reboot your machine (or turn it ON).

2- Enter BIOS. Sometimes, you need to press "Del" or "F2" or "F10" to enter BIOS. I'm not sure what kind of BIOS do you have but these are the most common keys.

3- ALL BIOS must have settings to determine which device to boot from first and which device to boot form as second option, etc. It's usually called "Booting" but that depends on which BIOS do you have. Don't worry, you'll figure it out.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]



4- Check your booting options and see whether for some reason if your machine is booting from any network device.
[http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)

5- If so, then please do the following:

a- MAKE SURE your CD/DVD Drive is the First Boot Device
b- Make sure your Internal HDD is the Second Boot Device

These are the most important two options that you need to set.

[B][COLOR=Red]_NOTE THAT_[/COLOR] ... in some BIOS as attached above, there are [COLOR=Blue]*Hard Disk Boot Priority*[/COLOR]. It's totally different story. Let me know if you need me to explain that to you but I don't think you need it now.
[/B]

c- Disable any option that has to do with booting another device, like Network Devices.



**6-** *** Optional *** [I]If you suspect that someone has access your machine and changed your BIOS settings, there is always an option to Restore BIOS to the default options. No harm to do that but DO NOT do it in case you have no experience with BIOS. 

[/I]

7- Save your changes on BIOS and reboot. Actually there is an Option to Exit Saving Changes and it will reboot your machine automatically.


Now, please check and see if the same problem will occur again or not?

Waiting for your feedback and please do let me know in case you need any further explanation or help :)

---

### Post by Jag809 on 2011-07-18
> **mzycdth said:**
>  Have you upgraded your video card drivers and flash?  
  Yes

---

### Post by Jag809 on 2011-07-18
> **amjjawad said:**
> Hi again,

I have discussed with my friends about your case and hope we could help you and others to fix that weird issue :)

I know you are new so I'll take it easy and go step by step, deal? okay :)

First thing to check is:

1- Reboot your machine (or turn it ON).


Now, please check and see if the same problem will occur again or not?

Waiting for your feedback and please do let me know in case you need any further explanation or help :)

I already did all that and everything still the same ...(screen problem not yet fixed)

P.S: Dont bother so much in trying to explain simple things with that extremely specification.. (im new using ubuntu but i know a lil about computers in general) BTW i really appreciate the fact that y'all are trying to help me... Thnks

---

### Post by amjjawad on 2011-07-18
> **Jag809 said:**
> I already did all that and everything still the same ...(screen problem not yet fixed)


Okay, then time to move to part II :)

> 
P.S: Dont bother so much in trying to explain simple things with that extremely specification.. (im new using ubuntu but i know a lil about computers in general) BTW i really appreciate the fact that y'all are trying to help me... Thnks

Usually, even in real life, I do my best to be as simple as possible. I deeply sorry if that sounded like I'm underestimating you or something which is not true, I was just trying to help YOU and OTHERS as well ;)
Remember, the whole world will read this and some people have less knowledge than you so me or anyone else don't have to repeat the same all over again ;)

Hope you know what I mean and don't worry, I feel so much better when I could do something to a Linux Mate :)

---

### Post by amjjawad on 2011-07-18
Please post the output of 

```
sudo cat /var/log/syslog > jag.txt
```

Please wrap up the text with "CODE" tags or select the whole thing and click "#".

Also, please post the output of:

```
sudo lshw

```

And don't forget to wrap up the text with CODE tags.

---

### Post by chili555 on 2011-07-18
The syslog file is likely to be many hundreds of lines. I'd suggest you zip it and post it as an attackment to your reply using the paperclip tool at the top of the reply box:```
sudo cat /var/log/syslog > jag.txt
zip jag.zip jag.txt
```Attach the file jag.zip and we'll take a look.

---

### Post by Jag809 on 2011-07-18
(Here it is) the output of lshw command

```
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0406000-f0406fff
        *-usb:3
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0607400-f06074ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0400000-f0403fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ 
alex@alex-Aspire-5516:~$ clear

alex@alex-Aspire-5516:~$ sudo lshw
alex-aspire-5516          
    description: Notebook
    version: V1.10
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=38366366-3638-6664-3635-00235AD8AFA6
  *-core
       description: Motherboard
       product: Aspire 5516
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXPEE0Y00292120F1E1601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.10
          date: 04/21/2009
          size: 114KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket M2/S1G1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: S2
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:f0000000-f01fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:18 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:f0300000-f03fffff
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: 00:24:2c:66:9f:0a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.109 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:f0300000-f0303fff
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:a000(size=4096) memory:f0200000-f02fffff
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c0
                serial: 00:23:5a:d8:af:a6
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f0607000-f06073ff
           *-disk
                description: ATA Disk
                product: ST9160310AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0303
                serial: 5SV6NMN2
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00099dde
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 23a594a5-3a0a-4e8f-9726-767d502e6033
                   size: 9540MiB
                   capacity: 9540MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-15 13:49:28 filesystem=ext4 lastmountpoint=/ modified=2011-07-15 14:02:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-07-18 17:21:06 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 80d5e590-75fc-477e-8b43-0df4097deca3
                   size: 1431MiB
                   capacity: 1431MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /windows
                   version: FAT32
                   serial: 079e-3ca8
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro state=mounted
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: a92a24f6-371b-4b95-b13e-dc9fe9de1fae
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-07-15 14:14:42 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ880AS
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0404000-f0404fff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f0405000-f0405fff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0406000-f0406fff
        *-usb:3
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0607400-f06074ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0400000-f0403fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0



```

---

### Post by Jag809 on 2011-07-18
```
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): preparing device.
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): deactivating device (reason: 2).
Jul 18 17:21:07 alex-Aspire-5516 kernel: [   19.698522] atl1c 0000:05:00.0: irq 42 for MSI/MSI-X
Jul 18 17:21:07 alex-Aspire-5516 kernel: [   19.698633] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:07.0/0000:05:00.0/net/eth0
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): carrier now ON (device state 2)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> modem-manager is now available
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Trying to start the supplicant...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) starting connection 'Auto eth0'
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> dhclient started with pid 639
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 18 17:21:07 alex-Aspire-5516 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jul 18 17:21:07 alex-Aspire-5516 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jul 18 17:21:07 alex-Aspire-5516 dhclient: All rights reserved.
Jul 18 17:21:07 alex-Aspire-5516 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 18 17:21:07 alex-Aspire-5516 dhclient: 
Jul 18 17:21:07 alex-Aspire-5516 dhclient: Listening on LPF/eth0/00:23:5a:d8:af:a6
Jul 18 17:21:07 alex-Aspire-5516 dhclient: Sending on   LPF/eth0/00:23:5a:d8:af:a6
Jul 18 17:21:07 alex-Aspire-5516 dhclient: Sending on   Socket/fallback
Jul 18 17:21:07 alex-Aspire-5516 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 18 17:21:07 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 18 17:21:07 alex-Aspire-5516 init: apport pre-start process (695) terminated with status 1
Jul 18 17:21:07 alex-Aspire-5516 init: alsa-restore main process (705) terminated with status 19
Jul 18 17:21:07 alex-Aspire-5516 acpid: starting up with proc fs
Jul 18 17:21:07 alex-Aspire-5516 acpid: 32 rules loaded
Jul 18 17:21:07 alex-Aspire-5516 acpid: waiting for events: event logging is off
Jul 18 17:21:07 alex-Aspire-5516 cron[707]: (CRON) INFO (pidfile fd = 3)
Jul 18 17:21:07 alex-Aspire-5516 anacron[728]: Anacron 2.3 started on 2011-07-18
Jul 18 17:21:07 alex-Aspire-5516 init: apport post-stop process (734) terminated with status 1
Jul 18 17:21:07 alex-Aspire-5516 cron[731]: (CRON) STARTUP (fork ok)
Jul 18 17:21:07 alex-Aspire-5516 cron[731]: (CRON) INFO (Running @reboot jobs)
Jul 18 17:21:07 alex-Aspire-5516 anacron[728]: Will run job `cron.daily' in 5 min.
Jul 18 17:21:07 alex-Aspire-5516 anacron[728]: Will run job `cron.weekly' in 10 min.
Jul 18 17:21:07 alex-Aspire-5516 anacron[728]: Will run job `cron.monthly' in 15 min.
Jul 18 17:21:07 alex-Aspire-5516 anacron[728]: Jobs will be executed sequentially
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.352408] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.352418] wl 0000:02:00.0: setting latency timer to 64
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.388224] lib80211_crypt: registered algorithm 'TKIP'
Jul 18 17:21:08 alex-Aspire-5516 dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
Jul 18 17:21:08 alex-Aspire-5516 dhclient: DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
Jul 18 17:21:08 alex-Aspire-5516 dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Jul 18 17:21:08 alex-Aspire-5516 dhclient: bound to 192.168.1.102 -- renewal in 39384 seconds.
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   address 192.168.1.102
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   prefix 24 (255.255.255.0)
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   gateway 192.168.1.1
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '192.168.1.1'
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '167.206.251.130'
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '167.206.251.129'
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Scheduling stage 5
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Done scheduling stage 5
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth1, iface: eth1)
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <error> [1311024068.591811] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): now managed
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): bringing up device.
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): preparing device.
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): deactivating device (reason: 2).
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.568925] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.602415] [drm] Initialized drm 1.1.0 20060810
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.757674] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.854182] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.931378] [drm] radeon defaulting to kernel modesetting.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.931384] [drm] radeon kernel modesetting enabled.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.931493] radeon 0000:01:05.0: power state changed by ACPI to D0
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth1/rfkill0) (driver <unknown>)
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.931499] radeon 0000:01:05.0: power state changed by ACPI to D0
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.931509] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934285] [drm] initializing kernel modesetting (RS690 0x1002:0x791F).
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934323] [drm] register mmio base: 0xF0100000
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934326] [drm] register mmio size: 65536
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934538] ATOM BIOS: ATI
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934564] radeon 0000:01:05.0: VRAM: 256M 0x0000000070000000 - 0x000000007FFFFFFF (256M used)
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934570] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934592] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934594] [drm] Driver supports precise vblank timestamp query.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934607] [drm] radeon: irq initialized.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934740] [drm] Detected VRAM RAM=256M, BAR=256M
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.934746] [drm] RAM width 128bits DDR
Jul 18 17:21:08 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: New relevant interface eth0.IPv4 for mDNS.
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: Registering new address record for 192.168.1.102 on eth0.IPv4.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955911] [TTM] Zone  kernel: Available graphics memory: 438010 kiB.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955916] [TTM] Zone highmem: Available graphics memory: 900094 kiB.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955919] [TTM] Initializing pool allocator.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955944] [drm] radeon: 256M of VRAM memory ready
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955947] [drm] radeon: 512M of GTT memory ready.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.955977] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::223:5aff:fed8:afa6.
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: New relevant interface eth0.IPv6 for mDNS.
Jul 18 17:21:08 alex-Aspire-5516 avahi-daemon[556]: Registering new address record for fe80::223:5aff:fed8:afa6 on eth0.*.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.964958] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.975416] radeon 0000:01:05.0: WB enabled
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.976760] [drm] Loading RS690/RS740 Microcode
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.978038] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.980598] [drm] radeon: ring at 0x0000000080001000
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.980620] [drm] ring test succeeded in 1 usecs
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.980783] [drm] radeon: ib pool ready.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.980858] [drm] ib test succeeded in 0 usecs
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.980914] [drm] Enabling audio support
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987413] [drm] Radeon Display Connectors
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987418] [drm] Connector 0:
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987420] [drm]   VGA
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987424] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987427] [drm]   Encoders:
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987429] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987432] [drm] Connector 1:
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987434] [drm]   LVDS
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987437] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987439] [drm]   Encoders:
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   20.987442] [drm]     LCD1: INTERNAL_LVTM1
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   21.064318] hda_codec: ALC272X: BIOS auto-probing.
Jul 18 17:21:08 alex-Aspire-5516 kernel: [   21.081965] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jul 18 17:21:08 alex-Aspire-5516 init: anacron main process (728) killed by TERM signal
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519061] [drm] fb mappable at 0xD0040000
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519066] [drm] vram apper at 0xD0000000
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519069] [drm] size 4325376
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519071] [drm] fb depth is 24
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519073] [drm]    pitch is 5632
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.519343] fbcon: radeondrmfb (fb0) is primary device
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.521221] Console: switching to colour frame buffer device 170x48
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.521267] fb0: radeondrmfb frame buffer device
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.521270] drm: registered panic notifier
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.521281] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
Jul 18 17:21:09 alex-Aspire-5516 gdm-binary[908]: WARNING: Unable to find users: no seat-id found
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jul 18 17:21:09 alex-Aspire-5516 kernel: [   21.986688] ppdev: user-space parallel port driver
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) successful, device activated.
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant interface state:  starting -> ready
Jul 18 17:21:09 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Jul 18 17:21:10 alex-Aspire-5516 kernel: [   22.546502] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Jul 18 17:21:10 alex-Aspire-5516 avahi-daemon[556]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::224:2cff:fe66:9f0a.
Jul 18 17:21:10 alex-Aspire-5516 avahi-daemon[556]: New relevant interface eth1.IPv6 for mDNS.
Jul 18 17:21:10 alex-Aspire-5516 avahi-daemon[556]: Registering new address record for fe80::224:2cff:fe66:9f0a on eth1.*.
Jul 18 17:21:11 alex-Aspire-5516 acpid: client connected from 1088[0:0]
Jul 18 17:21:11 alex-Aspire-5516 acpid: 1 client rule loaded
Jul 18 17:21:12 alex-Aspire-5516 gdm-session-worker[1120]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Successfully called chroot.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Successfully dropped privileges.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Successfully limited resources.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Running.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Watchdog thread running.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Canary thread running.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Successfully made thread 1193 of process 1193 (n/a) owned by '1000' high priority at nice level -11.
Jul 18 17:21:13 alex-Aspire-5516 rtkit-daemon[1195]: Supervising 1 threads of 1 processes of 1 users.
Jul 18 17:21:14 alex-Aspire-5516 rtkit-daemon[1195]: Successfully made thread 1206 of process 1193 (n/a) owned by '1000' RT at priority 5.
Jul 18 17:21:14 alex-Aspire-5516 rtkit-daemon[1195]: Supervising 2 threads of 1 processes of 1 users.
Jul 18 17:21:14 alex-Aspire-5516 rtkit-daemon[1195]: Successfully made thread 1207 of process 1193 (n/a) owned by '1000' RT at priority 5.
Jul 18 17:21:14 alex-Aspire-5516 rtkit-daemon[1195]: Supervising 3 threads of 1 processes of 1 users.
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) starting connection 'Auto Guabas Wifi'
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1/wireless): access point 'Auto Guabas Wifi' has security, but secrets are required.
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Jul 18 17:21:16 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 18 17:21:17 alex-Aspire-5516 kernel: [   29.976024] eth0: no IPv6 routers present
Jul 18 17:21:17 alex-Aspire-5516 kernel: [   29.987730] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Jul 18 17:21:24 alex-Aspire-5516 ntpdate[1042]: step time server 91.189.94.4 offset 6.215189 sec
Jul 18 17:21:25 alex-Aspire-5516 kernel: [   31.920030] eth1: no IPv6 routers present
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1/wireless): connection 'Auto Guabas Wifi' has security, and secrets exist.  No new secrets needed.
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Config: added 'ssid' value 'Guabas Wifi'
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Config: added 'scan_ssid' value '1'
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Config: added 'psk' value '<omitted>'
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> Config: set interface ap_scan to 1
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  inactive -> scanning
Jul 18 17:21:32 alex-Aspire-5516 wpa_supplicant[644]: Trying to associate with 00:25:9c:c2:57:be (SSID='Guabas Wifi' freq=2412 MHz)
Jul 18 17:21:32 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  scanning -> associating
Jul 18 17:21:32 alex-Aspire-5516 wpa_supplicant[644]: Association request to the driver failed
Jul 18 17:21:33 alex-Aspire-5516 wpa_supplicant[644]: Associated with 00:25:9c:c2:57:be
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  associating -> associated
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Jul 18 17:21:33 alex-Aspire-5516 wpa_supplicant[644]: WPA: Key negotiation completed with 00:25:9c:c2:57:be [PTK=CCMP GTK=TKIP]
Jul 18 17:21:33 alex-Aspire-5516 wpa_supplicant[644]: CTRL-EVENT-CONNECTED - Connection to 00:25:9c:c2:57:be completed (auth) [id=0 id_str=]
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Guabas Wifi'.
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> dhclient started with pid 1453
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jul 18 17:21:33 alex-Aspire-5516 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jul 18 17:21:33 alex-Aspire-5516 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jul 18 17:21:33 alex-Aspire-5516 dhclient: All rights reserved.
Jul 18 17:21:33 alex-Aspire-5516 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 18 17:21:33 alex-Aspire-5516 dhclient: 
Jul 18 17:21:33 alex-Aspire-5516 dhclient: Listening on LPF/eth1/00:24:2c:66:9f:0a
Jul 18 17:21:33 alex-Aspire-5516 dhclient: Sending on   LPF/eth1/00:24:2c:66:9f:0a
Jul 18 17:21:33 alex-Aspire-5516 dhclient: Sending on   Socket/fallback
Jul 18 17:21:33 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jul 18 17:21:33 alex-Aspire-5516 dhclient: DHCPREQUEST of 192.168.1.109 on eth1 to 255.255.255.255 port 67
Jul 18 17:21:36 alex-Aspire-5516 dhclient: DHCPREQUEST of 192.168.1.109 on eth1 to 255.255.255.255 port 67
Jul 18 17:21:36 alex-Aspire-5516 dhclient: DHCPACK of 192.168.1.109 from 192.168.1.1
Jul 18 17:21:36 alex-Aspire-5516 dhclient: bound to 192.168.1.109 -- renewal in 35317 seconds.
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   address 192.168.1.109
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   prefix 24 (255.255.255.0)
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   gateway 192.168.1.1
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '192.168.1.1'
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '167.206.251.130'
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info>   nameserver '167.206.251.129'
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Scheduling stage 5
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Done scheduling stage 5
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 18 17:21:36 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jul 18 17:21:36 alex-Aspire-5516 avahi-daemon[556]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.109.
Jul 18 17:21:36 alex-Aspire-5516 avahi-daemon[556]: New relevant interface eth1.IPv4 for mDNS.
Jul 18 17:21:36 alex-Aspire-5516 avahi-daemon[556]: Registering new address record for 192.168.1.109 on eth1.IPv4.
Jul 18 17:21:37 alex-Aspire-5516 NetworkManager[562]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jul 18 17:21:37 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jul 18 17:21:37 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) successful, device activated.
Jul 18 17:21:37 alex-Aspire-5516 NetworkManager[562]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jul 18 17:21:45 alex-Aspire-5516 ntpdate[1522]: adjust time server 91.189.94.4 offset -0.000444 sec
Jul 18 17:21:49 alex-Aspire-5516 AptDaemon: INFO: Initializing daemon
Jul 18 17:26:49 alex-Aspire-5516 AptDaemon: INFO: Quitting due to inactivity
Jul 18 17:26:49 alex-Aspire-5516 AptDaemon: INFO: Shutdown was requested
Jul 18 17:26:50 alex-Aspire-5516 AptDaemon: INFO: Initializing daemon
Jul 18 17:31:50 alex-Aspire-5516 AptDaemon: INFO: Quitting due to inactivity
Jul 18 17:31:50 alex-Aspire-5516 AptDaemon: INFO: Shutdown was requested
Jul 18 17:58:17 alex-Aspire-5516 wpa_supplicant[644]: WPA: Group rekeying completed with 00:25:9c:c2:57:be [GTK=TKIP]
Jul 18 17:58:17 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  completed -> group handshake
Jul 18 17:58:17 alex-Aspire-5516 wpa_supplicant[644]: WPA: Group rekeying completed with 00:25:9c:c2:57:be [GTK=TKIP]
Jul 18 17:58:17 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jul 18 17:58:17 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  completed -> group handshake
Jul 18 17:58:17 alex-Aspire-5516 NetworkManager[562]: <info> (eth1): supplicant connection state:  group handshake -> completed



```

The other thing  :/

---

### Post by wildmanne39 on 2011-07-18
Hi, I am not an expert here I see that your wireless is eth1 and it should be wlan0, I am not sure that is the problem, lets see if someone else has a suggestion.

---

### Post by wildmanne39 on 2011-07-18
I am still looking over the logs I see this also.
```
nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
```

eth1): supplicant connection state:  scanning -> associating
Jul 18 17:21:32 alex-Aspire-5516 wpa_supplicant[644]: Association request to the driver failed

---

### Post by amjjawad on 2011-07-19
Hello again,

I was reading your thread from the beginning. I was trying to understand your issue even better but honestly, I'm a bit confused and I'd like to read some specific details.

First thing first, I'd like to know ... does your machine **start/turn ON **if the _LAN Cable is **NOT **connected/plugged_ in to your machine?

I'm sure you mentioned clearly that your **screen will be frozen** ONCE you **unplug** the LAN Cable. That's totally understood. Also, I understand that you CAN still use it (hear music, etc) but it's just the screen is frozen.

But if your machine can NOT _turn ON_ ***UNLESS*** the _LAN Cable_ is plugged in, then I think there's something wrong or missing in this thread that we all need to know :)

You confirmed that your machine is NOT booting from any Network device and you already have checked your BIOS.


>> Do you have the same issue IF you change the session? I mean, have you ever tried to login as Classic GNOME instead Unity? or perhaps Classic GNOME with no effect? if you haven't tried that yet, please do and report back :)


>>> NOW, what will happen if you turn OFF your Wireless Connection and KEEP your LAN Cable plugged in?
Try to turn your Wireless OFF, reboot, login to Ubuntu and then unplug your LAN Cable. If screen will freeze again, please reboot BUT DO NOT plug your LAN Cable, just keep it unplugged.

If the above procedure did NOT solve/fix the issue, repeat it 2-3 times.

If the problem is NOT yet fixed, then please issue this commands from Terminal:

```
sudo apt-get update

```

```
 sudo apt-get install --reinstall network-manager-gnome
```


Waiting for your reply :)

---

### Post by chili555 on 2011-07-19
> Hi, I am not an expert here I see that your wireless is eth1 and it should be wlan0, I am not sure that is the problem, lets see if someone else has a suggestion.This is not a problem. Many wireless drivers, including wl and  ipw2x00 for instance, use eth1.> nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failedThat's scary, isn't it? However, my syslog shows the same line as it's connecting perfectly and trouble-free! I'd be interested to have amjjawad and wildmanne39 look in their syslogs for the same. If we all have it and all connect seamlessly, I assume it's harmless.

---

### Post by amjjawad on 2011-07-19
> **chili555 said:**
> I'd be interested to have amjjawad and wildmanne39 look in their syslogs for the same. If we all have it and all connect seamlessly, I assume it's harmless.

Will do and will post back ;)


[B]Edit:
[/B]>  			 				nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed 			 		

I don't have the specific above line in my syslog.
Shall I look into something else?

Yes, I do have both **eth0** and **wlan0** up and running.

---

### Post by Jag809 on 2011-07-19
i got some updates : 

does your machine **start/turn ON **if the _LAN Cable is **NOT **connected/plugged_ in to your machine?

Technically "yes'' : But it wont pass the ubuntu logo (but im able to heard the sound that it makes when the pc starts)

I did what amjjawad told me to do ,so,  I switched the login thing to ubuntu classic (no effects), restarted my pc (LAN cable was no connected) and just like that, the computer start normally.. Everything was OK, i plug the LAN cable, opened the mozilla search something, then unplug the cable and it didn't freeze .... 

P.S: Of all the login option the ubuntu classic-no effect- was the only one the works w/o the LAN cable connected.. Another thing... The grub screen (or how ever that thing is called) only shows up somethings

And Thks (again) i was about to give up !

---

### Post by amjjawad on 2011-07-19
WOW, very interesting update, have to admit :)

> **Jag809 said:**
> i got some updates : 

does your machine **start/turn ON **if the _LAN Cable is **NOT **connected/plugged_ in to your machine?

Technically "yes'' : But it wont pass the ubuntu logo (but im able to heard the sound that it makes when the pc starts)

Does that mean, you hear the start sound of Ubuntu but screen is frozen on the Ubuntu logo with the 5 dots?


> I did what amjjawad told me to do ,so,  I switched the login thing to ubuntu classic (no effects), restarted my pc (LAN cable was no connected) and just like that, the computer start normally.. Everything was OK, i plug the LAN cable, opened the mozilla search something, then unplug the cable and it didn't freeze .... 

So, the computer or the screen did not freeze when you start your machine WITHOUT your LAN Cable **and **you logged in as Classic no effect? 

This is really interesting. Have you tried to repeat that process? I mean, try to work WITHOUT your LAN Cable connected.

1- Unplug the LAN Cable
2- Turn your machine ON
3- Login to Classic No Effect Session
4- Use your Wireless Connection instead

THEN ...

Repeat the above scenario but ...
Login to Unity

Please report back :)


> Another thing... The grub screen (or how ever that thing is called) only shows up somethings


I did not understand ... what do you mean?

> And Thks (again) i was about to give up !

My motto was, is and will always be: Never Give up, Never Surrender.
If you really want to learn, you must fail and do tons of mistakes. That's the correct way of learning and I mean Real Learning :)

Keep it up ... you are doing great job and we'll be with you to the end ;)

---

### Post by Jag809 on 2011-07-19
> **amjjawad said:**
> 
Does that mean, you hear the start sound of Ubuntu but screen is frozen on the Ubuntu logo with the 5 dots?

the computer or the screen did not freeze when you start your machine WITHOUT your LAN Cable **and **you logged in as Classic no effect? 



YES and Yes ... (The pc never freezes, only the screen)

> **amjjawad said:**
> 
1- Unplug the LAN Cable
2- Turn your machine ON
3- Login to Classic No Effect Session
4- Use your Wireless Connection instead

THEN ...

Repeat the above scenario but ...
Login to Unity



I've tried that (Didn't work)

The issue about the grub is that this screen doesn't always load when i startup mi pc !!!

Edit* When using wireless connection, Im not able to stay connected for more that 3 minutes, after 3 to 5 mints the computer will disconnect me from any wireless network..

---

### Post by wep940 on 2011-07-19
I *think* you may have already answered the question, but just in case:[B]is referring to making sure you don't have your hard-wire and  wireless working at the same time.  In other words, if the hard-wire is  plugged in, you had to disable the wireless before you plugged in the  cable, especially if your wireless connection is auto-connect.  The  reverse holds true as well - if you want to use wireless, be sure to  unplug the hard-wire cable before enabling the wireless connection.  You  can't have both trying to connect to the same access point as far as I  have ever known.
[/B]
[B]And.....sorry about the bold text.  I don't know what happened.  I pasted in amjjawad's userid and for some reason I can't turn bold off.  Don't know why.  Even tried erasing the text back to the ":" to start over by just typing it, but everything is still bold.  So.......I'm really not shouting or anything - I must just be stupid ;)
[/B]

---

### Post by wildmanne39 on 2011-07-19
@chili555 I do have the same message in my logs.
> nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed

@Jag809
I am wondering if you should try nomodeset as a boot parameter to see if you can boot into unity properly then? Here is a link for nomodesetting.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by wep940 on 2011-07-19
Didn't think about that - it's true of some nVidia cards and also many Intel graphics.  I don't know if it still holds true or not, but:

- nomodeset *used* to be for nVidia related cards

- i915.modeset=0 (or if it doesn't help then i915.modeset=1) *used* to work with a lot of other cards, and in particular Intel graphics (doesn't need to be anything with 915 in the name/chipset)

Good catch!

Dave ;)

---

### Post by wep940 on 2011-07-19
I had my suspicions so I just checked something.  Note that your graphics have the (X1200) in the output.  This is an old adapter from what I've read, and is no longer supported in the graphics driver.  I believe it needs the legacy driver, and I think the legacy driver has been discontinued.

See this link for more info:

[http://ubuntuforums.org/archive/index.php/t-1604866.html](http://ubuntuforums.org/archive/index.php/t-1604866.html)

---

### Post by wildmanne39 on 2011-07-19
@wep940 Thank you for that information it is very helpful and much appreciated, now we just have to wait and see what happens.

---

### Post by chili555 on 2011-07-19
> I had my suspicions so I just checked something. Note that your graphics have the (X1200) in the output. This is an old adapter from what I've read, and is no longer supported in the graphics driver. I believe it needs the legacy driver, and I think the legacy driver has been discontinued.I believe the driver *radeon* is proper and in place.

[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)> SUPPORTED HARDWARE

       The  radeon driver supports PCI, AGP, and PCIE video cards based on the
       following ATI chips:

       <snip>
       RS600/RS690/RS740
                   Radeon X1200/X1250/X2100
<snip>

---

### Post by wep940 on 2011-07-19
If I remember correctly, that's the open Radeon driver, not the ATI one.  Somewhere on the net I remember reading some people still have trouble with that.  I might suggest trying to set the video to vesa first just to see if that helps.  Also, I think there is an xorg-radeon-"something" that can be downloaded - I think it's the open driver though, not to mention xorg.conf has been depricated for a few releases now.  I know the new files to help configure things are in a different place now - I just don't remember where and I'm on my Windows laptop right now.
 
Like you, I'm also curious about the flash version, etc., and where it came from.  I tried 11.04 but just personally decided to go back to 10.04 for now, and I remember having a real time of it with flash and, I think, Shockwave, in 11.04.  I do remember having the whole thing lock up - I couldn't even use my mouse or keyboard.  Never did find what was causing that so I went back to 10.10.
 
dave ;)

---

### Post by amjjawad on 2011-07-20
As for the main issue, have you tried this:

(a)

```
sudo apt-get install --reinstall network-manager-gnome

```If not, please do!

(b)
Is there any good reason why you're connected to both LAN and Wireless Network at the same time?

(c)
Turn your Wireless OFF, Keep the LAN Cable plugged in, Reboot, Login to Unity (not Classic with no effect) and after few mins remove/unplug the LAN Cable. What will happen?

(d)
After what the other guys said about the driver of your Graphics Card ... honestly I don't understand what's the relation between that and your LAN Cable but I'll be very interested to see what will happen.
[B]It's good to know whether it's a Network issue that is causing the frozen screen or it's the Graphics Card issue that is causing this. Note that, everything works fine on Classic with no effect!!!

[/B]> **Jag809 said:**
> 
Edit* When using wireless connection, Im not able to stay connected for  more that 3 minutes, after 3 to 5 mints the computer will disconnect me  from any wireless network..

This happens when you unplug your LAN Cable and Login to Classic no effect session, right?

Once you have that issue, please do:

```
sudo lshw -C network

```[B]Edit:
[/B]
```

*-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan1
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR=Red]**usb**[/COLOR] ip=192.168.2.51 multicast=yes wireless=Ralink STA

```Go to: [B]/etc/pm/config.d
[/B]Create a file and name it: ***config***

Then from Terminal:

```
sudo gedit /etc/pm/config.d/config
```Add a single line code:
```
SUSPEND_MODULES=[COLOR=Red][COLOR=Black]"[/COLOR][/COLOR]**[COLOR=Red]your_driver[/COLOR]**[COLOR=Red][COLOR=Black]"[/COLOR][/COLOR]
```Save and Close gedit.

For me, I need to put: SUSPEND_MODULES=[COLOR=Red][COLOR=Black]"[/COLOR][/COLOR]**[COLOR=Red]usb[/COLOR]**[COLOR=Red][COLOR=Black]"[/COLOR][/COLOR]
You just need to replace that with your driver after you'll run: **lshw -C network**.


[I][B]>> Why we are doing this?
[/B][/I]
If the file we wrote does its job, the driver will reload when the  computer comes out of Suspend, Network Manager will wake up and the  connection will be re-established immediately with no human intervention. This may work for you or it may not. After all, there is ho harm to give it a try.


> **Jag809 said:**
> 
The issue about the grub is that this screen doesn't always load when i startup mi pc !!!


From terminal, please issue this command:

```
sudo update-grub

```Reboot and check if the GRUB menu will pop up or not?

This will come handy too:

```
sudo apt-get update

``````
sudo apt-get install  startupmanager
```[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

By the way, I was wondering why your Kernel is: 2.6.37? I thought it should be 2.6.38!!!

---

### Post by amjjawad on 2011-07-20
> **wep940 said:**
> You  can't have both trying to connect to the same access point as far as I  have ever known.

This is not really true or perhaps at least in my case :)

I'm using now Linux Mint on one of the machines here and I'm now connected to both Wired and Wireless Network.



```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: **eth0**
       version: 10
       serial: 00:1e:8c:e7:f8:e5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[COLOR="red"]192.168.2.56[/COLOR] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:c800(size=256) memory:fe6ffc00-fe6ffcff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: **wlan0**
       serial: 00:16:44:99:a8:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.38-8-generic firmware=N/A ip=[COLOR="Red"]192.168.2.53[/COLOR] link=yes multicast=yes wireless=IEEE 802.11bg

```

Works fine, no issues at all.

As long as EACH has its own IP, there is no problem at all.

---

### Post by wep940 on 2011-07-20
Well, in my experience it caused problems, and others have posted about this in the past.  Perhaps it was fixed somewhere along the line - but it really didn't work before,  If you aren't having problems, more power to you ;)
 
About the video card things being mentioned :  note that the title begins with "Screen freeze".  In reading the OP's post they mention that the screen freezes but they can still move the mouse, etc..  This is why some of us suspect the video driver isn't playing well.  Top it off with it being an older Radeon card, and you are looking for driver problems.  While the open driver is supposed to support it, I have also read some posts on the net where that card still had problems.  So, it behoves us to be sure the video is truely working okay.  It may not be the problem, or at least the entire problem, but it does need to be checked.  Do a search on the net on ubuntu x1200 driver and you'll get a lot of interesting reading.  ;)
 
Dave ;)

---

### Post by amjjawad on 2011-07-20
> **wep940 said:**
> Well, in my experience it caused problems, and others have posted about this in the past.  Perhaps it was fixed somewhere along the line - but it really didn't work before,  If you aren't having problems, more power to you ;)
 
Never had that problem so guess I'm lucky ;)

> 
About the video card things being mentioned :  note that the title begins with "Screen freeze".  In reading the OP's post they mention that the screen freezes but they can still move the mouse, etc..  This is why some of us suspect the video driver isn't playing well.  Top it off with it being an older Radeon card, and you are looking for driver problems.  While the open driver is supposed to support it, I have also read some posts on the net where that card still had problems.  So, it behoves us to be sure the video is truely working okay.  It may not be the problem, or at least the entire problem, but it does need to be checked.  Do a search on the net on ubuntu x1200 driver and you'll get a lot of interesting reading.  ;)
 
Dave ;)

Indeed, the whole point is to find out what is going on here?!
We still don't know yet whether it's a Graphics Card Issue? Network Issue? or it's totally something else?!

I prefer to wait for the OP's reply. I'll not write more post until he replies :)

---

### Post by wep940 on 2011-07-20
I agree - there's something strange going on here.  I suspect there is more going on here than it appears.  Unplugging a network cable while running used to be a problem years ago, but I thought all the modern hardware had fixed that.  Not being able to boot at all with a network cable unplugged doesn't make a lot of sense(as you said - we need to know that from the OP).
 
At any rate, I think you've taken the things I've said ok, but just so you know I'm not argueing with you or trying distract from the things you are trying to do - just pitching in some other things that can be a contributing factor.  Like I mentioned somewhere (I thought it was this thread) when I tried 11.04 I had all kinds of trouble, including my screen, the mouse, everything locking up. 
 
At any rate, just wanted to be sure you knew I wasn't trying to condemn or distract from anything you've been doing with the OP - you're trying hard to find the source of a perplexing problem!
 
Dave ;)

---

### Post by amjjawad on 2011-07-20
> **wep940 said:**
> At any rate, just wanted to be sure you knew I wasn't trying to condemn or distract from anything you've been doing with the OP - you're trying hard to find the source of a perplexing problem!
 
Dave ;)

No worries, mate :)
Totally understood and everyone here is doing his/her best to help others so I'm not the only one nor I claim I'm the best, I'm just someone who is learning in the process of helping others :)

Thank you for your understanding and let's see what will happen :)

Last time, the OP brought some interesting updates. Hope he'll do it again :D

---

### Post by wep940 on 2011-07-20
I found some interesting information checking launchpad for bug reports for radeon and 11.04.  One even mentions having to have the lan cable plugged in to boot.  So here are some things I would try:

change the boot line to include:

radeon.modeset=0

Of course, since you can currently boot as long as the lan cable is plugged in, you will actually need to edit one of the grub config files to include that in order to test with the lan cable unplugged.

It seems that the Kernel Mode Setting (KMS) sometimes needs to be turned off, other times needs to be turned on.

It seems there are some power setting/actions that cause the problem, and that by turning off modeset and KMS it seems to allow one to boot.  This could also explain why unplugging the network cable seems to make the screen freeze.


EDIT:  For some, setting radeon.modeset=1 helps for KMS with radeon cards.

If we can get this to work, you may not be able to run unity yet, but hopefully we can get you to where you can boot without the lan cable plugged in.

It's also important to be sure it's using the open driver, but let's get past the booting problem first, then we'll move to the driver.

I'm going to be gone for a while, so hopefully [amjjawad]("http://ubuntuforums.org/member.php?u=941822") can walk you through doing this in simpler terms than what I have stated (hey, it's late ;) ).

To summarize:  11.04 and Kernel Mode Setting with the radeon cards and driver has been known to cause the exact problem you have stated in terms of not being able to boot unless the lan cable is plugged in.  Boot up with your lan cable plugged in, then edit the appropriate grub configuration file to include radeon.modeset=0.  Then try shutting down, unplugging the lan cable and then rebooting to see if it works.  If not, use the lan cable so you can boot again and change it to radeon.modeset=1, then shutdown, unplug the lan cable and try booting again.  There is some sort of problem with KMs (Kernel Mode Setting) with the radeon cards/driver and it also causes a power management problem.

[amjjawad]("http://ubuntuforums.org/member.php?u=941822"):  I'm getting pretty tired, and I also have to be gone for a while so I may not be back on until this evening or even tomorrow.  I know I wrote something a little confusing - hopefully that last paragraph where I summarized will give you what you need to walk the OP through trying this.

---

### Post by amjjawad on 2011-07-20
> **wep940 said:**
> If we can get this to work, you may not be able to run unity yet, but hopefully we can get you to where you can boot without the lan cable plugged in.


Please read this: [http://ubuntuforums.org/showpost.php?p=11064781&postcount=29](http://ubuntuforums.org/showpost.php?p=11064781&postcount=29)

and 

_[http://ubuntuforums.org/showpost.php?p=11064993&postcount=31](http://ubuntuforums.org/showpost.php?p=11064993&postcount=31)_[]("http://ubuntuforums.org/showpost.php?p=11064781&postcount=31")

---

### Post by wep940 on 2011-07-20
Back temporarily, but going to be gone the rest of the day.

Yep - saw those posts myself, but I thinkingt, and I could be wrong here because it's normally not a good thing for me to think ;) ,  that was one of the things that the OP already tried.  I only mention the driver because according to net posts and laucnhpad bug reports it causes the same symptoms with 11.04.

This post from the OP in this thread made me think we were past the boot problem:

 				 				**> Re: Screen freeze !!! Internet problem >?** 			
 			 			 		   		 		 		i got some updates : 

does your machine **start/turn ON **if the _LAN Cable is **NOT **connected/plugged_ in to your machine?

Technically "yes'' : But it wont pass the ubuntu logo (but im able to heard the sound that it makes when the pc starts)

I did what amjjawad told me to do ,so,  I switched the login thing to  ubuntu classic (no effects), restarted my pc (LAN cable was no  connected) and just like that, the computer start normally.. Everything  was OK, i plug the LAN cable, opened the mozilla search something, then  unplug the cable and it didn't freeze .... 

P.S: Of all the login option the ubuntu classic-no effect- was the only  one the works w/o the LAN cable connected.. Another thing... The grub  screen (or how ever that thing is called) only shows up somethings

And Thks (again) i was about to give up 

Since this means Gnome and not Unity, I was assuming therefore the driver problem.  They mention problems with the radeon driver and unity in 11.04 in the net threads and the launchpad bug reports I've read.  All the OP has to do, since they can boot okay now, is to just edit the grub boot line at boot time and try the radeon.modeset=0 and select unity at logon.  If it doesn't work, try the radeon.modeset=1 and select unity at boot.  If that doesn't work, just hook up the lan cable, reboot, make the change again to classic, take out the lan cable and reboot.

 
So at any rate, if you can get the OP to try your stuff first it would be good.  If it does fail, try the stuff I posted.  If the OP has video problems after being able to at least get past the boot, try the stuff I suggested.

I appreciate you working with the OP, and if needed, walking them through the stuff I have mentioned.

Thanks again!  Have a good one, and I'll talk with you later! ;) ;)

BTW - I tried accepting you as a friend but it's been so long since I did that I have no clue.  I tried the accept as friend and save, but I'm not sure it did anything.  So, I put your userid in the top box, clicked the friend box and then clicked save the changes.  If it didn't work please let me know and I'll go back in to fix it.

---

### Post by amjjawad on 2011-07-20
wep940,

I do appreciate your support and help and I have NO problem if you or anyone else wants to help the OP to fix his problem but my point was: Please read each post carefully as the OP can boot his machine without the LAN Cable Plugged in but his screen will be forzen in case he'll unplug the cable and his machine will still work, it's just the screen that is frozen.

If your steps will fix the issue, that's definitely great and we all here will learn from this. That's indeed what we all want. 
I'm not looking for any credit here for myself, I just want to help the OP and everyone is more than welcome but all what I'm saying is:

[B]Please, read the whole thing carefully :)
[/B]

Have a great day!

P.S.
I think you managed to add me as a friend!

---

### Post by wildmanne39 on 2011-07-20
Hi, I have been researching your problem and many people say they were able to fix this problem by upgrading there kernel to the latest.

You can open synaptic and type kernel in the search box then find your kernel and right click on it and see if there is an upgrade for it, if there is install it and reboot.
Thank you

---

### Post by amjjawad on 2011-07-20
> **wildmanne39 said:**
> Hi, I have been researching your problem and many people say they were able to fix this problem by upgrading there kernel to the latest.


It's a good point :)

I have noticed this on [http://ubuntuforums.org/showpost.php?p=11064993&postcount=31](http://ubuntuforums.org/showpost.php?p=11064993&postcount=31)

It's not the latest.

wildmanne39, may I ask how to upgrade the Kernel via CLI?

---

### Post by wildmanne39 on 2011-07-20
Hi amjjawad, first check to see the kernel you have now

```
uname -r
```

Next find available kernel images

```
apt-cache search linux-image 
```

Now install kernel by specifying version number

```
sudo apt-get install linux-image-x.x.x-xx
```

---

### Post by amjjawad on 2011-07-20
> **wildmanne39 said:**
> Hi amjjawad, first check to see the kernel you have now

```
uname -r
```Next find available kernel images

```
apt-cache search linux-image 
```Now install kernel by specifying version number

```
sudo apt-get install linux-image-x.x.x-xx
```

Thanks a million my friend :)

Now, OP knows both ways (Synaptic and CLI) :)

---

### Post by wildmanne39 on 2011-07-20
Hi, your welcome! I wonder if he got it fixed? since he has not been on here lately.

---

### Post by wep940 on 2011-07-20
Good luck - outa here.

---

### Post by Jag809 on 2011-07-20
I realized my laptop is kidda old so i wont break my head tryin to fix it ...... i been a lil bit busy in the past days, thats why i havent reply, but imma try to do everything y'all have said (suggest to do to solve the freezing problem)....(as soon as possible)

Another question not related to the main problem (i just dont want to create another tread for this simple question).....So.....Is this how partitions have to be divided ??

---

### Post by jtarin on 2011-07-20
That's a good start, but are your sure that is all you want to allow for Ubuntu?

---

### Post by wildmanne39 on 2011-07-20
Hi, it depends, this is ok if the ntfs partition is for data to share between windows and ubuuntu.

Swap is a little small usually 2 gigs is about right, because it is also used to suspend your system.

---

### Post by wep940 on 2011-07-21
And try to remember and understand - the fix so far only gets you to classic (gnome).  The information I have provided is to try to allow you to boot with no problems in 11.04 native - the default unity desktop.  That's all I'm trying to get people to understand - the problem is "fixed" in that it bypasses unity.  I would imagine when certain updates are done it will eventually default back to unity and the problem will reoccur.  What I've been suggesting IS to help you boot in 11.04 with the default desktop manager Unity without the problems you have had.  Simple as that.  I've read the posts in the thread many times - my point -> make it boot to Unity and you have a true fix that should hold true in future updates.  Right now it is more of a work-around than a fix.

---

### Post by amjjawad on 2011-07-21
> **Jag809 said:**
> I realized my laptop is kidda old so i wont break my head tryin to fix it ...... 


You are not breaking your head, you're learning new experience that you'll never forget, trust me :)

Don't give up, it's too early for that.


> i been a lil bit busy in the past days, thats why i havent reply, but imma try to do everything y'all have said (suggest to do to solve the freezing problem)....(as soon as possible)



We are going to wait for you so take your time ;)
I decided to take a day off from the forum (I've been online for many hours lately) but I just can't help it.

Remember, we're waiting for ya!

---

### Post by amjjawad on 2011-07-21
As for your question regarding partitioning, I second my friend's question:

> **jtarin said:**
> That's a good start, **but are your sure that is all you want to allow for Ubuntu?**

---

### Post by Jag809 on 2011-07-21
> **wildmanne39 said:**
> Hi, it depends, this is ok if the ntfs partition is for data to share between windows and ubuuntu.

Ssystem.

  What exactly do you mean ?>

---

### Post by jtarin on 2011-07-21
> **Jag809 said:**
> What exactly do you mean ?>

I think he is saying it's OK as long as their is no operating system on there.Only a shared data partition.
He will correct my statement if I misspoke.:P

---

### Post by wildmanne39 on 2011-07-21
Hi, that is what I meant thank you jtarin.

---

### Post by jtarin on 2011-07-21
:p

---

### Post by b1gag3 on 2011-07-23
Hi there, I'm the new one :)

I'm encounting the same problem. Got a acer aspire netbook (with ati radeon) with ubuntu 11.04 (unity) and the kernel is up to date (2.6.38-10-generic) Booting without plugged ethernet cable occurs systems freezing after login. If I boot with the cable and unplug it after I'm logged in, system freezes again. Booting the system without plugged cable, and disabling the wireless controller via keyboard "shortcut" causes no freezing after logging in as soon I don't try to activate the wireless controller. In this case, system freezes. 
If I boot without the cable ubuntu plays a error sound while the login mask is build up but no error message will be displayed. My linux knowlegde is not the best so please be patient :)

I read the thread, but I don't get the "workaround". Obviously the problem is not solved and any "solutions" like disabling the wireless controller doesn't work for me. :/

---

### Post by amjjawad on 2011-07-23
> **b1gag3 said:**
> Hi there, I'm the new one :)

I'm encounting the same problem. Got a acer aspire netbook (with ati radeon) with ubuntu 11.04 (unity) and the kernel is up to date (2.6.38-10-generic) Booting without plugged ethernet cable occurs systems freezing after login. If I boot with the cable and unplug it after I'm logged in, system freezes again. Booting the system without plugged cable, and disabling the wireless controller via keyboard "shortcut" causes no freezing after logging in as soon I don't try to activate the wireless controller. In this case, system freezes. 
If I boot without the cable ubuntu plays a error sound while the login mask is build up but no error message will be displayed. My linux knowlegde is not the best so please be patient :)

I read the thread, but I don't get the "workaround". Obviously the problem is not solved and any "solutions" like disabling the wireless controller doesn't work for me. :/


Hello and Welcome :)

I'd suggest to start your own thread (in order not to confuse anyone) **OR** follow this thread and read each suggestion/advice here.

The steps that the OP (Original Poster for this thread) has tried or will try might work for you or it might not :)

Thank you!

---

### Post by wildmanne39 on 2011-07-23
> **b1gag3 said:**
> Hi there, I'm the new one :)

I'm encounting the same problem. Got a acer aspire netbook (with ati radeon) with ubuntu 11.04 (unity) and the kernel is up to date (2.6.38-10-generic) Booting without plugged ethernet cable occurs systems freezing after login. If I boot with the cable and unplug it after I'm logged in, system freezes again. Booting the system without plugged cable, and disabling the wireless controller via keyboard "shortcut" causes no freezing after logging in as soon I don't try to activate the wireless controller. In this case, system freezes. 
If I boot without the cable ubuntu plays a error sound while the login mask is build up but no error message will be displayed. My linux knowlegde is not the best so please be patient :)

I read the thread, but I don't get the "workaround". Obviously the problem is not solved and any "solutions" like disabling the wireless controller doesn't work for me. :/Hi, try what I suggested in my previous post and upgrade the kernel and see if that works, please post back and let us know.

---

### Post by b1gag3 on 2011-07-23
Hi there, as I mentioned my kernel is up to date. I tried your steps right before :/

---

### Post by wildmanne39 on 2011-07-23
Hi, there are two more kernel updates since the one you are using. The kernel that says 2.6.39 or above is what you need.

You may have to activate backports and prerelease updates in synaptic to get the latest kernel update but do not install any other updates that way and as soon as you install the kernel update uncheck backport and prerelease updates. You will have to reload your list after you enable the prerelease and backport updates.

---

### Post by b1gag3 on 2011-07-23
synaptic doesn't showed me a kernel update. I tried it via console with you mentioned steps. but something i dont remember was in used and cann't be update. so I accessed the console before loading xserver and so on. I updated the kernel to 2.6.38-11. The process shows a error because of missing linux-headers for this revision. After reboot my screen starts flashing on booting process and the booting process seemed to be crashed. Trying to restore failed packages with the restore tool restored the kernel to 2.6.38-10. But display is allready flashing. But now every third flash you see the boot process log. Something like Error Log caused a &quot;failed&quot; instead of an &quot;Ok&quot;. Cant remember the correct label.   Summary: Booting ubuntu is currently not possible. So I'll reinstall ubuntu tomorow ...

---

### Post by wildmanne39 on 2011-07-23
Hi, I am sorry you had a failed kernel upgrade, let us know when you are back up and running.

---

### Post by b1gag3 on 2011-07-24
Here i'm back again :) Instead of reinstall ubuntu I tried to remove the several maybe broken kernels. So I removed first 2.6.38-11 and after that 2.6.38-10. My kernel shows now 2.6.38-8 and booting/login without cable works! even booting with cable and unplug it while logged in works. Hope this works not because of some misconfiguration caused of the failed kernel updates and the recovery after that :D

But there's still the error sound is played after the gui / login-form was build up.

---

### Post by wildmanne39 on 2011-07-24
> **b1gag3 said:**
> Here i'm back again :) Instead of reinstall ubuntu I tried to remove the several maybe broken kernels. So I removed first 2.6.38-11 and after that 2.6.38-10. My kernel shows now 2.6.38-8 and booting/login without cable works! even booting with cable and unplug it while logged in works. Hope this works not because of some misconfiguration caused of the failed kernel updates and the recovery after that :D

But there's still the error sound is played after the gui / login-form was build up.Hi, that is strange you must have some of the newer kernel in the mix for it to have fixed the problem.

---

### Post by b1gag3 on 2011-07-25
If you need some information, just say it.

But after several reboots, sometimes ubuntu crashed while booting. Don't know why. 

Unless of the failed boot processes, the ubuntu logo with the little loading dots doesn't show up anymore. Just right before the xserver is loaded the logo flashes up. Its not important to see the loading bar, but I thing thats not as it should be. But maybe this is content for another topic.

---

### Post by b1gag3 on 2011-07-25
ok rewind ... nothin works ... after booting today ubuntu freezes after login...
I retried the steps of yesterday... Installed 2.6.28-10 (headers and images). This time there was no hectic flashing while booting, but after login ... freeeeeeze.
So I tried to remove 2.6.38-10 again, and downgraded to 2.6.38-8 (images and headers). Works fine but after login, you get it, freeze.
Plug the ethernetcable works for 3-60 seconds then freeze ... its annoying >.<

---

### Post by amjjawad on 2011-07-25
> **b1gag3 said:**
> ok rewind ... nothin works ... after booting today ubuntu freezes after login...
I retried the steps of yesterday... Installed 2.6.28-10 (headers and images). This time there was no hectic flashing while booting, but after login ... freeeeeeze.
So I tried to remove 2.6.38-10 again, and downgraded to 2.6.38-8 (images and headers). Works fine but after login, you get it, freeze.
Plug the ethernetcable works for 3-60 seconds then freeze ... its annoying >.<

Please start your OWN thread ... I'm so much confused now and I lost track with what is going on with the Original Poster!

Thank you!

---

### Post by b1gag3 on 2011-07-25
The topic is that ubuntu is freezing if no ethernet cable is plugged in. i got the same problem, so i thought this would be the right place to discuss...

---

### Post by amjjawad on 2011-07-25
> **b1gag3 said:**
> The topic is that ubuntu is freezing if no ethernet cable is plugged in. i got the same problem, so i thought this would be the right place to discuss...

In fact, this called Hijack someone's else thread.

It would be harder for everyone here to keep track with what is going on. For me, I can't.

I'm sorry but it's a common thing to start a new thread even if you have the same problem.

Usually, I do the same, post in someone's else thread BUT only if I have one question or I know for sure that I'll need to write 1-2 posts. 
I see the process with you is taking few pages now so I'd suggest to start a new one.

Otherwise, I'm really sorry, I can't follow up with two users at the same time!

---

### Post by Jag809 on 2011-08-11
[SIZE=2]looks like i got a lot to read ...imma try to do everything yall have suggested to night.....Plus i got  a new problem regarding the dual boot ....

C yaa[/SIZE]...[FONT=Comic Sans MS]*_[SIZE=1]keep in mind English isnt my first language ![/SIZE]_*[/FONT]

---

### Post by amjjawad on 2011-08-11
> **Jag809 said:**
> [SIZE=2]looks like i got a lot to read ...imma try to do everything yall have suggested to night.....Plus i got  a new problem regarding the dual boot ....

C yaa[/SIZE]...[FONT=Comic Sans MS]*_[SIZE=1]keep in mind English isnt my first language ![/SIZE]_*[/FONT]

Where have you been? :)

Keep reading and I'll be waiting :)

So what? who told you that English is my first language? :)
Don't worry about that :)

---

### Post by Jag809 on 2011-08-13
> **amjjawad said:**
> As for the main issue, have you tried this:
(a)
```
sudo apt-get install --reinstall network-manager-gnome

```If not, please do!
Turn your Wireless OFF, Keep the LAN Cable plugged in, Reboot, Login to Unity (not Classic with no effect) and after few mins remove/unplug the LAN Cable. What will happen?


I tried that and it didn't work !!


> **amjjawad said:**
> By the way, I was wondering why your Kernel is: 2.6.37? I thought it should be 2.6.38!!!

i checked again and it is 2.6.38 

About the wireless issue: i was following ur instructions but i couldn't create a file (cuz i wasn't the owner?)..and i found this (check the pict below)

About the Grub issue: i follow your tutorial on how to DUALboot...but in the the moment that i have to decide in which partition i want to install windows it gives me a error ...maybe im doing something wrong when installing ubuntu.... I've installed ubuntu like 5 times and everytime a try to dualboot am gettin the same error (the errors says something like(you cants install windows in this partition cuz is not NTFS)but it is ntfs...

---

### Post by Jag809 on 2011-08-13
> **wep940 said:**
> 

To summarize:  11.04 and Kernel Mode Setting with the radeon cards and driver has been known to cause the exact problem you have stated in terms of not being able to boot unless the lan cable is plugged in.  Boot up with your lan cable plugged in, then edit the appropriate grub configuration file to include radeon.modeset=0.  Then try shutting down, unplugging the lan cable and then rebooting to see if it works.  If not, use the lan cable so you can boot again and change it to radeon.modeset=1, then shutdown, unplug the lan cable and try booting again.  There is some sort of problem with KMs (Kernel Mode Setting) with the radeon cards/driver and it also causes a power management problem.

[]("http://ubuntuforums.org/member.php?u=941822").

Ok..i got that but how imma suppose to do this ( edit the appropriate grub configuration file to include radeon.modeset=0.)...

---

### Post by Jag809 on 2011-08-13
> **wildmanne39 said:**
> Hi amjjawad, first check to see the kernel you have now

```
uname -r
```Next find available kernel images

```
apt-cache search linux-image 
```Now install kernel by specifying version number

```
sudo apt-get install linux-image-x.x.x-xx
```

Not....this doesn't work...but i would like to know how to identify the kernel version that i should update (using the synaptic) cuz when i write kernel..im getting a long @$$ list of stuff

P.s:my Kernel is: 2.6.38 (in case this is important)...Also (now imma check out this threat to see if it can help me [http://ubuntuforums.org/showthread.php?t=1811877](http://ubuntuforums.org/showthread.php?t=1811877))

---

### Post by Jag809 on 2011-08-19
Hola !

---

### Post by Jag809 on 2011-08-20
Erase this Comment !

---

### Post by Jag809 on 2011-08-23
Heeeeeeeeeeeeeeeeeeeeeeeeelp

---

### Post by Jag809 on 2011-08-24
Aaaaaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

---

### Post by wildmanne39 on 2011-08-25
Hi, here is a link that has solved many peoples problems that have the same issue.
[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)

---

### Post by amjjawad on 2011-08-27
> **Jag809 said:**
> Aaaaaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

This thread has started in July 16th, 2011 which means it's 1.5 month old now. I do need to go back and read all these 9 pages to remember what is going on.

Please check the previous post but wildmanne39 and report back.
You're taking so long to reply, amigo ;)

---

