---
title: "Help with networking/internet"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Yes on 2007-06-16
Ok, I dual boot between Ubuntu and Windows XP.  I get the network/internet on my desktop via Ethernet wire connected to a Linksys router, which gets internet through a RCA Cable Modem.  I had a topic in Absolute Beginner, but they seem to have run out of ideas.  If you want to read through every thing I've done so far, here's the topic: [http://ubuntuforums.org/showthread.php?t=470927&page=1](http://ubuntuforums.org/showthread.php?t=470927&page=1) .  

Here's a summary of the situation:

Static IP the correct IP is assigned, but it won't connect even with a safe DNS.

The driver is the correct one, is dected and loaded.

When DHCP is set (Instead of static), no IP is loaded and it gives an error.


Thanks for taking a look.

---

### Post by arvevans on 2007-06-16
Sorry to hear that you didn't get effective help over in the Absolute Beginner section.

You seem to be knowledgeable in some basic networking so I won't bore you with trivia that you probably already know (ask if you don't understand something).

The Linksys Hub/Router  needs to be set up to act as a DHCP server.  This means that it will select and provide a new local area network (LAN) based IP address when a new computer boots up and requests an IP address.  Your earlier windows "ipconfig" output indicates that this is happening because it is serving the 192.168.0.101 address to the windows PC.  That is a private IP address that gets translated to/from your public network IP address on the TV Cable side of your cable modem.  This is apparently all working OK  because your windows system is able to access the Internet.

The Linux system needs to be configured to automatically request it's own IP address from the Linksys hub/router when it boots up.  

There is the possibility that your network card (the Ethernet interface on the PC) is not being recognized by Ubuntu, or that you installed Ubuntu when the Ethernet network was disconnected and thus it did not install the Ethernet drivers.

I am assuming that you are running a Gnome desktop (not KDE/Kubuntu or X/Xubuntu).  

Click on /System/Administration/Network.  You should see a window that shows "Wired Connection" and possibly "Modem Connection".  The "Wired Connection" option should be checkmarked.  The Modem Connection part should not be checkmarked.  

At the top of this Network Settings window you should see tabs for "Connections", "General", "DNS", and "Hosts".  Click on "Connections"

In the "Connections" window, highlight the "Wired Connection" part by clicking on it.  Now click on "Properties"  In the Properties dialog box you need to set the "Configuration" box for "Automitic configuration (DHCP)", then click on OK.  This should return you to the Network Settings window.

Now click on "General" tab at the top of this window.  This window allows you to set the name that you want outside entities to see as your computer name.  This can be almost anything, as long as it doesn't include spaces or other non-printing characters (I use my ham radio callsign).  You should also make sure that the "Automatic Service Discovery" check box is checked.  This allows your computer to "find" it's way to the Internet and to find any LAN based printers or shared file systems on other local computers.  

Now click on the DNS tab to go to the next configuration screen.  This new window allows you to enter the two DNS server IP addresses that were provided by your Internet Service Provider.  If there are not already  two numerical IP addresses in this space, you will need to add them.  

At this point you are pretty well configured for local IP access.  You can look at the "Hosts" tab, but don't change anything there at this time.

Close out the Network Configuration windows.

Now comes the fun part.  We are going to open up the dreaded "Command Line Interface" to test basic Internet access capability.  Don't panic...it is much the same as the windows command line interface, but with a lot more power and functional capability.

Click on "Applications//Accessories/Terminal".  This should open a text based terminal screen and provide you with a prompt for entering commands.

At the command prompt, enter "ping -c2 127.0.0.1" and hit ENTER.  You should see two pings sent from your computer to it's internal loop around IP address (127.0.0.1).  Below that you should see Ping Response and an indication that 0% packets were lost.  This tells you that the IP communications protocol is running on your computer (hang in there...we have a few more tests to do before we can say that this can talk to the Internet).

At the command prompt, enter "ping -c2 72.14.207.99" and hit ENTER.  Again you should see two ping responses from the indicated IP address, followed by Ping Response lines that indicate 0% packet loss.  This IP address belongs to a Google server, so you have now, hopefully successfully, pinged Google directly by using their IP address instead of using an address translator such as a DNS (Dynamic Name Service) server/translator.  It this works, you know that you do have Internet access using raw IP address capability.

Next, at the command prompt, enter "ping -c2 google.com" and hit ENTER.  You should see the same two pings as above and the same Ping Response indication of 0% packets lost.  This last test tells you that the DNS service is working properly to translate your textual URL into a numerical IP address that the Internet backbone routers can use.

If all this worked for you, then go back to the graphical windows and try accessing Google.com with a browser (Firefox, Epiphany, etc.).  You should be up and working on the Internet.

FYI:  In those "ping -c2 address" commands, the "-c2" option limits the number of pings to just 2.  Without that command option the ping can run on forever (stop it with CTRL-C) instead of automatically just 4 pings as is done by windows command line ping commands.

All of this has been done with the assumption that your system is ready for Internet access and that it has a proper connection to the Internet.  If you find differences at some place in this procedure than you should look around that area to see what the problem might be.  Don't be afraid to get on this forum and ask for help.  Now you know the procedure and can more adequately describe to forum members just what you did, and what went wrong.  From there they should be able to provide the needed assistance.

Good luck,

Arv
_._

---

### Post by facthemighty on 2007-06-16
I've got a "Intel Pro/100 VE Network Connection"  under "network adapters" in the Device Manager of the old dell... 

The newer computer has a "Intel 8256V 10\ Network Connection".  I'll go back to the computer store or go to Best Buy and get a Cat-5 cable or maybe even a router. I'm not sure why since I've only got two computers... well, two computers with network capabillity. 

In the future, I might be gatting broadband by some company callled Cavtel.

---

### Post by Yes on 2007-06-16
Ok, I did all that, but when I tried to ping 72.14.207.99, it said "connect: Network is unreachable" .  I have no idea what to do.  Here's ifconfig, I think you might need it:

```
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:79:CA:0E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xac00 Memory:ff8e0000-ff900000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1620 (1.5 KiB)  TX bytes:1620 (1.5 KiB)
```

Thanks!

---

### Post by kevdog on 2007-06-16
Its fairly obvious that you are not receiving an ip address or making contact with the router through your ifconfig output.

Are you sure all the drivers are installed correctly?

---

### Post by Yes on 2007-06-16
It occasionaly works, so I'm pretty sure they're installed properly.

---

### Post by kevdog on 2007-06-16
I read all 12 pages of your post -- very useful suggestions by others.

Couple of things
#1. Nothing about a driver was mentioned.  You said you thought the driver was correct.  Did you ever install a driver for the card?
Run the command:
lshw
and post the results only of the section pertaining to network controller.

#2. Please post dmesg output

---

### Post by Yes on 2007-06-16
lshw:

```
 *-network
                description: Ethernet interface
                product: 82547EI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 00
                serial: 00:0c:f1:79:ca:0e
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A latency=0 link=no mingnt=255 multicast=yes port=twisted pair
                resources: iomemory:ff8e0000-ff8fffff ioport:ac00-ac1f irq:16
```

dmesg went off the top of the terminal page.  Here's what I could get:

```
1dc00 irq 16
[    5.104172] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 16
[    5.104184] scsi2 : ata_piix
[    5.129280] usb 5-7: new high speed USB device using ehci_hcd and address 4
[    5.266037] usb 5-7: configuration #1 chosen from 1 choice
[    5.266210] hub 5-7:1.0: USB hub found
[    5.266294] hub 5-7:1.0: 2 ports detected
[    5.557241] usb 1-2: USB disconnect, address 2
[    5.557246] usbcore: registered new interface driver hiddev
[    5.557329] usbcore: registered new interface driver libusual
[    5.563549] Initializing USB Mass Storage driver...
[    5.800920] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.984295] usb 1-2: configuration #1 chosen from 1 choice
[    6.228687] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    6.412723] usb 4-2: configuration #1 chosen from 1 choice
[    6.422542] scsi4 : SCSI emulation for USB Mass Storage devices
[    6.422655] usb-storage: device found at 3
[    6.422659] usb-storage: waiting for device to settle before scanning
[    6.434983] input: Logitech Optical USB Mouse as /class/input/input2
[    6.435022] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2
[    6.435113] scsi5 : SCSI emulation for USB Mass Storage devices
[    6.435179] usb-storage: device found at 2
[    6.435182] usb-storage: waiting for device to settle before scanning
[    6.435195] usbcore: registered new interface driver usb-storage
[    6.435200] USB Mass Storage support registered.
[    6.435353] usbcore: registered new interface driver usbhid
[    6.435358] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   11.422141] usb-storage: device scan complete
[   11.435014] usb-storage: device scan complete
[   11.438019] scsi 5:0:0:0: Direct-Access     IOI      MediaBay      CF 0013 PQ: 0 ANSI: 0 CCS
[   11.441009] scsi 5:0:0:1: Direct-Access     IOI      MediaBay      MS 0013 PQ: 0 ANSI: 0 CCS
[   11.444006] scsi 5:0:0:2: Direct-Access     IOI      MediaBay  MMC/SD 0013 PQ: 0 ANSI: 0 CCS
[   11.447004] scsi 5:0:0:3: Direct-Access     IOI      MediaBay      SM 0013 PQ: 0 ANSI: 0 CCS
[   11.457481] scsi 4:0:0:0: Direct-Access     WD       1600BB External  0108 PQ: 0 ANSI: 0
[   11.475562] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   11.476460] sda: Write Protect is off
[   11.476463] sda: Mode Sense: 03 00 00 00
[   11.476465] sda: assuming drive cache: write through
[   11.477329] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   11.478205] sda: Write Protect is off
[   11.478208] sda: Mode Sense: 03 00 00 00
[   11.478209] sda: assuming drive cache: write through
[   11.478212]  sda: sda1 sda2 sda3 sda4
[   11.499964] sd 4:0:0:0: Attached scsi disk sda
[   11.506005] sd 5:0:0:0: Attached scsi removable disk sdb
[   11.510985] sd 5:0:0:1: Attached scsi removable disk sdc
[   11.515987] sd 5:0:0:2: Attached scsi removable disk sdd
[   11.520978] sd 5:0:0:3: Attached scsi removable disk sde
[   11.527752] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[   11.527783] scsi 1:0:1:0: Attached scsi generic sg1 type 5
[   11.527815] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   11.527843] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   11.527871] sd 5:0:0:1: Attached scsi generic sg4 type 0
[   11.527900] sd 5:0:0:2: Attached scsi generic sg5 type 0
[   11.527928] sd 5:0:0:3: Attached scsi generic sg6 type 0
[   11.914921] Attempting manual resume
[   11.914925] swsusp: Resume From Partition 8:2
[   11.914927] PM: Checking swsusp image.
[   11.915646] PM: Resume from disk failed.
[   11.939047] kjournald starting.  Commit interval 5 seconds
[   11.939062] EXT3-fs: mounted filesystem with ordered data mode.
[   22.774489] NET: Registered protocol family 17
[   23.417462] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.458287] input: PC Speaker as /class/input/input3
[   23.518707] iTCO_vendor_support: vendor-support=0
[   23.522060] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   23.523034] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   23.523105] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.580141] intel_rng: Firmware space is locked read-only. If you can't or
[   23.580146] intel_rng: don't want to disable this in firmware setup, and if
[   23.580149] intel_rng: you are certain that your system has a functional
[   23.580150] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   23.602415] Linux agpgart interface v0.102 (c) Dave Jones
[   23.633051] parport: PnPBIOS parport detected.
[   23.633122] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   35.257260] ata3.00: qc timeout (cmd 0x27)
[   35.257267] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 0
[   35.257270] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   35.257273] ata3.00: 488397168 sectors, multi 16: LBA48 
[   35.257281] ata3.00: failed to set xfermode (err_mask=0x40)
[   35.257285] ata3: failed to recover some devices, retrying in 5 secs
[   70.406561] ata3.00: qc timeout (cmd 0x27)
[   70.406568] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 0
[   70.406582] ata3.00: failed to set xfermode (err_mask=0x40)
[   70.406587] ata3.00: limiting speed to UDMA/133:PIO3
[   70.406589] ata3: failed to recover some devices, retrying in 5 secs
[  105.555861] ata3.00: qc timeout (cmd 0x27)
[  105.555868] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 0
[  105.555880] ata3.00: failed to set xfermode (err_mask=0x40)
[  105.555884] ata3.00: disabled
[  106.059583] scsi3 : ata_piix
[  106.226137] ATA: abnormal status 0x7F on port 0x0001e407
[  106.226332] agpgart: Detected an Intel i875 Chipset.
[  106.228717] agpgart: AGP aperture is 64M @ 0xf8000000
[  106.238466] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  106.264811] EDAC MC: Ver: 2.0.1 Apr 15 2007
[  106.304592] EDAC i82875p: i82875p init one
[  106.304666] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[  106.304878] EDAC MC0: Giving out device to i82875p_edac i82875p: DEV 0000:00:00.0
[  106.517406] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[  106.517414] Uniform CD-ROM driver Revision: 3.20
[  106.517807] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  106.525757] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[  106.525869] sr 1:0:1:0: Attached scsi CD-ROM sr1
[  106.781333] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[  106.785343] Installing spdif_bug patch: Audigy 2 [Unknown]
[  106.977849] fuse init (API version 7.8)
[  106.994421] lp0: using parport0 (interrupt-driven).
[  107.048190] Adding 1566328k swap on /dev/disk/by-uuid/13775493-0c0a-4670-87e0-3634ae9c504d.  Priority:-1 extents:1 across:1566328k
[  107.251693] EXT3 FS on sda3, internal journal
[  107.678063] kjournald starting.  Commit interval 5 seconds
[  107.678511] EXT3 FS on sda1, internal journal
[  107.678517] EXT3-fs: mounted filesystem with ordered data mode.
[  107.711143] kjournald starting.  Commit interval 5 seconds
[  107.711861] EXT3 FS on sda4, internal journal
[  107.711868] EXT3-fs: mounted filesystem with ordered data mode.
[  107.765135] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  112.985140] input: Power Button (FF) as /class/input/input4
[  112.985173] ACPI: Power Button (FF) [PWRF]
[  112.985259] input: Sleep Button (CM) as /class/input/input5
[  112.985289] ACPI: Sleep Button (CM) [SLPB]
[  113.123966] No dock devices found.
[  113.169995] ibm_acpi: ec object not found
[  113.231012] Using specific hotkey driver
[  113.395748] pcc_acpi: loading...
[  119.676537] [drm] Initialized drm 1.1.0 20060810
[  119.692527] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  119.692795] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  120.366826] ppdev: user-space parallel port driver
[  121.634555] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  121.634563] apm: disabled - APM is not SMP safe.
[  121.646569] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  121.647377] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  121.647417] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  121.783346] Bluetooth: Core ver 2.11
[  121.783428] NET: Registered protocol family 31
[  121.783432] Bluetooth: HCI device and connection manager initialized
[  121.783438] Bluetooth: HCI socket layer initialized
[  121.802767] Bluetooth: L2CAP ver 2.8
[  121.802773] Bluetooth: L2CAP socket layer initialized
[  121.912185] Bluetooth: RFCOMM socket layer initialized
[  121.912200] Bluetooth: RFCOMM TTY layer initialized
[  121.912204] Bluetooth: RFCOMM ver 1.8
[  137.939822] [drm] Setting GART location based on new memory map
[  137.939834] [drm] Loading R300 Microcode
[  137.939876] [drm] writeback test succeeded in 1 usecs
[ 2811.980026] usb 5-4: new high speed USB device using ehci_hcd and address 6
[ 2812.112908] usb 5-4: configuration #1 chosen from 1 choice
[ 2812.113167] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2812.113421] usb-storage: device found at 6
[ 2812.113425] usb-storage: waiting for device to settle before scanning
[ 2817.113483] usb-storage: device scan complete
[ 2817.113977] scsi 6:0:0:0: Direct-Access     Memorex  TD Classic 003C  6.17 PQ: 0 ANSI: 0 CCS
[ 2817.115460] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 2817.116078] sdf: Write Protect is off
[ 2817.116083] sdf: Mode Sense: 45 00 00 08
[ 2817.116086] sdf: assuming drive cache: write through
[ 2817.117712] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 2817.118327] sdf: Write Protect is off
[ 2817.118332] sdf: Mode Sense: 45 00 00 08
[ 2817.118336] sdf: assuming drive cache: write through
[ 2817.118341]  sdf: sdf1
[ 2817.119500] sd 6:0:0:0: Attached scsi removable disk sdf
[ 2817.119576] sd 6:0:0:0: Attached scsi generic sg7 type 0
[ 2864.632033] usb 5-4: USB disconnect, address 6
[ 5257.966055] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.966065]     Additional sense: Medium not present
[ 5257.966073] end_request: I/O error, dev sr0, sector 0
[ 5257.966077] Buffer I/O error on device sr0, logical block 0
[ 5257.966083] Buffer I/O error on device sr0, logical block 1
[ 5257.966092] Buffer I/O error on device sr0, logical block 2
[ 5257.966097] Buffer I/O error on device sr0, logical block 3
[ 5257.966103] Buffer I/O error on device sr0, logical block 4
[ 5257.966107] Buffer I/O error on device sr0, logical block 5
[ 5257.966113] Buffer I/O error on device sr0, logical block 6
[ 5257.966118] Buffer I/O error on device sr0, logical block 7
[ 5257.970500] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.970507]     Additional sense: Medium not present
[ 5257.970514] end_request: I/O error, dev sr0, sector 0
[ 5257.970518] Buffer I/O error on device sr0, logical block 0
[ 5257.974960] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.974967]     Additional sense: Medium not present
[ 5257.974973] end_request: I/O error, dev sr0, sector 4
[ 5257.974978] Buffer I/O error on device sr0, logical block 1
[ 5257.978680] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.978688]     Additional sense: Medium not present
[ 5257.978694] end_request: I/O error, dev sr0, sector 0
[ 5257.982215] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.982221]     Additional sense: Medium not present
[ 5257.982228] end_request: I/O error, dev sr0, sector 4
[ 5257.985991] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.985998]     Additional sense: Medium not present
[ 5257.986005] end_request: I/O error, dev sr0, sector 0
[ 5257.989672] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.989678]     Additional sense: Medium not present
[ 5257.989685] end_request: I/O error, dev sr0, sector 4
[ 5257.991735] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.991742]     Additional sense: Medium not present
[ 5257.991749] end_request: I/O error, dev sr0, sector 0
[ 5257.993714] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.993720]     Additional sense: Medium not present
[ 5257.993727] end_request: I/O error, dev sr0, sector 4
[ 5257.995799] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.995805]     Additional sense: Medium not present
[ 5257.995812] end_request: I/O error, dev sr0, sector 0
[ 5257.997543] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5257.997549]     Additional sense: Medium not present
[ 5257.997555] end_request: I/O error, dev sr0, sector 4
[ 5258.005175] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.005184]     Additional sense: Medium not present
[ 5258.005192] end_request: I/O error, dev sr1, sector 0
[ 5258.005647] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.005653]     Additional sense: Medium not present
[ 5258.005660] end_request: I/O error, dev sr1, sector 0
[ 5258.006087] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.006093]     Additional sense: Medium not present
[ 5258.006101] end_request: I/O error, dev sr1, sector 4
[ 5258.006534] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.006541]     Additional sense: Medium not present
[ 5258.006547] end_request: I/O error, dev sr1, sector 0
[ 5258.007016] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.007023]     Additional sense: Medium not present
[ 5258.007029] end_request: I/O error, dev sr1, sector 4
[ 5258.007476] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.007482]     Additional sense: Medium not present
[ 5258.007488] end_request: I/O error, dev sr1, sector 0
[ 5258.007917] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.007922]     Additional sense: Medium not present
[ 5258.007928] end_request: I/O error, dev sr1, sector 4
[ 5258.008377] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.008383]     Additional sense: Medium not present
[ 5258.008389] end_request: I/O error, dev sr1, sector 0
[ 5258.008819] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.008825]     Additional sense: Medium not present
[ 5258.008831] end_request: I/O error, dev sr1, sector 4
[ 5258.009280] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.009286]     Additional sense: Medium not present
[ 5258.009292] end_request: I/O error, dev sr1, sector 0
[ 5258.009709] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5258.009714]     Additional sense: Medium not present
[ 5258.009720] end_request: I/O error, dev sr1, sector 4
[ 5281.694765] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.694775]     Additional sense: Medium not present
[ 5281.694783] end_request: I/O error, dev sr0, sector 0
[ 5281.694787] printk: 26 messages suppressed.
[ 5281.694791] Buffer I/O error on device sr0, logical block 0
[ 5281.694798] Buffer I/O error on device sr0, logical block 1
[ 5281.694805] Buffer I/O error on device sr0, logical block 2
[ 5281.694810] Buffer I/O error on device sr0, logical block 3
[ 5281.697530] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.697537]     Additional sense: Medium not present
[ 5281.697543] end_request: I/O error, dev sr0, sector 0
[ 5281.699292] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.699299]     Additional sense: Medium not present
[ 5281.699306] end_request: I/O error, dev sr0, sector 4
[ 5281.701068] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.701075]     Additional sense: Medium not present
[ 5281.701082] end_request: I/O error, dev sr0, sector 0
[ 5281.703032] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.703038]     Additional sense: Medium not present
[ 5281.703045] end_request: I/O error, dev sr0, sector 4
[ 5281.704808] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.704814]     Additional sense: Medium not present
[ 5281.704821] end_request: I/O error, dev sr0, sector 0
[ 5281.706805] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.706811]     Additional sense: Medium not present
[ 5281.706818] end_request: I/O error, dev sr0, sector 4
[ 5281.708596] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.708602]     Additional sense: Medium not present
[ 5281.708609] end_request: I/O error, dev sr0, sector 0
[ 5281.710361] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.710367]     Additional sense: Medium not present
[ 5281.710374] end_request: I/O error, dev sr0, sector 4
[ 5281.712357] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.712363]     Additional sense: Medium not present
[ 5281.712370] end_request: I/O error, dev sr0, sector 0
[ 5281.714107] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.714123]     Additional sense: Medium not present
[ 5281.714130] end_request: I/O error, dev sr0, sector 4
[ 5281.721694] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.721703]     Additional sense: Medium not present
[ 5281.721712] end_request: I/O error, dev sr1, sector 0
[ 5281.722434] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.722442]     Additional sense: Medium not present
[ 5281.722449] end_request: I/O error, dev sr1, sector 0
[ 5281.722861] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.722867]     Additional sense: Medium not present
[ 5281.722873] end_request: I/O error, dev sr1, sector 4
[ 5281.723308] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.723314]     Additional sense: Medium not present
[ 5281.723320] end_request: I/O error, dev sr1, sector 0
[ 5281.723726] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.723732]     Additional sense: Medium not present
[ 5281.723738] end_request: I/O error, dev sr1, sector 4
[ 5281.724156] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.724163]     Additional sense: Medium not present
[ 5281.724169] end_request: I/O error, dev sr1, sector 0
[ 5281.724581] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.724588]     Additional sense: Medium not present
[ 5281.724594] end_request: I/O error, dev sr1, sector 4
[ 5281.725012] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.725018]     Additional sense: Medium not present
[ 5281.725025] end_request: I/O error, dev sr1, sector 0
[ 5281.725437] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.725443]     Additional sense: Medium not present
[ 5281.725450] end_request: I/O error, dev sr1, sector 4
[ 5281.725879] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.725886]     Additional sense: Medium not present
[ 5281.725893] end_request: I/O error, dev sr1, sector 0
[ 5281.726304] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 5281.726311]     Additional sense: Medium not present
[ 5281.726317] end_request: I/O error, dev sr1, sector 4
[ 5301.831422] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[ 5362.786994] usb 5-4: new high speed USB device using ehci_hcd and address 7
[ 5362.919961] usb 5-4: configuration #1 chosen from 1 choice
[ 5362.920217] scsi7 : SCSI emulation for USB Mass Storage devices
[ 5362.920464] usb-storage: device found at 7
[ 5362.920469] usb-storage: waiting for device to settle before scanning
[ 5367.916397] usb-storage: device scan complete
[ 5367.916892] scsi 7:0:0:0: Direct-Access     Memorex  TD Classic 003C  6.17 PQ: 0 ANSI: 0 CCS
[ 5367.918379] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 5367.919001] sdf: Write Protect is off
[ 5367.919007] sdf: Mode Sense: 45 00 00 08
[ 5367.919011] sdf: assuming drive cache: write through
[ 5367.920743] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 5367.921368] sdf: Write Protect is off
[ 5367.921373] sdf: Mode Sense: 45 00 00 08
[ 5367.921376] sdf: assuming drive cache: write through
[ 5367.921381]  sdf:<6>usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5368.276078] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5368.409448]  sdf1
[ 5368.409980] sd 7:0:0:0: Attached scsi removable disk sdf
[ 5368.410051] sd 7:0:0:0: Attached scsi generic sg7 type 0
[ 5368.627890] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5368.871769] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5369.115629] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5369.359501] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5369.603372] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5369.847239] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5370.091109] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5370.223775] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5370.223783] end_request: I/O error, dev sdf, sector 997368
[ 5370.223788] printk: 32 messages suppressed.
[ 5370.223792] Buffer I/O error on device sdf1, logical block 997360
[ 5370.223799] Buffer I/O error on device sdf1, logical block 997361
[ 5370.223805] Buffer I/O error on device sdf1, logical block 997362
[ 5370.223810] Buffer I/O error on device sdf1, logical block 997363
[ 5370.223816] Buffer I/O error on device sdf1, logical block 997364
[ 5370.223821] Buffer I/O error on device sdf1, logical block 997365
[ 5370.223826] Buffer I/O error on device sdf1, logical block 997366
[ 5370.334990] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5370.578855] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5370.822725] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5371.066592] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5371.310462] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5371.554337] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5371.686976] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5371.686983] end_request: I/O error, dev sdf, sector 0
[ 5371.686988] Buffer I/O error on device sdf, logical block 0
[ 5371.686995] Buffer I/O error on device sdf, logical block 1
[ 5371.687001] Buffer I/O error on device sdf, logical block 2
[ 5371.798202] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5372.042069] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5372.285942] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5372.529814] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5372.773680] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5373.017552] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5373.261425] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5373.505296] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5373.749175] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5373.993033] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5374.236904] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5374.369546] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5374.369553] end_request: I/O error, dev sdf, sector 0
[ 5374.480796] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5374.724647] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5374.968511] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5375.212398] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5375.456257] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5375.700123] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5375.944000] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5376.187871] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5376.431737] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5376.565076] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5376.565083] end_request: I/O error, dev sdf, sector 0
[ 5376.565087] printk: 37 messages suppressed.
[ 5376.565092] Buffer I/O error on device sdf, logical block 0
[ 5376.675609] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5376.919480] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5377.167347] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5377.411216] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5377.655089] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5377.898961] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5378.142834] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5378.386696] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5378.519315] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5378.519322] end_request: I/O error, dev sdf, sector 996977
[ 5378.630566] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5378.874442] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5379.118312] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5379.362178] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5379.606051] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5379.849935] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5380.093791] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5380.337666] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5380.581530] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5380.825397] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5381.069268] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5381.313142] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5381.557010] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5381.800883] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5382.044752] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5382.288623] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5382.421251] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5382.421259] end_request: I/O error, dev sdf, sector 496
[ 5382.421264] printk: 14 messages suppressed.
[ 5382.421268] Buffer I/O error on device sdf1, logical block 488
[ 5382.556474] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5382.800347] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5383.044217] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5383.288098] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5383.531959] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5383.775836] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5383.908432] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5383.908439] end_request: I/O error, dev sdf, sector 997128
[ 5384.019699] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5384.263601] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5384.507443] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5384.751316] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5384.995182] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5385.239048] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5385.482918] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5385.726788] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5385.970663] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5386.103239] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5386.103246] end_request: I/O error, dev sdf, sector 997313
[ 5386.103251] printk: 15 messages suppressed.
[ 5386.103255] Buffer I/O error on device sdf1, logical block 997305
[ 5386.214530] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5386.458399] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5386.702270] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5386.946140] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5387.190009] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5387.433884] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5387.677750] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5387.921624] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5388.054191] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5388.054198] end_request: I/O error, dev sdf, sector 9
[ 5388.165491] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5388.409365] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5388.653231] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5388.897102] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5389.140972] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5389.384843] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5389.632713] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5389.896570] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5390.160430] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5390.424294] usb 5-4: reset high speed USB device using ehci_hcd and address 7
[ 5390.568895] sd 7:0:0:0: SCSI error: return code = 0x00070000
[ 5390.568902] end_request: I/O error, dev sdf, sector 0
[ 5390.568907] printk: 13 messages suppressed.
[ 5390.568911] Buffer I/O error on device sdf, logical block 0
[ 5411.665013] usb 5-4: USB disconnect, address 7
[ 5415.179117] usb 5-4: new high speed USB device using ehci_hcd and address 8
[ 5415.312024] usb 5-4: configuration #1 chosen from 1 choice
[ 5415.312269] scsi8 : SCSI emulation for USB Mass Storage devices
[ 5415.312519] usb-storage: device found at 8
[ 5415.312523] usb-storage: waiting for device to settle before scanning
[ 5420.312583] usb-storage: device scan complete
[ 5420.313085] scsi 8:0:0:0: Direct-Access     Memorex  TD Classic 003C  6.17 PQ: 0 ANSI: 0 CCS
[ 5420.314566] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 5420.315188] sdf: Write Protect is off
[ 5420.315193] sdf: Mode Sense: 45 00 00 08
[ 5420.315196] sdf: assuming drive cache: write through
[ 5420.316930] SCSI device sdf: 997375 512-byte hdwr sectors (511 MB)
[ 5420.317555] sdf: Write Protect is off
[ 5420.317560] sdf: Mode Sense: 45 00 00 08
[ 5420.317563] sdf: assuming drive cache: write through
[ 5420.317568]  sdf: sdf1
[ 5420.318729] sd 8:0:0:0: Attached scsi removable disk sdf
[ 5420.318803] sd 8:0:0:0: Attached scsi generic sg7 type 0
```

Thanks!

---

### Post by kevdog on 2007-06-16
Can you  post  lspci 

and 
save cat desmg > out.txt

and then upload the out.txt file.  I need to see the whole log if possible.

---

### Post by kevdog on 2007-06-16
could you also post the following:

modprobe -l | grep e1000

---

### Post by kevdog on 2007-06-16
...and the following:
lsmod | grep e100

---

### Post by Yes on 2007-06-16
Ok, I just rebooted into Ubuntu, and this time I happen to have internet access/network access.  Should I still run all those commands, or should I reboot and then do them (I'm sure that if I rebooted, the access would be gone).

---

### Post by kevdog on 2007-06-17
While you have a connection install ethtool from either Synaptic or using aptitude.

---

### Post by Yes on 2007-06-17
Ok, I did that.  Should I reboot now and run those commands?

---

### Post by kevdog on 2007-06-17
Yes only if its not working!

---

### Post by Yes on 2007-06-17
lsmod | grep e100 :

```
e1000            126016        0
```

modprobe -l | grep e1000 :

```
/lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
```

lspci :

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
03:04.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 03)
```

Attached is the dmesg log.  It was to big to attach as one file, so I spilt it into two.

Thanks!

---

### Post by kevdog on 2007-06-17
Ok here is the part referencing your network controller from dmesg:

[    3.619731] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 16
[    3.619747] PCI: Setting latency timer of device 0000:02:01.0 to 64
[    3.784989] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0c:f1:79:ca:0e
[    4.079877] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

Doesnt seem to be any errors.

Is it not working now again??

---

### Post by kevdog on 2007-06-17
Post output of:

sudo modinfo e1000

---

### Post by Yes on 2007-06-17
No, its not working now.  Here's modinfo:

```
filename:       /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
version:        7.3.15-k2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     037027F24F37E1AAEFC4360
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010B5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001099sv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001079sv*sd*bc*sc*i*
alias:          pci:v00008086d00001078sv*sd*bc*sc*i*
alias:          pci:v00008086d00001077sv*sd*bc*sc*i*
alias:          pci:v00008086d00001076sv*sd*bc*sc*i*
alias:          pci:v00008086d00001075sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d00001028sv*sd*bc*sc*i*
alias:          pci:v00008086d00001027sv*sd*bc*sc*i*
alias:          pci:v00008086d00001026sv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001019sv*sd*bc*sc*i*
alias:          pci:v00008086d00001018sv*sd*bc*sc*i*
alias:          pci:v00008086d00001017sv*sd*bc*sc*i*
alias:          pci:v00008086d00001016sv*sd*bc*sc*i*
alias:          pci:v00008086d00001015sv*sd*bc*sc*i*
alias:          pci:v00008086d00001014sv*sd*bc*sc*i*
alias:          pci:v00008086d00001013sv*sd*bc*sc*i*
alias:          pci:v00008086d00001012sv*sd*bc*sc*i*
alias:          pci:v00008086d00001011sv*sd*bc*sc*i*
alias:          pci:v00008086d00001010sv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Csv*sd*bc*sc*i*
alias:          pci:v00008086d00001009sv*sd*bc*sc*i*
alias:          pci:v00008086d00001008sv*sd*bc*sc*i*
alias:          pci:v00008086d00001004sv*sd*bc*sc*i*
alias:          pci:v00008086d00001001sv*sd*bc*sc*i*
alias:          pci:v00008086d00001000sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           TxDescriptors:Number of transmit descriptors (array of int)
parm:           RxDescriptors:Number of receive descriptors (array of int)
parm:           Speed:Speed setting (array of int)
parm:           Duplex:Duplex setting (array of int)
parm:           AutoNeg:Advertised auto-negotiation setting (array of int)
parm:           FlowControl:Flow Control setting (array of int)
parm:           XsumRX:Disable or enable Receive Checksum offload (array of int)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           eeprom_bad_csum_allow:Allow bad EEPROM checksums (int)
parm:           debug:Debug level (0=none,...,16=all) (int)
```

Thanks.

---

### Post by kevdog on 2007-06-17
I could play around with the ethtool utility to change some of the settings on the card, but I would be guessing at this point.  I think something is probably wrong with the driver -- it doesnt seem like there should be so many aliases, but what do I know.

Not sure what to tell you to do at this point.  I think this is your dads computer.  I might if want to continue working through an ethernet wired connection, go buy a NIC card for $5 and plug it into a pci slot and try that way rather than using the onboard NIC.  If it doesnt work you could always return it.

Sorry Im stumped at this point!

I found the source files for the card, or the e1000 drivers on the intel website.  They have a linux source, but this would mean you would have to compile the drivers and then install it that way.  If you are brave you could always try this approach.

---

### Post by Yes on 2007-06-17
I'll try to get the NIC card, but I'm not sure how soon I could get that.  

I'm perfectly willing to give compiling the drivers a shot, but I would have no idea how to do so.  Will I need a specific program to compile the files, or can I do that straight from the terminal?

Thanks for all your help.

---

### Post by kevdog on 2007-06-17
I think the only package you need to install is the build-essential package -- this allows you to compile.

If you dont have an internet connection on the computer (you do but sporadically) do the following:
if internet connection
sudo aptitude install build-essential

if no internet connection but have ubuntu cd
sudo apt-cd rom add
sudo aptitude update
sudo aptitude install build-essential

Ill see if I can find the page where the sources were.  I did a search under google with your card type, looking for e1000 drivers.

---

### Post by Yes on 2007-06-17
Ok, I did the sudo aptitude install (I had internet connection), everything seemed to be working, but then it gave this error:

```
Err http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-16.28
  404 Not Found
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.28_i386.deb: 404 Not Found
```

Should I try again, or what?

Thanks.

---

### Post by Yes on 2007-06-17
Also, I was wondering if you could "hide" icons on the desktop - Keep them stored in/home/username/Desktop, but not have their icons displayed.  I know this is the wrong place, but, I figured I already had the topic, so...

Thanks.

Edit: Never mind, I figured it out.

---

### Post by Yes on 2007-06-18
Once I manage to install build-essential, if I do manage to do that, what would I do next?  I know I would have to find the soruce files, but what do I do to compile them?

Thanks.

---

### Post by Yes on 2007-06-18
Bump.l

---

### Post by DBStevens on 2007-06-18
kevdog his 

sudo modinfo e1000 

is fine and yes for some reason there is a dump truck load of aliases 


I run with the e1000 driver and have no trouble at all .

From my system:

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller


Yes,

Did you see my last post in the prior thread?

---

### Post by Yes on 2007-06-18
Yeah, I just replied.

---

