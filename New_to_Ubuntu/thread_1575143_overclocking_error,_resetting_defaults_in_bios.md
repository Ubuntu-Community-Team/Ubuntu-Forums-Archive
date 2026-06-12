---
title: "overclocking error, resetting defaults in bios"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by salima on 2010-09-15
p { margin-bottom: 0.21cm; }  I am trying to restore factory defaults from the bios for clock settings. (dont know the proper terms, sorry) i read that i should select 'load optimized defaults', but i dont know where to find that option.
 

 Should i be looking in cpu or chipset or somewhere else? It kind of freaks me out to go in there too, but not as much as the other option of removing the cmos battery...nonono, i wouldnt want to try that, i would feel like i was attempting brain surgery with no diploma.
 

 I have a hcl pc with american trend bios, if that is any help.

---

### Post by lukeiamyourfather on 2010-09-15
What motherboard or computer do you have? Each is slightly different so instructors for one board might not work on another.

---

### Post by vivek40 on 2010-09-15
Did you try  doing this first!
[http://tinyurl.com/2uurze5](http://tinyurl.com/2uurze5)

:-)

As suggested by Luke above, please post your motherboard and computer specs
sudo lshw

Also what is the error you are getting!

---

### Post by cascade9 on 2010-09-15
> **salima said:**
> p { margin-bottom: 0.21cm; }  I am trying to restore factory defaults from the bios for clock settings. (dont know the proper terms, sorry) i read that i should select 'load optimized defaults', but i dont know where to find that option.

 Should i be looking in cpu or chipset or somewhere else? It kind of freaks me out to go in there too, but not as much as the other option of removing the cmos battery...nonono, i wouldnt want to try that, i would feel like i was attempting brain surgery with no diploma.
 
 I have a hcl pc with american trend bios, if that is any help.

Normally that setting is on the initial BIOS screen. Like here- 

[IMG]http://www.legitreviews.com/images/reviews/1158/EVGA-P55-FTW-BIOS-Main.jpg[/IMG]

BTW, after you've used that setting, I'd go poking around in the BIOS and turn off all the junk you dont use/need (things like serial ports). You dont need to do that, but I always do.

---

### Post by salima on 2010-09-15
sorry-that was american megatrends...but mine doesnt look anything like the screen here in  the comment. i will go back in and write down the options and come back tomorrow-hurt my hand and have to use my left hand for now...really tired.

here is the lshw:

  	 	 	 	p { margin-bottom: 0.21cm; }  root@salima-desktop:~# lshw  
 salima-desktop             
     description: Desktop Computer  
     product: P5GC-TVM-SI  
     vendor: HCL Infosystems Limited  
     version: System Version  
     serial: 7073A1002932  
     width: 32 bits  
     capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp  
     configuration: boot=normal chassis=desktop cpus=2 uuid=18F30839-0E12-DC11-ABF0-0C2CFBD7E124  
 

 

   *-core  
        description: Motherboard  
        product: P5GC-TVM-SI  
        vendor: ASUSTeK Computer INC.  
        physical id: 0  
        version: Rev 1.xx  
        serial: MB-1234567890  
        slot: To Be Filled By O.E.M.  
 

      *-firmware  
           description: BIOS  
           vendor: American Megatrends Inc.  
           physical id: 0  
           version: 0201 (03/09/2007)  
           size: 64KiB  
           capacity: 448KiB  
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification  
 

 

 

      *-cpu:0                               (....................is this the power suppply?)
           description: CPU  
           product: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz  
           vendor: Intel Corp.  
           physical id: 4  
           bus info: cpu@0  
           version: 6.15.13  
           serial: 0000-06FD-0000-0000-0000-0000  
           slot: LGA 775  
           size: 1200MHz  
           capacity: 3800MHz  
           width: 64 bits  
           clock: 200MHz  
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq  
           **configuration: id=1 ** 
 

         *-cache:0  
              description: L1 cache  
              physical id: 5  
              slot: L1-Cache  
              size: 32KiB  
              capacity: 32KiB  
              capabilities: pipeline-burst internal varies data  
         *-cache:1  
              description: L2 cache  
              physical id: 6  
              slot: L2-Cache  
              size: 2MiB  
              capacity: 2MiB  
              capabilities: pipeline-burst internal varies instruction  
         *-logicalcpu:0  
              description: Logical CPU  
              **physical id: 1.1 ** 
              width: 64 bits  
              capabilities: logical  
         *-logicalcpu:1  
              description: Logical CPU  
              **physical id: 1.2 ** 
              width: 64 bits  
              capabilities: logical  
 

 

 

      *-memory  
           description: System Memory  
           physical id: 32  
           slot: System board or motherboard  
           size: 1GiB                       .........................................(kinda skimpy aint it?)
         *-bank:0  
              description: DIMM SDRAM Synchronous  
              product: PartNum0  
              vendor: Manufacturer0  
              physical id: 0  
              serial: SerNum0  
              slot: DIMM0  
              size: 1GiB  
              width: 64 bits  
         *-bank:1  
              description: DIMM [empty]  
              product: PartNum1  
              vendor: Manufacturer1  
              physical id: 1  
              serial: SerNum1  
              slot: DIMM1  
 

 

 

      *-cpu:1  
           physical id: 1  
           bus info: cpu@1  
           version: 6.15.13  
           serial: 0000-06FD-0000-0000-0000-0000  
           size: 1200MHz  
           capacity: 1200MHz  
           capabilities: ht cpufreq  
           configuration: id=1  
         *-logicalcpu:0  
              description: Logical CPU  
              **physical id: 1.1 ** 
              capabilities: logical  
         *-logicalcpu:1  
              description: Logical CPU  
              **physical id: 1.2 ** 
              capabilities: logical  
      *-pci  
           description: Host bridge  
           product: 82945G/GZ/P/PL Memory Controller Hub  
           vendor: Intel Corporation  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 02  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=agpgart-intel  
           **resources: irq:0 ** 
 

         *-display  
              description: VGA compatible controller  
              product: 82945G/GZ Integrated Graphics Controller  
              vendor: Intel Corporation  
              physical id: 2  
              bus info: pci@0000:00:02.0  
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: msi pm bus_master cap_list rom  
              configuration: driver=i915 latency=0  
              resources: irq:16 memory:cfe00000-cfe7ffff ioport:9800(size=8) memory:d0000000-dfffffff(prefetchable) memory:cfe80000-cfebffff  
 

         *-multimedia  
              description: Audio device  
              product: N10/ICH 7 Family High Definition Audio Controller  
              vendor: Intel Corporation  
              physical id: 1b  
              bus info: pci@0000:00:1b.0  
              version: 01  
              width: 64 bits  
              clock: 33MHz  
              capabilities: pm msi pciexpress bus_master cap_list  
              configuration: driver=HDA Intel latency=0  
              resources: irq:19 memory:cfef8000-cfefbfff  
 

         *-pci:0  
              description: PCI bridge  
              product: N10/ICH 7 Family PCI Express Port 1  
              vendor: Intel Corporation  
              physical id: 1c  
              bus info: pci@0000:00:1c.0  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pciexpress msi pm bus_master cap_list  
              configuration: driver=pcieport  
              **resources: irq:24 ioport:e000(size=4096) memory:40000000-401fffff memory:40200000-403fffff(prefetchable) ** 
 

         *-usb:0  
              description: USB Controller  
              product: **N10**/ICH7 Family USB UHCI Controller #1  
              vendor: Intel Corporation  
              physical id: 1d  
              bus info: pci@0000:00:1d.0  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              **resources: irq:20 ioport:a000(size=32) ** 
 

         *-usb:1  
              description: USB Controller  
              product: **N10**/ICH 7 Family USB UHCI Controller #2  
              vendor: Intel Corporation  
              physical id: 1d.1  
              bus info: pci@0000:00:1d.1  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              **resources: irq:17 ioport:a400(size=32) ** 
 

         *-usb:2  
              description: USB Controller  
              product: **N10**/ICH 7 Family USB UHCI Controller #3  
              vendor: Intel Corporation  
              physical id: 1d.2  
              bus info: pci@0000:00:1d.2  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              **resources: irq:18 ioport:a800(size=32) ** 
 

         *-usb:3  
              description: USB Controller  
              product: **N10/**ICH 7 Family USB UHCI Controller #4  
              vendor: Intel Corporation  
              physical id: 1d.3  
              bus info: pci@0000:00:1d.3  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              **resources: irq:19 ioport:b000(size=32) ** 
 

         *-usb:4  
              description: USB Controller  
              product: **N10**/ICH 7 Family USB2 EHCI Controller  
              vendor: Intel Corporation  
              physical id: 1d.7  
              bus info: pci@0000:00:1d.7  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm debug bus_master cap_list  
              configuration: driver=ehci_hcd latency=0  
              **resources: irq:20 memory:cfeffc00-cfefffff ** 
 

         *-pci:1  
              description: PCI bridge  
              product: 82801 PCI Bridge  
              vendor: Intel Corporation  
              physical id: 1e  
              bus info: pci@0000:00:1e.0  
              version: e1  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci bus_master cap_list  
              **resources: ioport:d000(size=4096) memory:cff00000-cfffffff memory:40400000-404fffff(prefetchable) ** 
 

            *-network  
                 description: Ethernet interface  
                 product: RTL-8110SC/8169SC Gigabit Ethernet  
                 vendor: Realtek Semiconductor Co., Ltd.  
                 physical id: 4  
                 bus info: pci@0000:01:04.0  
                 logical name: eth0  
                 version: 10  
                 serial: 00:1b:fc:53:6e:bd  
                 size: 10MB/s  
                 capacity: 1GB/s  
                 width: 32 bits  
                 clock: 66MHz  
                 capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
                 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s  
                 **resources: irq:19 ioport:d800(size=256) memory:cffffc00-cffffcff memory:40400000-4041ffff(prefetchable) ** 
 

         *-isa  
              description: ISA bridge  
              product: 82801GB/GR (ICH7 Family) LPC Interface Bridge  
              vendor: Intel Corporation  
              physical id: 1f  
              bus info: pci@0000:00:1f.0  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa bus_master cap_list  
              configuration: latency=0  
 

         *-ide:0  
              description: IDE interface  
              product: 82801G (ICH7 Family) IDE Controller  
              vendor: Intel Corporation  
              physical id: 1f.1  
              bus info: pci@0000:00:1f.1  
              logical name: scsi0  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide bus_master emulated  
              configuration: driver=ata_piix latency=0  
              **resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) ** 
 

            *-cdrom  
                 description: DVD-RAM writer  
                 product: BAER DH-20A4P  
                 vendor: MOSER  
                 physical id: 0.0.0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw  
                 logical name: /dev/dvd  
                 logical name: /dev/dvdrw  
                 logical name: /dev/scd0  
                 logical name: /dev/sr0  
                 version: 9M74  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 status=nodisc  
 

         *-ide:1  
              description: IDE interface  
              product: **N10**/ICH7 Family SATA IDE Controller  
              vendor: Intel Corporation  
              physical id: 1f.2  
              bus info: pci@0000:00:1f.2  
              logical name: scsi3  
              version: 01  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ide pm bus_master cap_list emulated  
              configuration: driver=ata_piix latency=0  
              **resources: irq:17 ioport:c800(size=8) ioport:c400(size=4) ioport:c000(size=8) ioport:b800(size=4) ioport:b400(size=16) ** 
 

            *-disk  
                 description: ATA Disk  
                 product: Hitachi HDS72161  
                 vendor: Hitachi  
                 physical id: 0.0.0  
                 bus info: scsi@3:0.0.0  
                 logical name: /dev/sda  
                 version: P22O  
                 serial: PVG904ZHS8ES1V  
                 size: 149GiB (160GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=00072bfb  
 

               *-volume:0  
                    description: **EXT4 volume ** 
                    vendor: Linux  
                    physical id: 1  
                    bus info: scsi@3:0.0.0,1  
                    logical name: /dev/sda1  
                    logical name: /  
                    version: 1.0  
                    serial: 4e8521c9-5a9a-4af3-81a7-fd873941bcc0  
                    size: 146GiB  
                    capacity: 146GiB  
                    capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized  
                    configuration: created=2010-09-03 05:24:01 filesystem=ext4 lastmountpoint=/9&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;p&#65533;&#65533;&#65533;u^ &#65533;U/&#65533;d&#65533;&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;&#798;&#65533;&#65533;&#65533;&#65533;a modified=2010-09-05 16:17:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-05 16:17:09 state=mounted  
 

 

               *-volume:1  
                    description: Extended partition  
                    physical id: 2  
                    bus info: scsi@3:0.0.0,2  
                    logical name: /dev/sda2  
                    size: 2909MiB  
                    capacity: 2909MiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 2909MiB  
                       capabilities: nofs  
 

         *-serial UNCLAIMED  
              description: SMBus  
              product: N10/ICH 7 Family SMBus Controller  
              vendor: Intel Corporation  
              physical id: 1f.3  
              bus info: pci@0000:00:1f.3  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              configuration: latency=0  
              **resources: ioport:400(size=32) ** 
 root@salima-desktop:~#

---

### Post by salima on 2010-09-15
sorry, forgot to say the error is 'overclocking or overvoltage failed'

and i dont know why there are smilies in the lshw...on my copy they are 8's

---

### Post by realzippy on 2010-09-15
[http://pctechnotes.com/wp-content/uploads/2009/09/remove-battery.jpg](http://pctechnotes.com/wp-content/uploads/2009/09/remove-battery.jpg)

..unplug the battery on the mainboard for a few seconds.This should return to default settings.

EDIT: Sorry-overread this:
*.. not as much as the other option of removing the cmos battery...nonono, i wouldnt want to try that, i would feel like i was attempting brain surgery with no diploma.*


EDIT2:
On the other hand when asking
*Should i be looking in cpu or chipset or somewhere else?*
you should wait with overclocking until you know what you are doing.BTW,Ubuntu (default) "downclocks" your CPU to save power;and generally I see no use in overclocking an ubuntu system;may I ask what you are going to do with that machine?&#960; calculating  ;-)  ?

---

### Post by cascade9 on 2010-09-15
> **salima said:**
> sorry-that was american megatrends...but mine doesnt look anything like the screen here in the comment. i will go back in and write down the options and come back tomorrow-hurt my hand and have to use my left hand for now...really tired.

Probably its the 'new' layout then. In that case, the setting you are looking for is (probably) "Load BIOS Defaults" 

Edit- under 'smart", though the pic makes that semi-obvious. 

[IMG]http://img195.imageshack.us/img195/5779/n684.jpg[/IMG]


BTW your "8s" turned into that smilie because (this has an added space) "8 )" = 8) 


> **realzippy said:**
> [http://pctechnotes.com/wp-content/uploads/2009/09/remove-battery.jpg](http://pctechnotes.com/wp-content/uploads/2009/09/remove-battery.jpg)

..unplug the battery on the mainboard for a few seconds.This should return to default settings.

EDIT: Sorry-overread this:
*.. not as much as the other option of removing the cmos battery...nonono, i wouldnt want to try that, i would feel like i was attempting brain surgery with no diploma.*


EDIT2:
On the other hand when asking
*Should i be looking in cpu or chipset or somewhere else?*
you should wait with overclocking until you know what you are doing.BTW,Ubuntu (default) "downclocks" your CPU to save power;and generally I see no use in overclocking an ubuntu system;may I ask what you are going to do with that machine?&#960; calculating  ;-)  ?

Removing the BIOS battery is for people who cant find the "Clear CMOS" jumper. Its a dirty way to achive the same thing. 

Who knows if salima is actually overclocking? I've had a &#%%# MSI motherboard that would periodically decide that I was overclocking, pop up with an "overclocking failed, entering BIOS to reset defualts" message..even though I wasnt overclocking. Stupid thing bit the dust a few days ago, time to RMA it. 

As for "see no use in overclocking"- opnion. If you can pull a few more MHz (or even get an extra core or two) from your CPU without hurting it, why not? Sure, its useless IF you have a modern system, and are doing just a bit of web browsing, but if you're doing some heavy stuff (like video encoding) then it can really be worth it. 

I dont see any connection between overclocking and cpufreq anyway. ;)

---

### Post by salima on 2010-09-15
p { margin-bottom: 0.21cm; }  Sorry, i didnt make that clear at all; the pc shuts down , sometimes tries to restart itself, sometimes i have to push the button a dozen times before it will start, sometimes i have to give up and give it a rest til it is good and ready. So i think there is something wrong, maybe the power supply is burned out? It is really hot here all the time and major dust issues. Over 35 celsius six months out of the year.  
 

 Sometimes it starts ok first time. Current here is wild, i have a battery backup surge protector thing, big black box. So i am trying to see what needs to be fixed so i can tell the repairg guy what to replace. Otherwise he will want to take it to the shop and i would like to avoid that.  
 

 Wow my bios doesnt look like that either. I wouuld be more likely to have something way old than newer. What i have on the first page is five main categories; MAIN, ADVANCED, POWER, BOOT and EXIT. Under ADVANCED i have USB CONFIG, CPU CONFIG, CHIPSET, DEVICES CONFIG, PCI PnP. Under POWER i have APM CONFIG, HARDWARE MONITOR. Under BOOT i have BOOT PRIORITY, BOOT SETTINGS, and SECURITY.
 

 Boot settings has a 'restore default option' but i dont see anywhere else.

---

### Post by salima on 2010-09-16
bump

---

### Post by realzippy on 2010-09-17
So which BIOS do you have?
There has to be something about the version/vendor on the first page.It cannot
be so hard to get this information,type it into google,together with the word
"manual" and read this.
Or unplug the ******* CMOS battery;thread solved.

---

### Post by cascade9 on 2010-09-18
> **realzippy said:**
> So which BIOS do you have?
There has to be something about the version/vendor on the first page.It cannot
be so hard to get this information,type it into google,together with the word
"manual" and read this.
Or unplug the ******* CMOS battery;thread solved.

That should work. 

If you've never overclocked your CPU (which I really doubt you have) then  you should NEVER get this message. From my experience, if you get it more than once or twice and you have never overclocked, its a dodgy motherboard.

---

### Post by salima on 2010-09-18
p { margin-bottom: 0.21cm; }   

  [COLOR=#000000]hi-[/COLOR]
  [COLOR=#000000]this has been going on for over a year now, first only sometimes. happens all the time now...called the man, they reset it for me-worked fine when they were here but first thing tonight happened again. Had to push the button 7 times before it took off.[/COLOR]
  

  [COLOR=#000000]I will go back and see what they can do. Let them replace the motherboard, power supply, put in more fans, chipset, whatever...this is definitely something i cant do. I only wish i had been able to pinpoint the problem. [/COLOR] 
  

  [COLOR=#000000]Marking the thread solved.[/COLOR]
  [COLOR=#000000]Thanks all-[/COLOR]

---

