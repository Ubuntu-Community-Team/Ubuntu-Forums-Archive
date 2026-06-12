---
title: "only certain windows WILL NOT resize (cant make smaller)"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by CleveRuse on 2011-06-03
Can someone please help. I'm having problems resizing certain Windows that are taller than the screen - specifically Gnome Color Chooser and Evolution mail (and the main page for Compiz Config. acts funny - keeps auto resizing when I scroll). I'm running Ubuntu 11.04 with Gnome desktop (classic). I have searched my problem and found similar problems - like not being able to resize Windows taller than the screen - but these issues are said to have been fixed in the new release and my problem is specific to these apps (and (prolly more, I just can't quite remember)

So does anyone have a fix for this, or even know the cause. This problem persists whether using Compiz or Metacity as a window manager ...also I believe it happens using Unity, tho I couldn't care less since I'll never use that garbage. 

If it helps, I'm on a mini notebook PC (Verizon's Gateway mini LT20) - something like that anyway

I appreciate any and all advise ....so thnx in advance

*On a side note, I'd like to know why, when I'm in, say ...Compiz, and I choose a category, then resize the window to fit the screen, then choose the Back button to return to previous screen, does the window revert to the size it was before I chose the option? 

I mean, if I'm in Comipiz, and I choose the category 'Resize Window', then resize that window, then choose the back button and return to the main page, why does the window auto-resize to its original specs? Why not retain the size I just imposed? It's not like I opened a NEW window, it's the SAME F'n window ...Sooo annoying!

I guess wut i'm saying is this cant be the intended behavior, since its absolutely RETARDED, so ...how can i FIX this? how can i fix both these irritating problems?

---

### Post by robsoles on 2011-06-06
> **CleveRuse said:**
> ...

I appreciate any and all advise



Would you mind stating your display height in pixels? I have a netbook only does 600 pixels high and I have had to turn on auto-hide for both top and bottom panels in Gnome to get more windows to fit on the display.

It's commonly down to a touch of laziness that a window has no provision for scrolling and is coded to make itself the minimum height required to fit it's contents - resize it all you like, it will snap back as soon as it's own size check code executes; I've seen this in Windows Apps but they more often just make it completely un-resizable.

Regarding 'any and all advice' :)

Provide more info, you might consider info 'bait for techies' and the more relevant 'bait' the better.

Although I share your reasoning, I am not sure it helps gain responses, where you trash Unity. Basically an idea of the less people you offend the more people might feel free to respond - sorry, prolly a bit preachy really :roll:

---

### Post by CleveRuse on 2011-06-13
Hey thnx for the reply. My original reply was lost so ill be brief. My screen resolution is 1054x600 i believe. As for all other useful, relevant data, ill try to be cogent, but its difficult for me to know wuts relevant since i dont know wuts wrong (or have experience with Linux -or computers period,except web surfing, prior to a month ago)

I use Compiz for ...i guess everything, effects for windows and their borders; I use 'Compiz-fusion icon' to reload windows when something messes up my window borders... Umm, and 'Ubuntu tweak' for a couple things, like to set up wut should happen when my cursor crosses over a corner of a page, or to DL packages, or just for editional effects. But i notice this problem when all of those things r disabled as well. Ive even tried the "Ubuntu-No Effect" option at Log-in. Also tried running "Unity" instead. or with "fusion-icon" disabled, or with 'Metacity" rather than 'Compiz" ...Wut else? Oh, logging in as differnt User. -NOTHING

So, yeah, i feel like im out of options but its really annoying. The most annoying is when Im in 'CCSM' itself, instead of fitting on the page or even just NOT fitting on the page, but NOT fitting on the page consistently, like the other bratty misbehaving windows, it constantly adjusts itself as i scroll; so that as i scroll down, the top half disappears,then as i scroll bak up,it goes down, which, strictly in terms of function, is convenient, since it allows access that would otherwize be denied, but then sometimes it does this thing where it will adjust itself in the same manner (up/down), only then it will be whenever i attempt to make a selection on the page, shifting a fraction of a second b4 my selection is registered, so that i cant make a selection at all. then im left the only two options; either i can minimize it by clicking on its corresponding launcher in 'Docky', or I can Reboot so that i can close it. ...oh, or i guess i could launch a terminal from the keyboard and "KILL" it that way. As u can see, all those options suck.

well, im prolly missing something obvious, but for now atleast, Im at a loss.

I was hoping there might be something to be done in 'CCSM's 'Window management", but i cant make sense of things like 'window rules' and 'resize windows', or wutever theyre called.

Oh yeah, I even tried restoring Compiz to default settings, from both an option within 'Ubuntu Tweak', and from the terminal using the "--recursive unset" command.

*wasn't so quick a reply after all;)

---

### Post by wildmanne39 on 2011-06-13
> **CleveRuse said:**
> hey thnx for the reply. my original reply was lost so ill be brief. my screen resolution is 1054x600 i believe. as for any n all other useful, relevant data, ill try to post unprompted but its difficult for me to know wuts relevant since i dont know wuts wrong (or have experience with Linux -or computers period,except web surfing, prior to a month ago)

i use Compiz for, i guess everything, effects for windows n their borders,i use Compiz-fusion icon to reload windows when something messes up my window borders... ph, and 'Ubuntu tweak' for a couple things to set up things like wut should happen when my mouse cursor crosses over corner of a page or DL packages or just for editional effects, but i notice this problem when all of those things r disabled. i even tried "Ubuntu (No Effect)" mode option at Log-in. Also tried "Unity", or with "fusion-icon" disabled, or with 'Metacity" rather than 'Compiz" ...Wut else? Oh, logging in as differnt User. -NOTHING

So, yeah, i feel like im out of options but its really annoying. The most annoying is when Im in 'CCSM' itself, instead of fitting on the page or even just NOT fitting on the page, but NOT fitting on the page consistently, like the other bratty misbehaving windows, it constantly adjusts itself as i scroll; so that as i scroll down, the top half disappears,then as i scroll bak up,it goes down, which, strictly in terms of function, is convenient, since it allows access that would otherwize be denied, but then sometimes it does this thing where it will adjust itself in the same manner (up/down), only then it will be whenever i attempt to make a selection on the page, shifting a fraction of a second b4 my selection is registered, so that i cant make a selection at all. then im left the only two options; either i can minimize it by clicking on its corresponding launcher in 'Docky', or I can Reboot so that i can close it. ...oh, or i guess i could launch a terminal from the keyboard and "KILL" it that way. As u can see, all those options suck.

well, im prolly missing something obvious, but for now atleast, Im at a loss.

I was hoping there might be something to be done in 'CCSM's 'Window management", but i cant make sense of things like 'window rules' and 'resize windows', or wutever theyre called.

Oh yeah, I even tried restoring Compiz to default settings, from both an option within 'Ubuntu Tweak', and from the terminal using the "--recursive unset" command.

*wasn't so quick a reply after all;)
Hi, have you looked in additional settings to see if there is a driver for your video card? I am not sure that will help but it might. It gets hard to pin point a problem when you have changed so many settings especially use compiz and metacity, in compiz look in the resize window plugin and see what your settings are, also you might look in move window. I also would create another user and log on with that name and see if it helps.

---

### Post by CleveRuse on 2011-06-14
ahhh, NOPE... But thats wut ive u all for;) And thnx ...of coarse it helps, tho it may not be THE answer, its something i havent and wouldnt have thought of, so,,, At the very least i can eliminate it - the driver suggestion i mean. As for the the "new user" trick, i already tried it (as temporary user tho), and as for the settings in the above mentioned, i cant really make sense of them -tho most are not even set- thats why i just reset them all to default -numerous times, actually reset my whole system using an option in 'Ubuntu Tweak'- then only set the ones i could make sense of. But maybe someone here can so i'll take note of the settings for the ones mentioned and post them here after i look into the 'Driver' bit. Im posting now cuz i have no ideaa how long it'll take to see about the driver since i hardly know wut drivers are or wut they do (except maybe act like a liason between hardware? making devices  "Readable"?

Ill be back.

---

### Post by wildmanne39 on 2011-06-14
> **CleveRuse said:**
> ahhh, NOPE... But thats wut ive u all for;) And thnx ...of coarse it helps, tho it may not be THE answer, its something i havent and wouldnt have thought of, so,,, At the very least i can eliminate it - the driver suggestion i mean. As for the the "new user" trick, i already tried it (as temporary user tho), and as for the settings in the above mentioned, i cant really make sense of them -tho most are not even set- thats why i just reset them all to default -numerous times, actually reset my whole system using an option in 'Ubuntu Tweak'- then only set the ones i could make sense of. But maybe someone here can so i'll take note of the settings for the ones mentioned and post them here after i look into the 'Driver' bit. Im posting now cuz i have no ideaa how long it'll take to see about the driver since i hardly know wut drivers are or wut they do (except maybe act like a liason between hardware? making devices  "Readable"?

Ill be back.
Hi, if you have a driver for your card it will be in additional drivers, put this in a terminal and I will take a look and see what hardware you have so we can help you better.
```
sudo lshw
```  post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by CleveRuse on 2011-06-14
whoops, shoulda read a little closer...the next one should be wut ur lookin for
thnx so much 4 lookin at this stuff 4 me]

---

### Post by CleveRuse on 2011-06-14
sorry here:

```
ab@CleveRuse-LT20:~$ sudo lshw
[sudo] password for ab: 
cleveruse-lt20            
    description: Notebook
    version: V1.08
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=BasicNB_QS uuid=3A57E249-FBE8-2B45-2E72-00235A71D846
  *-core
       description: Motherboard
       product: LT20
       vendor: Acer
       physical id: 0
       version: V1.08
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.08
          date: 08/12/2009
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: EBE10UE8AFSA-8G-F
             vendor: 0x7F7FFE0000000000
             physical id: 0
             serial: 0xE8DC3E8E
             slot: J2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm nx cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1c
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1d
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:58280000-582fffff ioport:60f0(size=8) memory:40000000-4fffffff memory:58300000-5833ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:58200000-5827ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:58340000-58343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:57100000-581fffff ioport:50000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: f0:7b:cb:87:28:6e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:57100000-5710ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:56100000-570fffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=8192) memory:55000000-560fffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: c0
                serial: 00:23:5a:71:d8:46
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:1000(size=4096) memory:54000000-54ffffff ioport:53000000(size=16777216)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:6080(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6060(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6040(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:58344400-583447ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:60d8(size=8) ioport:60fc(size=4) ioport:60d0(size=8) ioport:60f8(size=4) ioport:6020(size=16) memory:58344000-583443ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54501
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PBBO
                serial: 100315PBPB04ECGA2Y4M
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002f103
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3d6fb382-e202-4abb-b38f-2619503b51da
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-19 23:44:49 filesystem=ext4 lastmountpoint=/ modified=2011-06-04 11:27:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-06-14 11:48:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1013MiB
                   capacity: 1013MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1013MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:6000(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 9412
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

```oh, and the reason i was gone so long is cuz my Android phone "Bricked" this morning after flashing a Radio Update, So ive been stressing all day trying to get Ubuntu to recognize my SDcard in a Micro-SDcard-Reader so i can remove the Radio-Image from the root of my SDcard... So maybe there'll be some useful information 4 this as well in the above:)

---

### Post by wildmanne39 on 2011-06-14
> **CleveRuse said:**
> sorry here:

```
ab@CleveRuse-LT20:~$ sudo lshw
[sudo] password for ab: 
cleveruse-lt20            
    description: Notebook
    version: V1.08
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=BasicNB_QS uuid=3A57E249-FBE8-2B45-2E72-00235A71D846
  *-core
       description: Motherboard
       product: LT20
       vendor: Acer
       physical id: 0
       version: V1.08
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.08
          date: 08/12/2009
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: EBE10UE8AFSA-8G-F
             vendor: 0x7F7FFE0000000000
             physical id: 0
             serial: 0xE8DC3E8E
             slot: J2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm nx cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1c
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1d
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:58280000-582fffff ioport:60f0(size=8) memory:40000000-4fffffff memory:58300000-5833ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:58200000-5827ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:58340000-58343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:57100000-581fffff ioport:50000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: f0:7b:cb:87:28:6e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:57100000-5710ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:56100000-570fffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=8192) memory:55000000-560fffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: c0
                serial: 00:23:5a:71:d8:46
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:1000(size=4096) memory:54000000-54ffffff ioport:53000000(size=16777216)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:6080(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6060(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6040(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:58344400-583447ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:60d8(size=8) ioport:60fc(size=4) ioport:60d0(size=8) ioport:60f8(size=4) ioport:6020(size=16) memory:58344000-583443ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54501
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PBBO
                serial: 100315PBPB04ECGA2Y4M
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002f103
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3d6fb382-e202-4abb-b38f-2619503b51da
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-19 23:44:49 filesystem=ext4 lastmountpoint=/ modified=2011-06-04 11:27:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-06-14 11:48:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1013MiB
                   capacity: 1013MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1013MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:6000(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 9412
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

```oh, and the reason i was gone so long is cuz my Android phone "Bricked" this morning after flashing a Radio Update, So ive been stressing all day trying to get Ubuntu to recognize my SDcard in a Micro-SDcard-Reader so i can remove the Radio-Image from the root of my SDcard... So maybe there'll be some useful information 4 this as well in the above:)Hi put this into the terminal
```
sudo lspci -k
``` and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by StarZtorm on 2011-06-14
guys, whoa. Just hold down alt and click to drag the window. By holding down alt you can drag the window over the top border, and then just rescale it so it will fit to your screen.

---

### Post by CleveRuse on 2011-06-17
> **StarZtorm said:**
> guys, whoa. Just hold down alt and click to drag the window. By holding down alt you can drag the window over the top border, and then just rescale it so it will fit to your screen.

WHAT???? that doesnt work at all.By top border, do u mean the top panel where the launchers and applets are? Not only does it still not let me resize, pressing 'alt' does not allow me to move the window over the panel. If the panel was the problem, wouldnt i be able to resize my window while the panel is hidden ...or deleted. And why would it be just a couple windows that i have this problem with? Are u sure u understand the compaint? --Sorry, i dont mean to sound rude or unappreciative.

Maybe it would help to note that Gnome-Color-Chooser doesnt even give me the option to resize it when i right-click on the border, as other windows (like Evolution mail) that also wont allow me to resize beyond a certain point. But even if Gnome-Color-Chooser isnt set up to allow resizing, Evolution must be (since it does give me the option, and i can resize it somewhat) so i like to atleast figure out the problem for this, cuz its bound to repeat itself.

---

### Post by CleveRuse on 2011-06-17
Sorry, I was gone so long, i was having a crisis with my phone. i feel bad that I pretty much abandoned my post ...hope U stil care to help me. I honestly forgot all about it.
here's my output:

```
ab@CleveRuse-LT20:~$ sudo lspci -k
[sudo] password for ab: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0241
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel modules: i2c-i801
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e016
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 0241
    Kernel driver in use: atl1c
    Kernel modules: atl1c
ab@CleveRuse-LT20:~$ 

```

*I'm glad someone can make sense of this stuff cuz it looks like Gibberish to Me:)

---

