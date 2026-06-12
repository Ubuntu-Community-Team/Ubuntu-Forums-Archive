---
title: "How to change Screen Resolution in Old P-3 Desktop"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by nimdave24 on 2010-05-23
Hi Team

First of all I must thank ubuntu team for sending me free Ubuntu 10.04 CD which has inspired me to use Ubuntu. Honestly I m very much new to lunux OS and Ubuntu 10.04 is my first Linux OS. I am just a week old ubuntu user, 

I was using Win-XP since years and I have decent knowledge about those (Windows) OS, but I have installed Ubuntu in one of my old P-3 PC. The Desktop is quite old made, its P-III 465 Mhz, 256 Ram. The PC does not contain any additional graphic card inserted, its the motherboard graphics only. so i dont know its details. (even i have not tried to search it out from the M.board), but its a old P-3 465 Mhz desktop. 

Now from the moment I have installed Ubuntu it has 800 X 600 screen resolution, I have tried to search from where i can change it but i am unable to search it out, can anybody help me how can i change my screen resolution to 1024 X 768 or may be 1200 X 800 please help me .

Suppose in case i need to insert additional graphics card to my mother board can anyone suggest me which is most suitable for me and after inserting the graphic card what I need to do further to change my screen resolution.

Please revert.
Nimesh Dave

---

### Post by -humanaut- on 2010-05-23
Can you type this in a terminal: sudo lshw 

and post back? It's sounds like a graphics card problem there may or may not be a driver available.

---

### Post by nimdave24 on 2010-05-24
> **-humanaut- said:**
> Can you type this in a terminal: sudo lshw 

and post back? It's sounds like a graphics card problem there may or may not be a driver available.
Dear [-humanaut-]("http://ubuntuforums.org/member.php?u=1049264")
Thanks a lot for takiung interest in my thread, but tell you frankly I am new to linux Os and I am not getting what you are asking for.

Can you just elaborate more, how can i find that? what is sudo lshw and from where and how can i find it?

Hope you reply and help me

Regards 
Nimesh

---

### Post by -humanaut- on 2010-05-24
Open a terminal and type sudo lshw

basically that will list the hardware on your computer copy it and paste it back here and I'll be able to determine what drivers, etc... are necessary to help you.

---

### Post by halitech on 2010-05-24
it might be easier to open a terminal and run
```
lspci
```
and paste the info back. This will give less info but enough to tell us what video card you have. Also, if you could tell us the make and model of your monitor, it will help us as well.

---

### Post by romeug on 2010-05-24
this is one of the better means of system analysis and 'repair' that was both instructive and effective, and providing a few differing approaches...

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by nimdave24 on 2010-05-25
> **halitech said:**
> it might be easier to open a terminal and run
```
lspci
```and paste the info back. This will give less info but enough to tell us what video card you have. Also, if you could tell us the make and model of your monitor, it will help us as well.

Dear The details are as under

description: Sub Chassis
    product: Folsom
    vendor: TriGem Computer, Inc.
    version: 1.00
    serial: 0123456789
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific chassis=sub frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: Folsom
       vendor: TriGem Computer, Inc.
       physical id: 0
       version: Rev.A
       serial: 0123456789
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          size: 96KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.5
          slot: Socket370
          size: 466MHz
          capacity: 1133MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM0
             size: 256MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: 82810E DC-133 (GMCH) Graphics Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82810E DC-133 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8000000-fbffffff(prefetchable) memory:f4000000-f407ffff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:f4100000-f41fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:01:06.0
                logical name: eth0
                version: 10
                serial: 00:40:2b:13:18:02
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.28 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:9 ioport:3000(size=256) memory:f4100000-f41000ff
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
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
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1800(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SV2042H
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PK10
                serial: 0263J1CNC04423
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004eeea
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9dd65bdc-1d9c-4d0d-b31d-695c513937c6
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-20 01:12:09 filesystem=ext4 lastmountpoint=/&#65533;&#65533;~pi&#65533;&#65533;*r&#65533;&#65533;%&#916;&#65533;&#65533;u^ &#65533;g&#65533;0&#65533;W/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;v&#65533;h&#65533;v&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a modified=2010-05-20 14:23:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-25 17:00:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 711MiB
                   capacity: 711MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 711MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:1200(size=256) ioport:1300(size=64)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

---

### Post by nimdave24 on 2010-05-25
> **halitech said:**
> it might be easier to open a terminal and run
```
lspci
```and paste the info back. This will give less info but enough to tell us what video card you have. Also, if you could tell us the make and model of your monitor, it will help us as well.


And the result for lspci is

00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Please help me

---

### Post by halitech on 2010-05-25
your video card is
[color="red"]00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)[/color]

try this:

open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```
then
```
gksudo gedit /etc/X11/xorg.conf
```
in the previous 2 commands make sure you put X11 and not x11 as Linux is case sensative. then add
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1024x768" "800x600"
	EndSubSection

EndSection
```
save and reboot and you should have 1024x768 resolution.

---

### Post by nimdave24 on 2010-05-25
> **halitech said:**
> your video card is
[COLOR=red]00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)[/COLOR]

try this:

open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```then
```
gksudo gedit /etc/X11/xorg.conf
```in the previous 2 commands make sure you put X11 and not x11 as Linux is case sensative. then add
```
Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" "true"
    HorizSync    30.0-60.0
    VertRefresh    50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
            Depth        24
            Modes        "1024x768" "800x600"
    EndSubSection

EndSection
```save and reboot and you should have 1024x768 resolution.

Thanks Buddy For your helping hand but somehow its not done yet.  still its shows in 800x600 only and I am afraid it could be 640x480 also, because everything looks so big, you just cant imagine, most of the windows are bigger for my monitor. every website has a bigger scroll, its really horrible, and I really dont want to go back to windows-xp or any else verson
Ok you have also asked for my monitor brand : Its -  LG Studioworks 452V
Hope this may help you to resolve my problem

Thanks again buddy,

---

### Post by halitech on 2010-05-25
did some checking and the native resolution is 1920 x 1200 @60 Hz (24inch screen) so even 1024x768 will look big.

Try changing the HorizSync to 30-83 and the VertRefrsh to 56-75. Then add "1920x1200" to the modes line. should look like this:
```

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" "true"
    HorizSync    30.0-83.0
    VertRefresh    56.0-75.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
            Depth        24
            Modes        "1920x1200" "1024x768" "800x600"
    EndSubSection

EndSection
```

[http://www.lg.com/ca_en/support/product/support-product-profile.jsp?customerModelCode=W2452V-TF&matchedModelCode=2300000404&searchEngineModelCode=W2452V-TF&initialTab=documents&targetPage=support-product-profile#](http://www.lg.com/ca_en/support/product/support-product-profile.jsp?customerModelCode=W2452V-TF&matchedModelCode=2300000404&searchEngineModelCode=W2452V-TF&initialTab=documents&targetPage=support-product-profile#)

---

### Post by -humanaut- on 2010-05-25
product: 82810E DC-133 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation

These cards have a known problem with Ubuntu I've heard it's been fixed with updates if its not fixed I'd recommend giving Debian Stable a try on that system.

---

### Post by nimdave24 on 2010-05-26
> **halitech said:**
> did some checking and the native resolution is 1920 x 1200 @60 Hz (24inch screen) so even 1024x768 will look big.

Try changing the HorizSync to 30-83 and the VertRefrsh to 56-75. Then add "1920x1200" to the modes line. should look like this:
```

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" "true"
    HorizSync    30.0-83.0
    VertRefresh    56.0-75.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
            Depth        24
            Modes        "1920x1200" "1024x768" "800x600"
    EndSubSection

EndSection
```[http://www.lg.com/ca_en/support/product/support-product-profile.jsp?customerModelCode=W2452V-TF&matchedModelCode=2300000404&searchEngineModelCode=W2452V-TF&initialTab=documents&targetPage=support-product-profile#](http://www.lg.com/ca_en/support/product/support-product-profile.jsp?customerModelCode=W2452V-TF&matchedModelCode=2300000404&searchEngineModelCode=W2452V-TF&initialTab=documents&targetPage=support-product-profile#)


Still not done buddy, i dont know what to do, i am bearing all this since almost 10 days and i dont have solution.
 
Well its old configuration PC. Now can we resolve the problem by inserting Graphic card or PCI card? As one of my friend told me that its an old brand so it may not accept the Graphic card (I dont know at what extent its true but he suggested that) so can i insert a suitable PCI card which may resolve the issue??

Can anyone suggest me for the same

Please

---

### Post by sadaruwan12 on 2010-05-26
```
ection "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" "true"
    HorizSync    30.0-83.0
    VertRefresh    56.0-75.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
            Depth        24
            Modes        "1920x1200" "1024x768" "800x600"
            Virtual      1024 768
    EndSubSection

EndSection
```

Try the above configuration let me know if it works or not.

---

### Post by mikewhatever on 2010-05-26
I suspect that computer is way too old for 1920x1200 and for any current Ubuntu release. Even if you fix the resolution, Ubuntu will not run well. I'd much recommend trying Slitaz or Puppy instead.
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
[http://www.puppylinux.com/](http://www.puppylinux.com/)

---

### Post by halitech on 2010-05-26
> **nimdave24 said:**
> Still not done buddy, i dont know what to do, i am bearing all this since almost 10 days and i dont have solution.
 
Well its old configuration PC. Now can we resolve the problem by inserting Graphic card or PCI card? As one of my friend told me that its an old brand so it may not accept the Graphic card (I dont know at what extent its true but he suggested that) so can i insert a suitable PCI card which may resolve the issue??

Can anyone suggest me for the same

Please

without knowing the motherboard its hard to say. most systems will have a least a PCI slot you can use, might have an AGP slot as well. if you can open the case, look and see if there is a brown slot. it should start back about an inch from the edge of the case. PCI cards are getting harder to find but an AGP (if you have the slot) will be easier to find. With it being a P3, chances are you won't have a PCIe slot.

---

### Post by cascade9 on 2010-05-26
Sorry to say, but you will never get 1920x1200 running on i810 video- 

> Intel® 82810 Graphics and Memory Controller Hub (GMCH)  **Supported Features**     [IMG]http://www.intel.com/sites/templates/pix/circuit388.gif[/IMG] 
   The Intel® 82810 graphics controller supports the following:      

[LIST]
[*]2D Graphics
[LIST]
[*]Up to 1600X1200 in 8-bit color at 85Hz refresh
[/LIST]
 
[/LIST]
[http://www.intel.com/support/graphics/intel810/sb/cs-009120.htm](http://www.intel.com/support/graphics/intel810/sb/cs-009120.htm)

Thats 8bit @ 1600x1200. Who wants to uise 256 colour? Not me. IIRC, 16bit colour was limited to 1280x1024, and 24/32bit colour was 1024x768. 

@ halitech- yes, being a p3 there is 0 chance of having a PCIe slot. If nimdave24 is lucky, there will be an AGP slot. 

@ nimdave24- if it is 'corporate' computer (comkpaq, dell, etc) what model computer is it? If its a home made box, the motherboard model number will help....If you dont know the model number, do this from a console- 

sudo lshw

The 'core' value should help a lot to figure out if you have an AGP slot or not. 

> *-core
       description: Motherboard
       product: MS-7388
       vendor: MICRO-STAR INTERNATIONAL CO.,LTD
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.

Or you could always just do it the way I do, with  screwdriver and eyeballs. If you wouldnt recognise an AGP slot that wont help much though.

---

### Post by nimdave24 on 2010-05-28
> **sadaruwan12 said:**
> ```
Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" "true"
    HorizSync    30.0-83.0
    VertRefresh    56.0-75.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
            Depth        24
            Modes        "1920x1200" "1024x768" "800x600"
            Virtual      1024 768
    EndSubSection

EndSection
```Try the above configuration let me know if it works or not.


Hi Buddy
I have tried every suggestion from all you Pros and every trial ended in a failure, none of the trial has changed nothing except your suggestion. atleast by using your suggestion some (positive or negative) alteration happened. Well it has changed the resolution but not as one should expect, means the fonts and icons and windows size remains same but my screen became bigger. means everything was not included on my monitor screen. Means there are some programs on left side of the screen and on the right side of the screen I have a clock on my screen, then when i am seeing program icons on left side, i cant see clock on right side, if i move my mouse cursor on right side the entire screen moves towards left and i can see clock, but that time i can see program icons on the left side, same thing happen to above and below. so my entire screen became bigger than my monitor size.
The font size, icon sizer & windows size does not reduced.

but atleast good try, atleast some change i have seen on my screen. and may be we are closer to the resolution.

Please answer if you have another alternative.

---

### Post by xsinsx on 2010-05-28
Hmm, I know they are trying to help you but the display manager might also help as well its under system -> preferences -> Display and you should be able to change resolution in there. Just a thought.

---

### Post by nimdave24 on 2010-05-28
> **mikewhatever said:**
> I suspect that computer is way too old for 1920x1200 and for any current Ubuntu release. Even if you fix the resolution, Ubuntu will not run well. I'd much recommend trying Slitaz or Puppy instead.
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
[http://www.puppylinux.com/](http://www.puppylinux.com/)


Dear Mikewhatever

I totally agreed with you that my PC is too old for ubuntu 10.04, but this is all why people should shift to linux. isn't it? if I have new configured PC i would rather use Windows new version like vista and win-7, but i know i can not run vista and win 7 on my such old brand pc and thus I shifted to linux where i have all new features which vista and 7 can offer and i can open all office documents with ubuntu10.04 (.doc and .docx whatever i can open with open office 3.2, but if i have office 2003, i can not open .docx file) so that way linux new versions gives you that feel that you no longer a backward community in upcoming windows versions even if you have old p-3 PC. 

Anyways thanks to linux community. but coming to the point ubuntu 10.04 has reduced the speed of my PC significantly so I a, afraid if i run Slitaz or Puppy simultaneously what will happen to my PC, will it be able to lift the load of two OS ?? or not? a big question. So my question is I have never used SLitaz or Puppy, I just have heard about it. and most of the time i found that most of the time these OS (Puppy & slitaz)are used as stand by OS not as main OS. I know we can install Puppy permanently on hard disk, but i dont know about slitaz. and moreover i have never used them so i dont know the feel after installing it permanently on hard disk. are we able to open all programs in puppy? all office docs and all extension file like .doc, .docx, .xlsx etc. PDF files? And importantly do we get the feel that we are in 2010 not in 1995 after installing puppy permanently on hard disk..

If you have used those OS please elaborate more on your experiences about those OS.

Thanks again for your suggestion and waiting for more.

---

### Post by nimdave24 on 2010-05-28
> **xsinsx said:**
> Hmm, I know they are trying to help you but the display manager might also help as well its under system -> preferences -> Display and you should be able to change resolution in there. Just a thought.


Thanks xsinsx for your suggestion, 

but i am afraid to say that, there is no Display submenu in my System ---> Preference. so i dont think i can use it.

---

### Post by sadaruwan12 on 2010-05-28
> **nimdave24 said:**
> Hi Buddy
I have tried every suggestion from all you Pros and every trial ended in a failure, none of the trial has changed nothing except your suggestion. atleast by using your suggestion some (positive or negative) alteration happened. Well it has changed the resolution but not as one should expect, means the fonts and icons and windows size remains same but my screen became bigger. means everything was not included on my monitor screen. Means there are some programs on left side of the screen and on the right side of the screen I have a clock on my screen, then when i am seeing program icons on left side, i cant see clock on right side, if i move my mouse cursor on right side the entire screen moves towards left and i can see clock, but that time i can see program icons on the left side, same thing happen to above and below. so my entire screen became bigger than my monitor size.
The font size, icon sizer & windows size does not reduced.

but atleast good try, atleast some change i have seen on my screen. and may be we are closer to the resolution.

Please answer if you have another alternative.

Nice to here that but sorry I was little busy. Any way I think theres too much tinkering have been done to your xorg.conf file. So what I suggest is to you create a new xorg.conf file. Use the steps below.

> [LIST]
[*]Press CTRL+ALT+F1, Now you'll get to a terminal session
[*]Type sudo service gdm stop this will stop the xserver session.
[*]Now run sudo Xorg -configure. This will create a new xorg.conf file in your home folder.
[*]Type sudo mv /home/<user folder>/xorg.conf.new /etc/X11/xorg.conf
[*]After that type sudo service gdm start
[*]After getting to the GUI restart your system.
[/LIST]

After restarting open the xorg.conf file for editing.

```
sudo gedit /etc/X11/xorg.conf
```

You might see some thing like this
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "glx"
	Load  "dbe"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "HWcursor"           	# [<bool>]
        #Option     "Xinerama"           	# [<bool>]
        #Option     "StaticXinerama"     	# <str>
	Identifier  "Card0"
	Driver      "vmware"
	VendorName  "VMware"
	BoardName   "SVGA II Adapter"
	BusID       "PCI:0:15:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16                
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24                
	EndSubSection
EndSection
```

The above file is from OS that I run in my VMwaer your one might be similar to this as well. If it's not then please post your xorg file with out doing any thing to it so I can have a closer look.

If you have a similar kind of a xorg.conf file then ad this line

```
virtual 1024 768 #this is your resolution add anything you want#
```

and see if it resolves your problem.

---

### Post by sadaruwan12 on 2010-05-28
> **nimdave24 said:**
> Thanks xsinsx for your suggestion, 

but i am afraid to say that, there is no Display submenu in my System ---> Preference. so i dont think i can use it.

Now it known as Monitors.

---

### Post by nimdave24 on 2010-05-28
> **sadaruwan12 said:**
> Now it known as Monitors.

Ok, thanks again I have found it in monitor, but 800x600 is the highest resolution there, the rest 2 are 640x480 and 720x400. All the rest options are inactive so i cant click on that.

Honestly its a painful problem for me,

---

### Post by sadaruwan12 on 2010-05-28
> **nimdave24 said:**
> Dear Mikewhatever

I totally agreed with you that my PC is too old for ubuntu 10.04, but this is all why people should shift to linux. isn't it? if I have new configured PC i would rather use Windows new version like vista and win-7, but i know i can not run vista and win 7 on my such old brand pc and thus I shifted to linux where i have all new features which vista and 7 can offer and i can open all office documents with ubuntu10.04 (.doc and .docx whatever i can open with open office 3.2, but if i have office 2003, i can not open .docx file) so that way linux new versions gives you that feel that you no longer a backward community in upcoming windows versions even if you have old p-3 PC. 

Anyways thanks to linux community. but coming to the point ubuntu 10.04 has reduced the speed of my PC significantly so I a, afraid if i run Slitaz or Puppy simultaneously what will happen to my PC, will it be able to lift the load of two OS ?? or not? a big question. So my question is I have never used SLitaz or Puppy, I just have heard about it. and most of the time i found that most of the time these OS (Puppy & slitaz)are used as stand by OS not as main OS. I know we can install Puppy permanently on hard disk, but i dont know about slitaz. and moreover i have never used them so i dont know the feel after installing it permanently on hard disk. are we able to open all programs in puppy? all office docs and all extension file like .doc, .docx, .xlsx etc. PDF files? And importantly do we get the feel that we are in 2010 not in 1995 after installing puppy permanently on hard disk..

If you have used those OS please elaborate more on your experiences about those OS.

Thanks again for your suggestion and waiting for more.

Sorry to here that but I like to suggest PepperminOS I use it as a stand by but I think it's good enough to be a main OS as well. It run LXDE as a window manager which is very light on you PC resources.

And about that Old PC thing well now days the normal desktops are faster than some severs so the Linux for old PC's I don't think so bro, that's old windows thinking. Never the less if you run Win7 or Vista or your new PC you cant get the performance that a linux distro will give you. You can see the difference right after you install the virus guard to keep the thing that keep the windows safe. In Linux we roam freely with out any memory hugger just to keep the system safe.

Linux is not for Old PC's there a new distros which enables you to use your OLD hadware which those people at Micro$oft never do.

---

### Post by kansasnoob on 2010-05-28
I personally don't like creating and editing an "xorg.conf" with the newer X11.

I prefer this solution:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

That does however only change the Display resolution, if you also desire to change the login screen to the same resolution do this:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Actually the latter of the two changes both the login screen and display resolution, but it won't work with auto-login. You can do both without a problem.

I am concerned about the edits you've made to "xorg.conf" so I'd begin by running:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

And then either rebooting or restarting X.

---

### Post by sadaruwan12 on 2010-05-28
> **nimdave24 said:**
> Dear Mikewhatever

I totally agreed with you that my PC is too old for ubuntu 10.04, but this is all why people should shift to linux. isn't it? if I have new configured PC i would rather use Windows new version like vista and win-7, but i know i can not run vista and win 7 on my such old brand pc and thus I shifted to linux where i have all new features which vista and 7 can offer and i can open all office documents with ubuntu10.04 (.doc and .docx whatever i can open with open office 3.2, but if i have office 2003, i can not open .docx file) so that way linux new versions gives you that feel that you no longer a backward community in upcoming windows versions even if you have old p-3 PC. 

Anyways thanks to linux community. but coming to the point ubuntu 10.04 has reduced the speed of my PC significantly so I a, afraid if i run Slitaz or Puppy simultaneously what will happen to my PC, will it be able to lift the load of two OS ?? or not? a big question. So my question is I have never used SLitaz or Puppy, I just have heard about it. and most of the time i found that most of the time these OS (Puppy & slitaz)are used as stand by OS not as main OS. I know we can install Puppy permanently on hard disk, but i dont know about slitaz. and moreover i have never used them so i dont know the feel after installing it permanently on hard disk. are we able to open all programs in puppy? all office docs and all extension file like .doc, .docx, .xlsx etc. PDF files? And importantly do we get the feel that we are in 2010 not in 1995 after installing puppy permanently on hard disk..

If you have used those OS please elaborate more on your experiences about those OS.

Thanks again for your suggestion and waiting for more.

Sorry to here that but I like to suggest [PepperminOS]("http://peppermintos.com/") I use it as a stand by but I think it's good enough to be a main OS as well. It run LXDE as a window manager which is very light on you PC resources.

And about that Old PC thing well now days the normal desktops are faster than some severs so the Linux for old PC's I don't think so bro, that's old windows thinking. Never the less if you run Win7 or Vista or your new PC you cant get the performance that a linux distro will give you. You can see the difference right after you install the virus guard to keep the thing that keep the windows safe. In Linux we roam freely with out any memory hugger just to keep the system safe.

Linux is not for Old PC's there a new distros which enables you to use your OLD hadware which those people at Micro$oft never do.

---

### Post by nimdave24 on 2010-05-28
> **kansasnoob said:**
> I personally don't like creating and editing an "xorg.conf" with the newer X11.

I prefer this solution:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

That does however only change the Display resolution, if you also desire to change the login screen to the same resolution do this:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Actually the latter of the two changes both the login screen and display resolution, but it won't work with auto-login. You can do both without a problem.

I am concerned about the edits you've made to "xorg.conf" so I'd begin by running:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```And then either rebooting or restarting X.



I have tried from 
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
But I have got the following msgs


vphr04 is my user & PC name

vphr04@vphr04:~$ xrandr
Screen 0: minimum 640 x 400, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        67.0     60.0  
   720x400        70.0  
vphr04@vphr04:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
vphr04@vphr04:~$ xrandr --newmode “1024×768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
vphr04@vphr04:~$ xrandr --newmode “1024×768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18
vphr04@vphr04:~$ 


Would it be possible to change to 1024x768 in my PC?

---

### Post by nimdave24 on 2010-05-29
Dear Friends

Thanks a lot for your efforts to help me out to resolve my problem. but unfortunately i m fed up with it and ultimately i have surrendered, I thing i can not live with ubuntu anymore. There are several draw-backs which i have observed with it
(1) Ubuntu is taking more time to boot, and if you wish to open open office, its take hours to open in my system, so i will not recommend ubuntu for older PCs

(2) The resolution problem is persistent as ever, not with me but lots of people like me facing the same screen resolution problem, somehow they may find the solutions but I did not.

(3) There are lots of unnecessary programs in ubuntu which makes ubuntu slower compared to other linux os. 

But positive points are also there
like the most used linux os
one of the best forums
Getting quick reverts from forums
Perhaps it is the only company (Canonical) which sends free OS CD to your place on their own expense.
previously there may be many, but almost everyone has stopped sending free OS CD, but ubuntu still continue sending free CDs

So i have decided to churn from ubuntu, but i will not leave linux OS
Can anyone suggest me the fastest booting linux OS
The linux OS offers maximum speed. lightening fast, takes least time to open programs like open office etc. and importantly i have ancient model of PC so the idea; linux OS that runs best on the old PCs

Please suggest me the replacement for Ubuntu

---

### Post by halitech on 2010-05-29
sorry to see you go from Ubuntu but at least you are willing to try another distro. I just gave away a P3 500 with 192 meg of ram that I had installed debian with LXDE and it ran fine. You can do a minimal install and customize it yourself or just use the LXDE install cd.

[http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso)

---

### Post by wise_crypt on 2010-06-07
try this might help if you not using gdm :
```
sudo nano /etc/xdg/lxsession/LXDE/autostart
put this on the last line:
xrandr -s 1024x768
```actually you can put any startup command using this method; hope that help

---

### Post by herdivet on 2010-10-17
> **nimdave24 said:**
> Dear Friends

Thanks a lot for your efforts to help me out to resolve my problem. but unfortunately i m fed up with it and ultimately i have surrendered, I thing i can not live with ubuntu anymore. There are several draw-backs which i have observed with it
(1) Ubuntu is taking more time to boot, and if you wish to open open office, its take hours to open in my system, so i will not recommend ubuntu for older PCs

(2) The resolution problem is persistent as ever, not with me but lots of people like me facing the same screen resolution problem, somehow they may find the solutions but I did not.

(3) There are lots of unnecessary programs in ubuntu which makes ubuntu slower compared to other linux os. 

But positive points are also there
like the most used linux os
one of the best forums
Getting quick reverts from forums
Perhaps it is the only company (Canonical) which sends free OS CD to your place on their own expense.
previously there may be many, but almost everyone has stopped sending free OS CD, but ubuntu still continue sending free CDs

So i have decided to churn from ubuntu, but i will not leave linux OS
Can anyone suggest me the fastest booting linux OS
The linux OS offers maximum speed. lightening fast, takes least time to open programs like open office etc. and importantly i have ancient model of PC so the idea; linux OS that runs best on the old PCs

Please suggest me the replacement for Ubuntu

I know this thread is old, and you may have already found exactly what you want, but here's my experience.  Since you've tried Ubuntu and have some experience with it, you might consider lubuntu.

I have an old (PIII 1Ghz) that I beefed up to 1GB RAM and I am running lubuntu on it.  I am replying to you on this PC.

I don't think you'll get 'lightning fast' performance from any graphical OS with this old hardware, but I am able to open documents, spreadsheets, browse the web, etc. in an acceptable manner with this box.  No one will mistake it for a new system, but it gets the job done.

I hope this helps, and you're happy with your system now.

'Your mileage may vary'

---

