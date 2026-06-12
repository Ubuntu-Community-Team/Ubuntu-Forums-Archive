---
title: "Ok need some help.(wireless and boot-up)"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Scorcher21 on 2009-08-30
Ive been looking through a bunch of threads and cant seem to get what I need. I'm most likely missing something and if so, sorry for restating answered questions.

First off, I'm running a computer with umbuntu jaunty on 1 HDD and Win XP home on another HDD. Is there a way to select which OS boots? there isn't an option in my BIOS, right now I'm having to go in and change the boot order. Not a huge deal but the OS boot option would be better.

Second and more importantly I'm having real trouble getting my wireless up and running.
I've installed ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb and ndisgtk_0.8.4-1_i386.deb and also wifi-radar.

here is my sudo lshw:  (I've highlighted in [COLOR=Red]red[/COLOR] my network cards) [COLOR=Black]

[/COLOR] 	 	 me@H:~$ sudo lshw  
 [sudo] password for me:  
 h                          
     description: Desktop Computer  
     product: MS-6712  
     vendor: MSI  
     version: 1.0  
     serial: 00000000  
     width: 32 bits  
     capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp  
     configuration: chassis=desktop cpus=1  
   *-core  
        description: Motherboard  
        product: MS-6712  
        vendor: MSI  
        physical id: 0  
        version: 1.0  
        serial: 00000000  
      *-firmware  
           description: BIOS  
           vendor: American Megatrends Inc.  
           physical id: 0  
           version: Version 07.00T (04/02/01)  
           size: 64KiB  
           capacity: 192KiB  
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification  
      *-cpu  
           description: CPU  
           product: AMD Athlon(tm) XP 2700+  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 4  
           bus info: cpu@0  
           version: 6.8.1  
           slot: Socket-A  
           size: 2150MHz  
           capacity: 3GHz  
           width: 32 bits  
           clock: 165MHz  
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
              size: 256KiB  
              capacity: 1MiB  
              capabilities: synchronous internal write-back unified  
      *-memory  
           description: System memory  
           physical id: 1  
           size: 1255MiB  
      *-pci  
           description: Host bridge  
           product: VT8377 [KT400/KT600 AGP] Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 80  
           width: 32 bits  
           clock: 66MHz  
           configuration: driver=agpgart-via latency=8 module=via_agp  
         *-pci  
              description: PCI bridge  
              product: VT8237/VX700 PCI Bridge  
              vendor: VIA Technologies, Inc.  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci pm bus_master cap_list  
            *-display UNCLAIMED  
                 description: VGA compatible controller  
                 product: GeForce 7300 GT  
                 vendor: nVidia Corporation  
                 physical id: 0  
                 bus info: pci@0000:01:00.0  
                 version: a2  
                 width: 32 bits  
                 clock: 66MHz  
                 capabilities: pm agp agp-3.0 bus_master cap_list  
                 configuration: latency=248 maxlatency=1 mingnt=5  
         [COLOR=#ff0000]*-network:0 [/COLOR] 
 [COLOR=#ff0000]             description: Network controller [/COLOR] 
 [COLOR=#ff0000]             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [/COLOR] 
 [COLOR=#ff0000]             vendor: Broadcom Corporation [/COLOR] 
 [COLOR=#ff0000]             physical id: 6 [/COLOR] 
 [COLOR=#ff0000]             bus info: pci@0000:00:06.0 [/COLOR] 
 [COLOR=#ff0000]             version: 02 [/COLOR] 
 [COLOR=#ff0000]             width: 32 bits [/COLOR] 
 [COLOR=#ff0000]             clock: 33MHz [/COLOR] 
 [COLOR=#ff0000]             capabilities: bus_master [/COLOR] 
 [COLOR=#ff0000]             configuration: driver=b43-pci-bridge latency=248 module=ssb [/COLOR] 
         *-usb:0  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10  
              bus info: pci@0000:00:10.0 
              version: 80  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=248 module=uhci_hcd  
         *-usb:1  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10.1  
              bus info: pci@0000:00:10.1 
              version: 80  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=248 module=uhci_hcd  
         *-usb:2  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10.2  
              bus info: pci@0000:00:10.2 
              version: 80  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=248 module=uhci_hcd  
         *-usb:3  
              description: USB Controller  
              product: USB 2.0  
              vendor: VIA Technologies, Inc.  
              physical id: 10.3  
              bus info: pci@0000:00:10.3 
              version: 82  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=ehci_hcd latency=248 module=ehci_hcd  
         *-isa  
              description: ISA bridge  
              product: VT8235 ISA Bridge 
              vendor: VIA Technologies, Inc.  
              physical id: 11  
              bus info: pci@0000:00:11.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa pm bus_master cap_list  
              configuration: latency=0  
         *-ide  
              description: IDE interface 
              product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE  
              vendor: VIA Technologies, Inc.  
              physical id: 11.1  
              bus info: pci@0000:00:11.1 
              logical name: scsi0  
              logical name: scsi1  
              version: 06  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide pm bus_master cap_list emulated  
              configuration: driver=pata_via latency=32  
            *-disk:0  
                 description: ATA Disk  
                 product: WDC WD800BB-08JH  
                 vendor: Western Digital 
                 physical id: 0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/sda  
                 version: 06.0  
                 serial: WD-WCAM9M471026 
                 size: 74GiB (80GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=efe2efe2  
               *-volume:0  
                    description: EXT3 volume  
                    vendor: Linux  
                    physical id: 1  
                    bus info: scsi@0:0.0.0,1  
                    logical name: /dev/sda1  
                    logical name: /  
                    version: 1.0  
                    serial: bb0ef65a-4cdd-4d30-b6e8-76e81f9d4c78  
                    size: 71GiB  
                    capacity: 71GiB  
                    capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized  
                    configuration: created=2009-08-30 01:27:11 filesystem=ext3 modified=2009-08-30 10:57:29 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-30 10:46:00 state=mounted  
               *-volume:1  
                    description: Extended partition  
                    physical id: 2  
                    bus info: scsi@0:0.0.0,2  
                    logical name: /dev/sda2  
                    size: 3153MiB  
                    capacity: 3153MiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 3153MiB 
                       capabilities: nofs  
            *-disk:1  
                 description: ATA Disk  
                 product: WDC WD800JB-00JJ  
                 vendor: Western Digital 
                 physical id: 1  
                 bus info: scsi@0:0.1.0  
                 logical name: /dev/sdb  
                 version: 05.0  
                 serial: WD-WCAM9M546740 
                 size: 74GiB (80GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=220fac66  
               *-volume  
                    description: Windows NTFS volume  
                    physical id: 1  
                    bus info: scsi@0:0.1.0,1  
                    logical name: /dev/sdb1  
                    version: 3.1  
                    serial: 8a0198f8-2cd7-5344-8ba3-b3ebac0a1672  
                    size: 74GiB  
                    capacity: 74GiB  
                    capabilities: primary bootable ntfs initialized  
                    configuration: clustersize=4096 created=2009-08-07 12:55:01 filesystem=ntfs state=clean  
            *-cdrom:0  
                 description: DVD reader 
                 product: CDW/DVD TS-H492A  
                 vendor: TSSTcorp  
                 physical id: 2  
                 bus info: scsi@1:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 logical name: /media/cdrom0  
                 version: TB02  
                 capabilities: removable audio cd-r cd-rw dvd  
                 configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready  
               *-medium  
                    physical id: 0  
                    logical name: /dev/cdrom  
                    logical name: /media/cdrom0  
                    configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted 
            *-cdrom:1  
                 description: DVD-RAM writer  
                 product: DVDRW LH-20A1H 
                 vendor: LITE-ON  
                 physical id: 3  
                 bus info: scsi@1:0.1.0  
                 logical name: /dev/cdrom1  
                 logical name: /dev/cdrw1  
                 logical name: /dev/dvd1 
                 logical name: /dev/dvdrw1  
                 logical name: /dev/scd1 
                 logical name: /dev/sr1  
                 version: LL0C  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 status=nodisc  
         *-multimedia  
              description: Multimedia audio controller  
              product: VT8233/A/8235/8237 AC97 Audio Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 11.5  
              bus info: pci@0000:00:11.5 
              version: 50  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm cap_list  
              configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx  
         [COLOR=#ff0000]*-network:1 [/COLOR] 
 [COLOR=#ff0000]             description: Ethernet interface [/COLOR] 
 [COLOR=#ff0000]             product: VT6102 [Rhine-II] [/COLOR] 
 [COLOR=#ff0000]             vendor: VIA Technologies, Inc. [/COLOR] 
 [COLOR=#ff0000]             physical id: 12 [/COLOR] 
 [COLOR=#ff0000]             bus info: pci@0000:00:12.0 [/COLOR] 
 [COLOR=#ff0000]             logical name: eth0 [/COLOR] 
 [COLOR=#ff0000]             version: 74 [/COLOR] 
 [COLOR=#ff0000]             serial: 00:0c:76:f1:67:b9 [/COLOR] 
 [COLOR=#ff0000]             size: 10MB/s [/COLOR] 
 [COLOR=#ff0000]             capacity: 100MB/s [/COLOR] 
 [COLOR=#ff0000]             width: 32 bits [/COLOR] 
 [COLOR=#ff0000]             clock: 33MHz [/COLOR] 
 [COLOR=#ff0000]             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/COLOR] 
 [COLOR=#ff0000]             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=248 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s [/COLOR] 
      *-scsi  
           physical id: 2  
           bus info: usb@1:4  
           logical name: scsi2  
           capabilities: emulated scsi-host  
           configuration: driver=usb-storage  
         *-disk  
              description: SCSI Disk  
              physical id: 0.0.0  
              bus info: scsi@2:0.0.0  
              logical name: /dev/sdc  
              size: 995MiB (1043MB)  
              capabilities: partitioned partitioned:dos  
            *-volume  
                 description: Windows FAT volume  
                 vendor: MSWIN4.1  
                 physical id: 1  
                 bus info: scsi@2:0.0.0,1  
                 logical name: /dev/sdc1 
                 logical name: /media/disk  
                 version: FAT16  
                 serial: 2f49-35a0  
                 size: 994MiB  
                 capacity: 994MiB  
                 capabilities: primary bootable fat initialized  
                 configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted  
  [COLOR=#ff0000] *-network:0 DISABLED [/COLOR] 
 [COLOR=#ff0000]       description: Wireless interface [/COLOR] 
 [COLOR=#ff0000]       physical id: 1 [/COLOR] 
 [COLOR=#ff0000]       logical name: wlan0 [/COLOR] 
 [COLOR=#ff0000]       serial: 00:21:29:68:31:5f [/COLOR] 
 [COLOR=#ff0000]       capabilities: ethernet physical wireless [/COLOR] 
 [COLOR=#ff0000]       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg [/COLOR] 
 [COLOR=#ff0000]  *-network:1 DISABLED [/COLOR] 
 [COLOR=#ff0000]       description: Ethernet interface [/COLOR] 
 [COLOR=#ff0000]       physical id: 2 [/COLOR] 
 [COLOR=#ff0000]       logical name: pan0 [/COLOR] 
 [COLOR=#ff0000]       serial: da:95:ec:ea:13:73 [/COLOR] 
 [COLOR=#ff0000]       capabilities: ethernet physical [/COLOR] 
 [COLOR=#ff0000]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes [/COLOR] 
 [COLOR=#ff0000]me@H:~$ [/COLOR] 
 
[COLOR=Black]

here is a screenshot of my wireless network drivers
[IMG]http://i6.photobucket.com/albums/y215/Scorcher21/Screenshot-WirelessNetworkDrivers.png[/IMG]

and heres what happens when I try to configure network
[IMG]http://i6.photobucket.com/albums/y215/Scorcher21/cnnect.png[/IMG]
[/COLOR]
also when I try and run wifi-radar I get this error message in the background:

"[COLOR=Red]***wlan0     Interface doesn't support scanning : Network is down***[/COLOR]" over and over and over again.




Sorry thread is so long but just trying to give as much info as I know. And FYI I am very new to linux and programming so be gentle with the help :-)

---

### Post by Liolikas on 2009-08-30
Brief topics more fun to help, now like ohh I will have to read all this..when I will be over there will be 10 posts already. :lolflag:

Ok back to topic...

>Is there a way to select which OS boots? 
Yes it is you have to set up GRUB correctly. Edit /boot/grub/menu.lst file. Look google for examples.

And with that error do this:
> 
In a terminal:

sudo gedit /etc/NetworkManager/nm-system-settings.conf

under [ifupdown], change managed=true

save file, exit

sudo apt-get install gnome-network-admin

then restart the computer.


---

### Post by Scorcher21 on 2009-08-30
OK tried that



[IMG]http://i6.photobucket.com/albums/y215/Scorcher21/Screenshot-nm-system-settingsconf-e.png[/IMG]

and got this 

[IMG]http://i6.photobucket.com/albums/y215/Scorcher21/huh.png[/IMG]

and nothing seems to have changed.



As for the Grub I think I can get that just gonna take some work thank you.

---

### Post by tgeer43 on 2009-08-30
Here's what I did to get mine working.

Open up a terminal and enter the following commands:
```
ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid  *YOURESSID* 
iwconfig wlan0 key open *YOURWEPKEY*
dhcpcd -d wlan0
```Replacing *YOURESSID and **YOURWEPKEY *with the appropriate values for your network. If you're not using WEP security, it's probably OK to omit that line entirely. If you get an error about dhcpcd not being installed then just install it in Synaptic Package Manager. Please note that the first command is **_if_**config while the next three are **_iw_**config.

If this gets you connected then it's just a matter of adding the above lines to your /etc/rc.local file to have the system automatically connect you at each system start.

This has nothing to do with ndiswrapper or the other packages that you installed so you'd be able to uninstall them.

tgeer

[edit] The "Couldn't find package gnome-network-admin" error is because apt-get is trying to download the package from the repository and you're still not connected to the internet. Once you do get connected you can install that package and you'll have a nice little GUI program to easily configure your network connections.

---

### Post by Scorcher21 on 2009-08-30
ok,    


used my xp os and got the gnome-network-admin

so now I get the nice gui.

however once I try to change any values I get an error that I dont have permission

If I login through the terminal   'sodu network-admin' it prompts me for my password and accepts it opens the gui and same problem denied permission.

also when i enter ifconfig wlan0 up  it tells me permission denied also.

---

### Post by tgeer43 on 2009-08-30
Guess I should have mentioned that when entering those commands in a terminal they need to be prefixed with 'sudo':
```
sudo ifconfig wlan0 up
```My bad. I didn't even think about it since my commands are in /etc/rc.local which runs as root.

tgeer

---

### Post by roofnron on 2009-08-30
I am new user - just installed and couldn't get my wireless working either. 

I followed instructions here and it worked perfectly. 

[http://www.associatedcontent.com/article/1753452/how_to_get_wireless_working_with_ubuntu.html?singlepage=true&cat=15]("http://www.associatedcontent.com/article/1753452/how_to_get_wireless_working_with_ubuntu.html?singlepage=true&cat=15")

I didn't have to go so far as MadWifi or Ndiswrapper.

---

### Post by tgeer43 on 2009-08-30
Roofnron, that sounds like it might be just the ticket since the OP *does* have a Broadcom adapter.

Scorched21, remove the installed Windows driver before following that tutorial.

tgeer

---

