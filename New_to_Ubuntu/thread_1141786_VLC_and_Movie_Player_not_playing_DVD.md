---
title: "VLC and Movie Player not playing DVD"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by taurus on 2009-04-28
Where are those .VOB, .IFO, & .BUP located?  Assuming they are in ~/Desktop/movie, you could run vlc from a terminal with

Applications -> Accessories -> Terminal
```
vlc ~/Desktop/movie
```

---

### Post by monomanislive on 2009-05-03
that is the same problem i am having i need this to work   it's one of the reasons a switced to ubuntu because it could play movies  someone help !!!:(

---

### Post by blueridgedog on 2009-05-03
When I have problems such as this, I run the application from a terminal so that I can see any debugging or error messages that appear.  As taurus suggest, run "vnc /path/to/yourmedia" and see if that reveals any other useful bits.

---

### Post by gijello on 2009-05-03
I am having this same exact issue. 

"Could not open location; you might not have permission to open the file."

---

### Post by NimoTh on 2009-05-16
Same here on Jaunty 9.04. VLC tries to load the disc but then stops. No error messages on the console.

Help please

---

### Post by wbee on 2009-05-16
Hello,

See if this helps.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I'm guessing you have the restricted drivers package installed for stuff like Java Script and all?

If not,Applications>add/remove>in the "show" window,select all available applications. Then, in search,type restricted. It will show three. Install the one for your operating system.

Good luck.

---

### Post by goldblattster on 2009-05-16
You do have the libdvdcss library, do you? :D

---

### Post by mjhouska on 2009-10-16
> **wbee said:**
> Hello,

See if this helps.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I'm guessing you have the restricted drivers package installed for stuff like Java Script and all?

If not,Applications>add/remove>in the "show" window,select all available applications. Then, in search,type restricted. It will show three. Install the one for your operating system.

Good luck.
I got a dialogue saying "use synaptic to remove(unnamed) dependencies.

---

### Post by mjhouska on 2009-10-16
K in synaptic (system>administration) search for libdvdcss. select the ubuntu restricted package and accept the changes. this will remove the dependancies and install the software.

---

### Post by mjhouska on 2009-10-16
scratch that it still not workin

---

### Post by mjhouska on 2009-10-16
ill try installing vlc it worked in windows

---

### Post by mjhouska on 2009-10-16
k dvd  now plays in vlc and movie player too LOL! vlc must have added a missing part.

---

### Post by mjhouska on 2009-10-16
movie player dead now will try ejecting and reinserting cd

---

### Post by mjhouska on 2009-10-16
video is playing but i got this
 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.[/COLOR]
 [COLOR=#000000][/COLOR]

---

### Post by mjhouska on 2009-10-16
now it crased and i got this p, li { white-space: pre-wrap; }  
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not read the file.[/COLOR]
 [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.[/COLOR]
 [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.[/COLOR]
 [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.[/COLOR]
 [COLOR=#000000][/COLOR]

---

### Post by mjhouska on 2009-10-16
i give up. will try rolling back

---

### Post by kwacka on 2009-10-16
can you confirm that you have libdvdcss2 installed?

---

### Post by cljbville on 2009-10-18
I had the same problem.  I found my solution here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I had the[FONT=monospace] libdvdread4 already installed.  So I ran the command:

[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh

and that fixed it.  

Good Luck!

---

### Post by 3rdalbum on 2009-10-19
You're doing it wrong.

Don't try playing the .VOB files that are sitting in the DVD's directory; this doesn't work. You need to play the disc from the device, not from the mount point. Go to VLC and Open Disc, and there should be a popup there that allows you to choose your DVD drive. Select it and hit Ok and the disc will play.,

Your DVD drive is probably /dev/dvd or /dev/scd0.

---

### Post by im_prad on 2009-12-16
What If I have .vob file already saved and I want to play that??

The error I get on opening it I have pasted in this file :-

[http://cid-7dd6f65edce61d83.skydrive.live.com/self.aspx/ScreenShots--Etc/Ubuntu--Reltd/Vlc%20Error](http://cid-7dd6f65edce61d83.skydrive.live.com/self.aspx/ScreenShots--Etc/Ubuntu--Reltd/Vlc%20Error)

---

### Post by guilin on 2009-12-16
i did it all but i have the same problem dvd no works i installt all recomondation and lib  , but no way that its gos  vlc  player and media says   p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Fallo de reproducción:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#FF0000]Tu entrada no puede abrirse:[/COLOR]
 [COLOR=#000000]VLC es incapaz de abrir el MRL 'dvd:///dev/sr0'. Ver el registro para más detalles.[/COLOR]
[COLOR=#000000]what is happend what i've to do ?¿? 4 hours to find out and carging  libs and all for nothing what hell i make wrong and all that because i love ubuntu kubuntu linux
[/COLOR]

---

### Post by running_rabbit07 on 2009-12-16
Check out this thread for the answers you need. [http://ubuntuforums.org/showthread.php?t=1356026](http://ubuntuforums.org/showthread.php?t=1356026)

---

### Post by caglar sekmen on 2010-02-19
Go to terminal and type:

 sudo apt-get install libdvdread4

then type:

sudo /usr/share/doc/libdvdread4/install-css.sh

Then go to VLC select open disc from media option and choose the path from browse.

It worked fine for me ..

---

### Post by kittybrat on 2010-03-06
> **caglar sekmen said:**
> Go to terminal and type:

 sudo apt-get install libdvdread4

then type:

sudo /usr/share/doc/libdvdread4/install-css.sh

Then go to VLC select open disc from media option and choose the path from browse.

It worked fine for me ..


This did not work for me.  To be clear, nothing in this thread has helped. :(

I am running Karmic 9.10, and this problem didn't exist before my clean install (previously had Jaunty) just a few days ago.

At first I was getting that same error message from VLC: "Playback failure: VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc. Your input can't be opened: VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details"

So I installed libdvdread4 and tried again.  Now when I go into VLC and tell it to play DVD, the program crashes.

I'm having trouble finding a solution online, because everyone keeps pointing in the direction of libdvdread4.  Unfortunately, I'm not sure that's my problem, since it didn't work.  But I don't know.

Please help. :(

---

### Post by erikthedrink on 2010-04-05
You're not alone.  I'm still getting the same message, even after multiple terminal library updates.:mad:

---

### Post by kittybrat on 2010-04-05
> **erikthedrink said:**
> You're not alone.  I'm still getting the same message, even after multiple terminal library updates.:mad:

Oh, it started working finally after unstalling/reinstalling ... but now I have this problem where my cd rom won't eject a DVD if it has been idle for awhile.  I have a way to eject it, it's just irritating that the button on the hardware won't do it.  At least my program works again, though.

Have you tried uninstalling/reinstalling?  Silly question, I'm sure, but like I said, it (for some reason)worked for me.

---

### Post by erikthedrink on 2010-04-06
I just got home and restarted my laptop.  Now it works!  Yee-Haw!  I'm watching a Region 2 DVD called Oxford Blues with Rob Lowe and a cast of other later-famous British actors.:popcorn:

---

### Post by invisiblephrend on 2010-05-16
Your not gonna believe this, but I had this same problem.  I just resolved it by right clicking the disc icon on the desktop, Open With, VLC.  Worked like a charm.  FACEPALM! #-o

---

### Post by crasbelize on 2010-07-23
> **caglar sekmen said:**
> Go to terminal and type:

 sudo apt-get install libdvdread4

then type:

sudo /usr/share/doc/libdvdread4/install-css.sh

Then go to VLC select open disc from media option and choose the path from browse.

It worked fine for me ..


Hello all.

I have did almost everything in this post but the movie player in Ubuntu 10.04 won't play youtube videos.

Here is the error message from terminal: 

** Message: Error: "http://www.youtube.com/get_video?video_id=vt4X7zFfv4k&t=vjVQa1PpcFOXGBcFpMO3pqbK-tYqaAz8wEOwPiezg3A%3D&fmt=18": Not Found
gstsouphttpsrc.c(1096): gst_soup_http_src_parse_status (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstSoupHTTPSrc:source:
404 Not Found

---

### Post by mc4man on 2010-07-23
> I have did almost everything in this post but the movie player in Ubuntu 10.04 won't play youtube videos.

Don't quite see the connection between dvd video playback and your issue .
If you can't get resolved here then starting a new thread about your issue may prove a bit more beneficial

This was posted today with your same error message, though in lucid I don't see any issues whatsoever with the totem-mozilla plugin and youtube
(32 bit install

[http://ubuntuforums.org/showthread.php?p=9623238#post9623238](http://ubuntuforums.org/showthread.php?p=9623238#post9623238)

(nor have I seen any recent updates to totem-mozilla or totem. -  firefox did update about a wk. ago with no issues

---

### Post by Raizen44 on 2011-03-16
guys, need help with this. Totem player started acting up around January after an update - it stops in the middle of certain DVD's. after the last update it stopped working completely. Then it stopped detecting the DVD drive, and after a lot of fiddling finally got the drive working again, but still having problems with playing DVD's. I keep getting this error message on Totem

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

with VLC, it simply doesn't play. it appears to attempt to play the DVD's, but it never does. I already did the instal-css and I have the codecs that were mentioned earlier in this thread. would be really grateful for some help with this...:confused::confused::confused:

---

### Post by Raizen44 on 2011-03-17
> **Raizen44 said:**
> guys, need help with this. Totem player started acting up around January after an update - it stops in the middle of certain DVD's. after the last update it stopped working completely. Then it stopped detecting the DVD drive, and after a lot of fiddling finally got the drive working again, but still having problems with playing DVD's. I keep getting this error message on Totem

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

with VLC, it simply doesn't play. it appears to attempt to play the DVD's, but it never does. I already did the instal-css and I have the codecs that were mentioned earlier in this thread. would be really grateful for some help with this...:confused::confused::confused:


If it'll help, here are my laptop's specs using sudo lshw:

acheron                   
    description: Computer
    product: M360S
    vendor: CLEVO Co.
    version: N/A
    serial: None
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F54D-AB74-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M360S
       vendor: CLEVO Co.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00 (11/07/05)
          size: 98KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: Socket 479M
          size: 1500MHz
          capacity: 3GHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
        *-cache
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 768MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM [empty]
             physical id: 2
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:e0000000-e3ffffff
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
             resources: ioport:a000(size=4096) memory:e4100000-e41fffff memory:e8000000-efffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:e8000000-efffffff(prefetchable) memory:e4100000-e411ffff ioport:a000(size=128)
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
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8100(size=32)
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:9400(size=16)
           *-disk
                description: ATA Disk
                product: HTS421240H9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: HACO
                serial: HKA040AHCUDESL
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e098b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a84832e9-5d7f-4615-a7ce-dd3cfab26fae
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-09-27 11:59:15 filesystem=ext4 lastmountpoint=/S%W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;-&#65533;ew &#65533;&#65533;x/&#65533;d&#65533;-&#65533;'!&#65533;&#65533;wI&#65533;&#65533;wI&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-&#65533;&#65533;-&#65533;z modified=2011-03-13 02:53:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-17 11:37:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-L462C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:8400(size=256) ioport:9000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:8800(size=256) ioport:9080(size=128)
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
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:e4008000-e4008fff
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
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:e4009000-e4009fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:e400a000-e400afff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:90:f5:4d:ab:74
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
             resources: irq:19 ioport:8c00(size=256) memory:e400b000-e400bfff memory:38000000-3801ffff(prefetchable)
        *-network:1
             description: Wireless interface
             product: RT2561/RT61 rev B 802.11g
             vendor: RaLink
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: wlan0
             version: 00
             serial: 00:08:a1:9c:3a:fb
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci ip=192.168.2.103 latency=64 multicast=yes wireless=IEEE 802.11bg
             resources: irq:16 memory:e4000000-e4007fff
        *-pcmcia
             description: CardBus bridge
             product: CB1410 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:18 memory:38020000-38020fff ioport:1000(size=256) ioport:1400(size=256) memory:30000000-33ffffff(prefetchable) memory:34000000-37ffffff
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


hope someone here can help

---

### Post by djdg on 2011-09-22
The quest for the solution for this problem seems endless. Tried everything that was mentioned in this topic, and a lot other topics on the web. Will keep on searching, and hoping someone finds the solution in the meantime.

I'm using Ubuntu 11.04

---

