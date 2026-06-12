---
title: "Dual Boot Doesn't Boot"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Pbethe on 2009-06-06
I have this old computer that was running Windows 98.  My goal is to have a dual boot of xubuntu 9.04 and Windows 98.  I went through the steps of the install, then walked away from the computer while it was doing the repartitioning.  When I came back it was unsuccessfully trying to update packages.  I never did see a message indicating that the install was done.  

Now, when I reboot there is no indication that linux has been installed.  I see the old Windows 98 options and a message telling me to use safe mode.  When I try regular mode, it hangs.  In safe mode I can see that my hard drive has been repartitioned.  C: now has 40 Gbytes, just like I wanted.

Now, I have rebooted from the live CD.  This is what I have:

ubuntu                    
    description: Computer
    product: VT82C692BX
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal
  *-core
       description: Motherboard
       product: 693-596-ITE8661
       physical id: 0
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 4.51 PG (06/05/00)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: SLOT 1
          size: 566MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KiB
     *-cache:0
          description: L1 cache
          physical id: a
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: b
          slot: External Cache
          size: 128KiB
          capacity: 2MiB
          capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 384MiB
        *-bank:0
             description: DIMM EDRAM
             physical id: 0
             slot: BANK_0
             size: 128MiB
        *-bank:1
             description: DIMM EDRAM
             physical id: 1
             slot: BANK_1
             size: 128MiB
        *-bank:2
             description: DIMM EDRAM
             physical id: 2
             slot: BANK_2
             size: 128MiB
        *-bank:3
             description: DIMM EDRAM [empty]
             physical id: 3
             slot: BANK_3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 5c
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 bus_master cap_list
                configuration: latency=32 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 23
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
           *-disk
                description: ATA Disk
                product: WDC WD1200JB-00G
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 08.0
                serial: WD-WCALK1219681
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00022c55
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 2d10-09f6
                   size: 40GiB
                   capacity: 40GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 70GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1090MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                capabilities: audio
                configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-network
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth0
             version: 00
             serial: 00:a0:cc:e0:6d:2e
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:07.3
          version: 30
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:da:e3:63:ab:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	95008	94292	100
/dev/sda6                               partition	1116476	93940	-1

I have a clone of the hard disk from before the install.  Should I just start over, or is there a way to get the boot loader working?

---

### Post by Bucky Ball on 2009-06-06
Could you please post the result of:

```
sudo blkid
```... and the file:

```
nano /boot/grub/menu.lst
```

---

### Post by Pbethe on 2009-06-06
Right now I don't have a /boot/grub directory.  I guess I need to mount one of the new partitions.

cd /boot
ubuntu@ubuntu:/boot$ ls
abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin
ubuntu@ubuntu:/boot$ free -m
             total       used       free     shared    buffers     cached
Mem:           371        366          4          0         10         91
-/+ buffers/cache:        265        105
Swap:         1183        315        867
ubuntu@ubuntu:/boot$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="120_GB" UUID="2D10-09F6" TYPE="vfat" 
/dev/sda5: UUID="f5fea9fc-fb3d-4505-972e-24d18738dd11" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="96c101c8-5f22-48c4-85b2-afae1ee3a6a9" TYPE="swap" 
/dev/ramzswap0: TYPE="swap"

---

### Post by philinux on 2009-06-06
Get the super grub disk or usb version and use it to install grub. Looks like the installer fail to do this.

[http://www.supergrubdisk.org/w/index.php5?title=GrubNotInstalled](http://www.supergrubdisk.org/w/index.php5?title=GrubNotInstalled)

---

### Post by Bucky Ball on 2009-06-06
As philinux said, and also, this confuses me:
```

/dev/loop0

and

/dev/ramzswap0: TYPE="swap"
```Not sure what they are. Something odd appears to be happening. Have you a separate swap for Windows?

---

### Post by night_fox on 2009-06-06
Pbethe, firstly do what Philinux said.

Failing that, I think the /boot you looked at might have been on the live cd. Mount the linux filesystem using

> mkdir /media/<WHATEVER>
mount -t ext3 /dev/sda5 /media/<WHATEVER>
cat /media/<WHATEVER>/boot/grub/menu.lst

replace <WHATEVER> with anything you like


Bucky Ball:
/dev/loop0 is where the live cd filesystem image has been mounted. The livecd filesystem is squashfs, a highly compressed, read-only filesystem.

---

### Post by Pbethe on 2009-06-06
> **Bucky Ball said:**
> As philinux said, and also, this confuses me:
```

/dev/loop0

and

/dev/ramzswap0: TYPE="swap"
```Not sure what they are. Something odd appears to be happening. Have you a separate swap for Windows?

When I boot from the CD, it creates a swap in RAMDISK.  I never had understood that one.  I takes some of my memory to make up for the fact that I don't have much memory.  The swap partition, sda6, is what xubuntu created for me.  I started out with one fat32 partition with 120,000,000,000 bytes.

---

### Post by Pbethe on 2009-06-06
> **night_fox said:**
> Pbethe, firstly do what Philinux said.

Failing that, I think the /boot you looked at might have been on the live cd. Mount the linux filesystem using



replace <WHATEVER> with anything you like


Bucky Ball:
/dev/loop0 is where the live cd filesystem image has been mounted. The livecd filesystem is squashfs, a highly compressed, read-only filesystem.

This is what I have now:

ubuntu@ubuntu:/media/sda5/boot$ sudo ls -l
total 5612
-rw-r--r-- 1 root root  529118 2009-04-17 03:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   96795 2009-04-17 03:41 config-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-17 03:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-17 03:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501776 2009-04-17 03:41 vmlinuz-2.6.28-11-generic
ubuntu@ubuntu:/media/sda5/boot$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   190016      2392    187624   2% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   190016      2392    187624   2% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   190016         0    190016   0% /lib/init/rw
varrun                  190016       108    189908   1% /var/run
varlock                 190016         0    190016   0% /var/lock
udev                    190016       148    189868   1% /dev
tmpfs                   190016         0    190016   0% /dev/shm
rootfs                  190016    182096      7920  96% /
/dev/sr0                631804    631804         0 100% /cdrom
/dev/loop0              606720    606720         0 100% /rofs
tmpfs                   190016         8    190008   1% /tmp
/dev/sda5             72959868   1963964  67289712   3% /media/sda5

It looks like I have partitions, but still no grub directory.

---

### Post by night_fox on 2009-06-06
Yeah then you definitely need to reinstall grub. Use this link which Philinux just gave you. [http://www.supergrubdisk.org/w/index.php5?title=GrubNotInstalled](http://www.supergrubdisk.org/w/index.php5?title=GrubNotInstalled)

---

### Post by Pbethe on 2009-06-07
Penguinistas,

Things are looking better.  I rebooted without the CD or any removable media, and it put me into Windows.  Now, I can try Super Grub starting with a working MBR.

Thanks to all,
Paul

---

### Post by Pbethe on 2009-06-14
Phil, or anyone still reading this thread,

I am having trouble figuring out Supe Grub Disk.  To recap, this is what I have in boot of the Ext3 partition of my hard drive:

-rw-r--r-- 1 root root 529118 2009-04-17 03:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root 96795 2009-04-17 03:41 config-2.6.28-11-generic
-rw-r--r-- 1 root root 128796 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-17 03:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root 1074 2009-04-17 03:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501776 2009-04-17 03:41 vmlinuz-2.6.28-11-generic

I have been getting "file not found" errors when I try to boot with the diskette.  I hope there is a way to make this work, because now, neither my BIOS nor Windows 98 can see a CD in my drive.  They know that I have a CD drive but act as if it is always empty.

---

### Post by Pbethe on 2009-06-20
Bump

That Super Grub Disk seems just fine, but I still can't boot.  It appears that the problem is that I do not have a initrd file on my xubuntu partition.  Are there any SGD experts out there?

Oh, when I listen closely, I hear a sound like a woodpecker coming out of my CD drive.  I am hoping that the Super Grub diskette will bail me out of this one. In the mean time I can boot into Windows and try to reistall drivers for the CD, but I doubt that that will help.

---

### Post by Bucky Ball on 2009-06-21
Me either. Sounds like the woodpecker might have got the better of your optical drive; it happens, just like that.

Can you boot from any CD in that drive?

---

### Post by Pbethe on 2009-06-21
> **Bucky Ball said:**
> Me either. Sounds like the woodpecker might have got the better of your optical drive; it happens, just like that.

Can you boot from any CD in that drive?

No, if I boot with a CD in the drive, it tries a good, long time to boot from it but cannot read the CD.  Then it boots into Windows and acts as though the drive is empty.

If I can boot up linux, I can try to mount the drive and read a CD.  If that fails, I'll know that I have a hardware problem.

---

### Post by LewRockwell on 2009-06-21
you're dealing with legacy equipment(older) so you're troubleshooting options are greater as a result

you need a working optical drive so let's try this:

If you have a good drive laying around then put that in
If you have a source of CLEAN DRY AIR then open the drive, keep the drive open while the machine shuts down(you may need to try different sequences, I usually shut down to a prompt and then pull the power cord off the back), take the main cover off the machine, take it outside(or to an area where LOTS of dust can fly freely without upsetting anyone), and get rid of all that dust and debris from all over the machine

Pointers:
I use a vacuum cleaner with the flow reversed through the hose as my dry air blower(note: if you attempt this outside in cold weather then condensation will form on the internal components of the machine and that is bad, if it happens take the machine back inside and blow a fan over it til the condensation evaporates)

Some hair dryers have a "cool" setting that will work in a pinch

Some people use canned air but I don't like paying for air

Some people use electronics contact cleaner(CAN MUST SAY PLASTIC SAFE!) and I use that also for some washing/cleaning situations(WEAR SAFETY GLASSES OR GOOGLES AS IT WILL SPRAY BACK IN YOUR FACE!)

The big issue here is that you optical drive may just have a speck of dust on the "eye"(you might have even seen optical drive cleaning kits in the stores and they usually have a disk with a little soft brush on it for brushing the dust off the "eye")

In any event, if you haven't ever cleaned the insides of your machine(s) then this might be the time to do them all

You can scrub off the blades of the fans and the air inlets and outlets

If you feel up to it you can take the processor cooling fan off and do that area also(here you'll need to be careful and to take note of how the fan is mounted to the heatsink and how the heatsink is retained to the top of the processor)

The nice and easy ones are where the heatsink is retained and the fan is screwed or clipped or fastened somehow to JUST THE HEATSINK, and so when the fan is removed you don't disturb the HEAT TRANSFER PASTE that is between the underside of the heatsink and the top of the processor

ANYTIME THIS PASTE IS DISTURBED IT MUST BE CLEANED OFF AND NEW PASTE USED
(of course, if you've JUST put new paste on then just add a tiny bit more so it maintains a good coating)

here, the technician and the hobbyist will have a tube of this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007)

(old compound/paste MUST be cleaned off and I just spray some contact cleaner on a piece of paper towel and use that to wipe off the heatsink, the processor needs a little more delicate care so I clean them off with Q-tips/cotton swaps sprayed with cleaner)

While you're blowing things out make sure you blow both ways through the power supply(I don't expect the average person to disassemble these but the technician/hobbyist will find it satisfying to do so)

Floppy drives seem to get quite filthy also

whew, that's enough for now

keep us posted

---

### Post by Bucky Ball on 2009-06-22
> **LewRockwell said:**
> you're dealing with legacy equipment(older) so you're troubleshooting options are greater as a result

you need a working optical drive so let's try this:

If you have a good drive laying around then put that in


Good advice. If that one works you know the other is dead and may resurrect by cleaning (though doubtful).

> **LewRockwell said:**
> If you have a source of CLEAN DRY AIR then open the drive, keep the drive open while the machine shuts down(you may need to try different sequences, I usually shut down to a prompt and then pull the power cord off the back),

There is a small hole on the front where you can push a straightened paper clip to release the disc tray. Just shut down and use that.

> **LewRockwell said:**
> take the main cover off the machine, take it outside(or to an area where LOTS of dust can fly freely without upsetting anyone), and get rid of all that dust and debris from all over the machine

Good general advice but see not how this has anything to do with your current problem. Good general tip though.

> **LewRockwell said:**
> Pointers:
I use a vacuum cleaner with the flow reversed through the hose as my dry air blower(note: if you attempt this outside in cold weather then condensation will form on the internal components of the machine and that is bad, if it happens take the machine back inside and blow a fan over it til the condensation evaporates) Some hair dryers have a "cool" setting that will work in a pinch. Some people use canned air but I don't like paying for air

Just DO NOT take the machine outside if there is any chance of condensation. The only air being blown into a machine should be from a can of compressed air, for very good reason. Blowing air of any kind into the box should be avoided unless necessary, canned air or not. There is a good chance of knocking something (especially with the end of a vacuum cleaner hose) without noticing and hard blasts of air can damage components also.

> **LewRockwell said:**
> Some people use electronics contact cleaner(CAN MUST SAY PLASTIC SAFE!) and I use that also for some washing/cleaning situations(WEAR SAFETY GLASSES OR GOOGLES AS IT WILL SPRAY BACK IN YOUR FACE!)

! Washing and cleaning? Are you talking about inside the machine, with liquid blasting hard enough to spray back in your face? No, totally unnecessary procedure.

> **LewRockwell said:**
> In any event, if you haven't ever cleaned the insides of your machine(s) then this might be the time to do them all

You can scrub off the blades of the fans and the air inlets and outlets

! You should blow out your machine with a can or air and that is it. The blades of fans should never be 'scrubbed off' with anything. If you misalign the blades of your CPU fan, you are in serious trouble.

> **LewRockwell said:**
> If you feel up to it you can take the processor cooling fan off and do that area also(here you'll need to be careful and to take note of how the fan is mounted to the heatsink and how the heatsink is retained to the top of the processor)

The nice and easy ones are where the heatsink is retained and the fan is screwed or clipped or fastened somehow to JUST THE HEATSINK, and so when the fan is removed you don't disturb the HEAT TRANSFER PASTE that is between the underside of the heatsink and the top of the processor

ANYTIME THIS PASTE IS DISTURBED IT MUST BE CLEANED OFF AND NEW PASTE USED
(of course, if you've JUST put new paste on then just add a tiny bit more so it maintains a good coating)

here, the technician and the hobbyist will have a tube of this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007](http://www.newegg.com/Product/Product.aspx?Item=N82E16835100007)

(old compound/paste MUST be cleaned off and I just spray some contact cleaner on a piece of paper towel and use that to wipe off the heatsink, the processor needs a little more delicate care so I clean them off with Q-tips/cotton swaps sprayed with cleaner)

While you're blowing things out make sure you blow both ways through the power supply(I don't expect the average person to disassemble these but the technician/hobbyist will find it satisfying to do so)

Please, stick to the point or post a HOWTO: in the tutorials forum. This advice is confusing and potentially dangerous to hardware and humans, especially if the OP has little or no experience of sticking their hands in the box. Very little of this has anything to do with the problem. 

The processor should NEVER be removed unless you have a very old machine and/or you are pretty sure the thermal paste (probably a thermal pad) is dodgy or dead (in which case your processor could be too). I would definitely not advise removing your CPU for cleaning purposes ever! There is nothing to clean. The hose on a can of compressed air gets back there easily. The area where the heatsink meets the processor is totally sealed so it can't get dirty. There is a chance of bending the pins taking the CPU out or back in, *especially *for the novice, cracking the board putting the fan back (all depending on how intricate the fixing mechanism), damaging other parts on the board; it is a job for someone who knows what they're doing or has had the chance to practice on old, dead components (something I always advise when it comes to first time CPU and heatsink installation).

Pbethe, your optical drive sounds like it is dead or more unlikely, dirty as no CD is working in it (and you are sure you have the BIOS set to boot from it). Is your hard drive set to boot second or third in the BIOS? If so it is checking the CD, malfunctioning and thinking there is nothing in there so skipping to the second boot device.

If you have another lying around, can you connect it up and give it a try? If not, a cleaning disk available cheaply and readily might help. If not, replace hardware. :)

---

### Post by Pbethe on 2009-06-22
> **Bucky Ball said:**
> 

Good general advice but see not how this has anything to do with your current problem. Good general tip though.


[stuff deleted]


your optical drive sounds like it is dead or more unlikely, dirty as no CD is working in it (and you are sure you have the BIOS set to boot from it). Is your hard drive set to boot second or third in the BIOS? If so it is checking the CD, malfunctioning and thinking there is nothing in there so skipping to the second boot device.

If you have another lying around, can you connect it up and give it a try? If not, a cleaning disk available cheaply and readily might help. If not, replace hardware. :)

It is **trying** to boot from the CD when I set it to do so.  The hard drive is always the second choice. I had been hoping that a mistake in the BIOS settings was causing the CD problem, but this is looking more and more like a hardware problem.  I have a can of compressed air.  It sounds like a cleaning disk is worth a try.

It could be that the drive was failing when I first tried the install.  I never did figure out what I did wrong.

---

### Post by Bucky Ball on 2009-06-23
The compressed air might help but doubting that. If it still won't boot any cds, you could just about take it as a given that optical drive is dead. Working out how old it is might give a clue there.

They are relatively inexpensive nowadays so a replacement might be called for. If you know of anyone who has an old one or one you could try out, I'd give that a go to make doubly sure. If another drive works fine, you've identified you problem.

And yes, the optical drive malfunctioning halfway through the install is going to give unpredictable results. Try again. :)

---

### Post by Pbethe on 2010-01-16
I can't believe it.  I got a hold of an unused CD drive, new in the box.  After I installed it, it worked fine.  I could boot a Knoppix CD and shut down normally.  I could boot into Windows and read CDs.  Then I booted my Xubuntu CD.  It worked, and I could mount the ext3 partition that I had created.  I logged out of linux, and now, the drive is behaving just like the old one had.  I can put CDs in the drive, and the computer acts as though it is empty.  I can't even boot from a CD.  What next?

---

### Post by Pbethe on 2010-10-27
Maybe I should try a third CD drive, and see what happens.  If I buy one new with a warrenty, I have some protection if it dies, too.  My worry would be compatabillity.  I want something that my BIOS will recognize so that I can try Lubuntu Maverick. I know that I need ATA and not SATA. Is there anything else I need to know? I don't want to get something that will be incompatible was my hardware. Are there any brands that people recommend or advise against?

---

