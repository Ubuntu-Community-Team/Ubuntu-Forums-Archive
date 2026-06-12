---
title: "Software"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by weezyrider on 2011-02-10
I'm puzzled by one application. I'm trying to install Stellarium, it's listed in Ubuntu software, computer says installed, but it won't run. I got KStars from Ubuntu software, and that installed and will run. 

Now I've seen  some equivalents of programs I was using on Windows. One is Cartes du Ciel, it is now in linux (unix?) I do print my own star charts and this program will. I don't see Opera in the software list, either.

The other would be if I can find a list that will run under Wine. The only lists I have found are for games, not astronomy software.

I don't mind paying for software if I can use it.

I've installed Audacity, Gimp, and cdex - they all run

Weezy

---

### Post by NightwishFan on 2011-02-10
Stellarium requires 3d acceleration, perhaps you do not have a compatible 3d card (or have not enabled 3d support) check in System > Administration > Hardware drivers.

You can download opera for Ubuntu here:
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by oldos2er on 2011-02-10
So what happens if you type **stellarium** in a terminal?

---

### Post by weezyrider on 2011-02-10
I don't have administrator>hardware drivers.
I only have system>additional drivers.
I installed the 64bit version of 10.10
I've had a new video card installed, which should be more capable than the one that went south.
I had Stellarium running on this same drive, but under Win2K. Can you get the older versions like you could for windows?

1.I need a tutorial on installing without using Ubuntu software center. 

2. Need a list and instructions for Wine. All I can find is games. I  want astronomy software like Skymap lite(which I own) - I like to print charts at times.

I need an AV checker of some sort. I download some files for 2 XP machines that have dedicated software and no internet connections. I usually checked downloads thru 2K. 

I'll probably be using this part of the desktop more as Ubuntu books faster than W2K did.

And what's a terminal? I think I saw something like that while I was snooping around in Ubuntu, but I can't remember where I saw it. 
Thanks

---

### Post by SEisch on 2011-02-10
> **weezyrider said:**
> 

And what's a terminal? I think I saw something like that while I was snooping around in Ubuntu, but I can't remember where I saw it. 
Thanks

The terminal is used for typing commands for programs, files, etc.  It is located in Applications>Accessories>Terminal.

---

### Post by SEisch on 2011-02-10
What comes up when you look up System>Administration>Additional Drivers?  Does it list any proprietary drivers for your 3D graphics card?  Stellarium works on 10.10 for me with a proprietary driver.

---

### Post by oldos2er on 2011-02-10
Installing software: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.wikihow.com/Install-Software-in-Ubuntu](http://www.wikihow.com/Install-Software-in-Ubuntu)

Wine: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by weezyrider on 2011-02-10
> **SEisch said:**
> What comes up when you look up System>Administration>Additional Drivers?  Does it list any proprietary drivers for your 3D graphics card?  Stellarium works on 10.10 for me with a proprietary driver.

It says no new drivers found. Absolutely blank. W

---

### Post by weezyrider on 2011-02-10
> **SEisch said:**
> What comes up when you look up System>Administration>Additional Drivers?  Does it list any proprietary drivers for your 3D graphics card?  Stellarium works on 10.10 for me with a proprietary driver.

Apparently, the built in card was bypassed by installing a new card in a pci slot and set up as the main card.  Just checked. Card is working just fine in XP. Computer is dual boot, and XP is only used for Adobe and the internet connection is disabled. W

---

### Post by SEisch on 2011-02-11
If nothing comes up under Additional Drivers, you might want to try going to System>Administration>Synaptic Package Manager.  In the search box type in the brand name of your card and see if anything pops up.  
That's the only other idea I have.

---

### Post by weezyrider on 2011-02-13
Exactly what is Launchpad? It mentions something about setting up new account. Does it spam or track you?

How do you update that software selection box? I'd think there would be new software added, and I don't see a link to update it.

About Stellarium. The download from software still won't run. I did some snooping and found an info type file. It had a blurb about finding the right distro. Since the software center downloaded it, I never saw Stellarium's website. The one I tried to download independently said that I didn't have permission to run the child object. And I couldn't find the system requirements anyway. I  CAN find the requirements for windows.

If Ubuntu is going to fight everything I want - which is more informational stuff like star charting software, etc and just give me the social crap like facebook and twitter, I just might reinstall 2K. I don't have to do "mother may I" with Windows! Especially not when the program is reputable! I don't download indiscriminately.

---

### Post by corncob on 2011-02-13
Launchpad is a developer's website.  Being just a user I rarely go there myself.

Here's the Stellarium website:
[http://www.stellarium.org/](http://www.stellarium.org/)
and if you somehow still can't get there, here's a direct link to the user's guide (PDF):
[http://sourceforge.net/projects/stellarium/files/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf/download](http://sourceforge.net/projects/stellarium/files/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf/download)

---

### Post by oldsoundguy on 2011-02-13
Launchpad is where you file bug reports and check to see if there are work arounds.

A bit on the convoluted side, but that keeps the bogus posts/bug reports from the MS Fanbuoys at a minimum.

---

### Post by oldos2er on 2011-02-13
Run ```
sudo apt-get update
``` to update your software sources.

Still waiting for you to answer the question I asked you about Stellarium in the 'Software' thread.

---

### Post by ikt on 2011-02-13
> **weezyrider said:**
> I just might reinstall 2K. I don't have to do "mother may I" with Windows! Especially not when the program is reputable! I don't download indiscriminately.

heh

windows 2k

---

### Post by daggerstab on 2011-02-14
> **weezyrider said:**
> I'm puzzled by one application. I'm trying to install Stellarium, it's listed in Ubuntu software, computer says installed, but it won't run.

Stellarium has problems with some graphics card drivers. Try opening a terminal and running:
```
stellarium --safe-mode
```

If this works, you can modify the icon in the Applications menu as described here:
[http://ubuntuforums.org/showthread.php?t=1631931](http://ubuntuforums.org/showthread.php?t=1631931)

If it doesn't work, please look in Stellarium's log file for a possible error. The file is called "log.txt" and it is located in the hidden ".stellarium" directory in your home directory.

> **weezyrider said:**
> One is Cartes du Ciel, it is now in linux (unix?) I do print my own star charts and this program will.

You can download .deb packages for Ubuntu from Cartes du Ciel/Skychart's website: [http://www.ap-i.net/skychart/en/download](http://www.ap-i.net/skychart/en/download)

Look for "Linux Deb" and choose the link that matches your system's architecture (32-bit or 64-bit). After you download the package, double-click the file to open the GDebi package manager. The additional star catalogues are downloaded and installed in a similar way.

> **weezyrider said:**
> The other would be if I can find a list that will run under Wine. The only lists I have found are for games, not astronomy software.

In theory, Wine should be able to run anything that runs on Windows. In practice, it's still a work-in-progress. They maintain a database of (in)compatible software on their website:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Paqman on 2011-02-14
> **weezyrider said:**
> 
About Stellarium. The download from software still won't run.

If you want help with sorting this out, feel free to start a thread about it and we'll do our best. The first thing you'll probably be asked to do is open a terminal and launch it by typing:
```
stellarium
```
...and posting the errors it spits out. But since this thread is about Launchpad it'd be best to do it all in a separate thread about Stellarium.

---

### Post by daggerstab on 2011-02-14
**weezyrider**, [I have replied](http://ubuntuforums.org/showthread.php?t=1685407&page=2#11) in your other thread, you may want to read it.

---

### Post by grahammechanical on 2011-02-14
> I just might reinstall 2K. I don't have to do "mother may I" with  Windows! Especially not when the program is reputable! I don't download  indiscriminately.

This is why all the computers sending out spam without their owners knowing it are computers using Microsoft Windows operating Systems.

Regards and good luck with getting help from Microsoft.

---

### Post by weezyrider on 2011-02-15
What does DMI table is broken mean?

---

### Post by weezyrider on 2011-02-15
I tried messing with Stellarium via instructions in last post. I get the DMI-table-is-broken. I bought a book on Ubuntu, and my login looks nothing like the normal one. I skipped of personal info when I set up the account, so instead of desktop it shows computer name. I never put personal information in anywhere if I can help it, and I figured it was none of Ubuntu's business.  The computer is custom/2 separate hd/booted into by bios. Ubuntu is on it's own drive. I looked up the information and it was all dated 2009. Is it still accurate? How do I edit that error? Thanks

---

### Post by lisati on 2011-02-15
Threads merged: it can get confusing if you start a new thread on a question that someone has already given an answer to in another thread.

---

### Post by weezyrider on 2011-02-15
> **daggerstab said:**
> **weezyrider**, [I have replied]("http://ubuntuforums.org/showthread.php?t=1685407&page=2#11") in your other thread, you may want to read it.
I can't find the post. 
Here's the thing form stellarium
stellarium
Using default graphics system specified at build time:  raster 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/weezy/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/weezy/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/weezy/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL" 
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
Then It adds that table broken

---

### Post by weezyrider on 2011-02-15
here's dmesg:

```
dmesg:
[    0.526752] pci 0000:02:00.0: BAR 6: assigned [mem 0xfda00000-0xfda1ffff pref]
[    0.526755] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.526758] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.526761] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.526765] pci 0000:00:04.0:   bridge window [mem 0xe8000000-0xefffffff 64bit pref]
[    0.526770] pci 0000:03:06.0: BAR 6: assigned [mem 0xfdc00000-0xfdc03fff pref]
[    0.526773] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.526776] pci 0000:00:10.0:   bridge window [io  0x9000-0xafff]
[    0.526780] pci 0000:00:10.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.526783] pci 0000:00:10.0:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.526795] pci 0000:00:03.0: setting latency timer to 64
[    0.526801] pci 0000:00:04.0: setting latency timer to 64
[    0.526806] pci 0000:00:10.0: setting latency timer to 64
[    0.526810] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.526813] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.526815] pci_bus 0000:00: resource 6 [mem 0xa0000000-0xf3ffffff]
[    0.526818] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.526821] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.526823] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.526826] pci_bus 0000:01: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.526829] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.526831] pci_bus 0000:02: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.526834] pci_bus 0000:02: resource 2 [mem 0xe8000000-0xefffffff 64bit pref]
[    0.526837] pci_bus 0000:03: resource 0 [io  0x9000-0xafff]
[    0.526840] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.526842] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.526845] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.526847] pci_bus 0000:03: resource 5 [mem 0x000a0000-0x000bffff]
[    0.526850] pci_bus 0000:03: resource 6 [mem 0xa0000000-0xf3ffffff]
[    0.526853] pci_bus 0000:03: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.526898] NET: Registered protocol family 2
[    0.527108] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.529297] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.529985] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.530450] TCP: Hash tables configured (established 524288 bind 65536)
[    0.530453] TCP reno registered
[    0.530470] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.530537] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.530715] NET: Registered protocol family 1
[    0.530779] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.530802] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.552595] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.552603] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.552657] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.552662] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.552691] pci 0000:02:00.0: Boot video device
[    0.552702] PCI: CLS 64 bytes, default 64
[    0.593641] Scanning for low memory corruption every 60 seconds
[    0.593815] audit: initializing netlink socket (disabled)
[    0.593839] type=2000 audit(1297764891.589:1): initialized
[    0.608718] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.610525] VFS: Disk quotas dquot_6.5.2
[    0.610594] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.611303] fuse init (API version 7.14)
[    0.611400] msgmni has been set to 4998
[    0.612421] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.612425] io scheduler noop registered
[    0.612427] io scheduler deadline registered
[    0.612469] io scheduler cfq registered (default)
[    0.612663] pcieport 0000:00:03.0: setting latency timer to 64
[    0.612683]   alloc irq_desc for 40 on node 0
[    0.612685]   alloc kstat_irqs on node 0
[    0.612696] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.612788] pcieport 0000:00:04.0: setting latency timer to 64
[    0.612803]   alloc irq_desc for 41 on node 0
[    0.612804]   alloc kstat_irqs on node 0
[    0.612810] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.612883] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.612909] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.613110] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.613117] ACPI: Power Button [PWRB]
[    0.613180] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.613184] ACPI: Power Button [PWRF]
[    0.613258] ACPI: Fan [FAN] (on)
[    0.613695] ACPI: acpi_idle registered with cpuidle
[    0.618920] thermal LNXTHERM:01: registered as thermal_zone0
[    0.618928] ACPI: Thermal Zone [THRM] (40 C)
[    0.618988] ERST: Table is not found!
[    0.619172] Linux agpgart interface v0.103
[    0.619177] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.619298] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.619400] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.619689] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.619828] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.621160] brd: module loaded
[    0.621744] loop: module loaded
[    0.622169] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.622664] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.622670]   alloc irq_desc for 23 on node 0
[    0.622672]   alloc kstat_irqs on node 0
[    0.622685] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.622716] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.622724] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.623166] Fixed MDIO Bus: probed
[    0.623202] PPP generic driver version 2.4.2
[    0.623252] tun: Universal TUN/TAP device driver, 1.6
[    0.623254] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.623359] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.623757] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.623761]   alloc irq_desc for 22 on node 0
[    0.623762]   alloc kstat_irqs on node 0
[    0.623772] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.623798] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.623802] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.623849] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.623884] ehci_hcd 0000:00:0b.1: debug port 1
[    0.623893] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.623920] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    0.640024] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.640161] hub 1-0:1.0: USB hub found
[    0.640167] hub 1-0:1.0: 8 ports detected
[    0.640277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.640680] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.640683]   alloc irq_desc for 21 on node 0
[    0.640685]   alloc kstat_irqs on node 0
[    0.640694] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.640708] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.640711] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.640762] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.640799] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xfe02f000
[    0.646427] Freeing initrd memory: 10744k freed
[    0.702147] hub 2-0:1.0: USB hub found
[    0.702153] hub 2-0:1.0: 8 ports detected
[    0.702296] uhci_hcd: USB Universal Host Controller Interface driver
[    0.702453] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.702456] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.702634] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.702755] mice: PS/2 mouse device common for all mice
[    0.702879] rtc_cmos 00:04: RTC can wake from S4
[    0.702927] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.702961] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.703075] device-mapper: uevent: version 1.0.3
[    0.703221] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.703385] device-mapper: multipath: version 1.1.1 loaded
[    0.703389] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.703695] cpuidle: using governor ladder
[    0.703697] cpuidle: using governor menu
[    0.704121] TCP cubic registered
[    0.704272] NET: Registered protocol family 10
[    0.704709] lo: Disabled Privacy Extensions
[    0.704964] NET: Registered protocol family 17
[    0.705008] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (2 cpu cores) (version 2.20.00)
[    0.705064] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[    0.705067] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[    0.705069] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    0.705216] PM: Resume from disk failed.
[    0.705230] registered taskstats version 1
[    0.705529]   Magic number: 15:328:224
[    0.705661] rtc_cmos 00:04: setting system clock to 2011-02-15 10:14:52 UTC (1297764892)
[    0.705664] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.705666] EDD information not available.
[    0.705755] Freeing unused kernel memory: 908k freed
[    0.706269] Write protecting the kernel read-only data: 10240k
[    0.706464] Freeing unused kernel memory: 412k freed
[    0.706883] Freeing unused kernel memory: 1644k freed
[    0.723104] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.731286] udev[111]: starting version 163
[    0.868663] Floppy drive(s): fd0 is 1.44M
[    0.896475] FDC 0 is a post-1991 82077
[    0.900380] pata_amd 0000:00:0d.0: version 0.4.1
[    0.900446] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.902772] scsi0 : pata_amd
[    0.903004] pata_pdc2027x 0000:03:06.0: version 1.0
[    0.903480] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    0.903486]   alloc irq_desc for 16 on node 0
[    0.903489]   alloc kstat_irqs on node 0
[    0.903503] pata_pdc2027x 0000:03:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    0.960035] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.003560] pata_pdc2027x 0000:03:06.0: PLL input clock 16729 kHz
[    1.033570] pata_pdc2027x 0000:03:06.0: setting latency timer to 64
[    1.033587] scsi1 : pata_amd
[    1.034590] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    1.034593] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    1.034863] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.035240] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.035244]   alloc irq_desc for 20 on node 0
[    1.035246]   alloc kstat_irqs on node 0
[    1.035256] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.035261] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.035316] nv_probe: set workaround bit for reversed mac addr
[    1.035712] scsi2 : pata_pdc2027x
[    1.035847] scsi3 : pata_pdc2027x
[    1.035894] ata3: PATA max UDMA/100 mmio m16384@0xfddf8000 cmd 0xfddf97c0 irq 16
[    1.035897] ata4: PATA max UDMA/100 mmio m16384@0xfddf8000 cmd 0xfddf95c0 irq 16
[    1.114697] hub 1-3:1.0: USB hub found
[    1.114964] hub 1-3:1.0: 4 ports detected
[    1.202223] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    1.202227] ata1.00: 160086528 sectors, multi 16: LBA 
[    1.202253] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc700c5c5) ACPI=0x7f01f (15:600:0x13)
[    1.240443] ata1.00: configured for UDMA/133
[    1.240627] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    1.240856] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.241051] sd 0:0:0:0: [sda] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    1.241104] sd 0:0:0:0: [sda] Write Protect is off
[    1.241107] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.241131] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.241350]  sda: sda1 sda2 < sda5 >
[    1.265779] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.391221] usb 1-3.1: new low speed USB device using ehci_hcd and address 3
[    1.560832] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:19:21:47:11:c3
[    1.560838] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.560932] sata_nv 0000:00:0e.0: version 3.5
[    1.560950] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.560953] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.561018] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.561185] scsi4 : sata_nv
[    1.561296] scsi5 : sata_nv
[    1.561547] ata5: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    1.561551] ata6: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    1.583230] usb 1-3.2: new high speed USB device using ehci_hcd and address 4
[    1.620327] ata2.00: ATAPI: SONY    DVD-ROM DDU1615, GYS4, max UDMA/66
[    1.620360] ata2.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P53, max UDMA/66
[    1.620385] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc700c5c5) ACPI=0x1f01f (30:30:0x1f)
[    1.620390] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc700c5c5) ACPI=0x1f01f (30:30:0x1f)
[    1.660273] ata2.00: configured for UDMA/66
[    1.700275] ata2.01: configured for UDMA/66
[    1.701869] scsi 1:0:0:0: CD-ROM            SONY     DVD-ROM DDU1615  GYS4 PQ: 0 ANSI: 5
[    1.703907] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    1.703911] Uniform CD-ROM driver Revision: 3.20
[    1.704065] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.704142] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.705280] scsi 1:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P53 PQ: 0 ANSI: 5
[    1.710301] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.710452] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.710532] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.718245] Initializing USB Mass Storage driver...
[    1.718465] scsi6 : usb-storage 1-3.2:1.0
[    1.718580] usbcore: registered new interface driver usb-storage
[    1.718583] USB Mass Storage support registered.
[    1.793228] usb 1-3.3: new high speed USB device using ehci_hcd and address 5
[    1.914660] hub 1-3.3:1.0: USB hub found
[    1.914975] hub 1-3.3:1.0: 4 ports detected
[    2.040061] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.099021] ata5.00: ATA-7: ST380815AS, 3.AAC, max UDMA/133
[    2.099025] ata5.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.182329] ata5.00: configured for UDMA/133
[    2.182504] scsi 4:0:0:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[    2.182694] sd 4:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.182719] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.182753] sd 4:0:0:0: [sdb] Write Protect is off
[    2.182756] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.182897] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.183131]  sdb:
[    2.193236] usb 1-3.3.2: new full speed USB device using ehci_hcd and address 6
[    2.230347]  sdb1
[    2.230653] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.318798] usbcore: registered new interface driver hiddev
[    2.321738] input: HID 1267:c002 as /devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3.1/1-3.1:1.0/input/input3
[    2.321858] generic-usb 0003:1267:C002.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1267:c002] on usb-0000:00:0b.1-3.1/input0
[    2.321916] usbcore: registered new interface driver usbhid
[    2.321918] usbhid: USB HID core driver
[    2.510031] ata6: SATA link down (SStatus 0 SControl 300)
[    2.722385] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0128 PQ: 0 ANSI: 0
[    2.723494] scsi 6:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0128 PQ: 0 ANSI: 0
[    2.724495] scsi 6:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0128 PQ: 0 ANSI: 0
[    2.725496] scsi 6:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0128 PQ: 0 ANSI: 0
[    2.726262] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    2.727475] sd 6:0:0:1: Attached scsi generic sg5 type 0
[    2.728230] sd 6:0:0:2: Attached scsi generic sg6 type 0
[    2.729732] sd 6:0:0:3: Attached scsi generic sg7 type 0
[    2.734658] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    2.738389] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    2.740253] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    2.742002] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    2.866563] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.716792] udev[472]: starting version 163
[   13.769690] Adding 3303420k swap on /dev/sda5.  Priority:-1 extents:1 across:3303420k 
[   13.833606] lp: driver loaded but no devices found
[   13.868036] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.868091] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   13.938697] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   13.969376] parport_pc 00:0a: reported by Plug and Play ACPI
[   13.969467] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.974843] EDAC MC: Ver: 2.1.0 Jan 21 2011
[   13.988395] type=1400 audit(1297790105.774:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=642 comm="apparmor_parser"
[   13.988711] type=1400 audit(1297790105.774:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   13.988883] type=1400 audit(1297790105.774:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   14.032052] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.071453] parport0: Printer, Hewlett-Packard hp LaserJet 1300
[   14.180620] EDAC amd64_edac:  Ver: 3.3.0 Jan 21 2011
[   14.180735] lp0: using parport0 (interrupt-driven).
[   14.192610] input: Wacom Bamboo as /devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3.3/1-3.3.2/1-3.3.2:1.0/input/input4
[   14.193064] [drm] Initialized drm 1.1.0 20060810
[   14.212219] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   14.212230] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.212231]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.212233]  (Note that use of the override may cause unknown side effects.)
[   14.212251] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   14.232610] usbcore: registered new interface driver wacom
[   14.232615] wacom: v1.52:USB Wacom tablet driver
[   14.234655] ppdev: user-space parallel port driver
[   14.404705] [drm] radeon defaulting to kernel modesetting.
[   14.404709] [drm] radeon kernel modesetting enabled.
[   14.420625] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   14.420634] radeon 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   14.420639] radeon 0000:02:00.0: setting latency timer to 64
[   14.424950] [drm] initializing kernel modesetting (RV380 0x1002:0x5B63).
[   14.429949] [drm] register mmio base: 0xFDAF0000
[   14.429953] [drm] register mmio size: 65536
[   14.430327] [drm] Generation 2 PCI interface, using max accessible memory
[   14.430333] radeon 0000:02:00.0: VRAM: 128M 0xE8000000 - 0xEFFFFFFF (128M used)
[   14.430336] radeon 0000:02:00.0: GTT: 512M 0xC8000000 - 0xE7FFFFFF
[   14.430383]   alloc irq_desc for 42 on node 0
[   14.430386]   alloc kstat_irqs on node 0
[   14.430398] radeon 0000:02:00.0: irq 42 for MSI/MSI-X
[   14.430403] radeon 0000:02:00.0: radeon: using MSI.
[   14.430437] [drm] radeon: irq initialized.
[   14.430773] [drm] Detected VRAM RAM=128M, BAR=128M
[   14.430779] [drm] RAM width 128bits DDR
[   14.449885] [TTM] Zone  kernel: Available graphics memory: 1286586 kiB.
[   14.449890] [TTM] Initializing pool allocator.
[   14.449925] [drm] radeon: 128M of VRAM memory ready
[   14.449927] [drm] radeon: 512M of GTT memory ready.
[   14.449968] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.452688] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   14.453853] [drm] PCIE GART of 512M enabled (table at 0xE8040000).
[   14.454241] [drm] Loading R300 Microcode
[   14.463605] [drm] radeon: ring at 0x00000000C8000000
[   14.463630] [drm] ring test succeeded in 1 usecs
[   14.463848] [drm] radeon: ib pool ready.
[   14.463949] [drm] ib test succeeded in 0 usecs
[   14.464097] [drm] Default TV standard: PAL
[   14.464099] [drm] 27.000000000 MHz TV ref clk
[   14.464103] [drm] DFP table revision: 4
[   14.464167] [drm] Default TV standard: PAL
[   14.464168] [drm] 27.000000000 MHz TV ref clk
[   14.464204] [drm] Radeon Display Connectors
[   14.464206] [drm] Connector 0:
[   14.464207] [drm]   VGA
[   14.464210] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   14.464212] [drm]   Encoders:
[   14.464214] [drm]     CRT1: INTERNAL_DAC1
[   14.464215] [drm] Connector 1:
[   14.464217] [drm]   DVI-I
[   14.464218] [drm]   HPD1
[   14.464220] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   14.464222] [drm]   Encoders:
[   14.464224] [drm]     CRT2: INTERNAL_DAC2
[   14.464226] [drm]     DFP1: INTERNAL_TMDS1
[   14.464227] [drm] Connector 2:
[   14.464229] [drm]   S-video
[   14.464230] [drm]   Encoders:
[   14.464231] [drm]     TV1: INTERNAL_DAC2
[   14.521585] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   14.521594] Intel ICH 0000:00:10.2: PCI INT C -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[   14.521629] Intel ICH 0000:00:10.2: setting latency timer to 64
[   14.641266] type=1400 audit(1297790106.424:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1042 comm="apparmor_parser"
[   14.641577] type=1400 audit(1297790106.424:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1042 comm="apparmor_parser"
[   14.641755] type=1400 audit(1297790106.424:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1042 comm="apparmor_parser"
[   14.648394] type=1400 audit(1297790106.434:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1041 comm="apparmor_parser"
[   14.671102] type=1400 audit(1297790106.454:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1048 comm="apparmor_parser"
[   14.671502] type=1400 audit(1297790106.454:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1048 comm="apparmor_parser"
[   14.674477] type=1400 audit(1297790106.464:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1043 comm="apparmor_parser"
[   14.733547] [drm] fb mappable at 0xE80C0000
[   14.733551] [drm] vram apper at 0xE8000000
[   14.733553] [drm] size 5242880
[   14.733555] [drm] fb depth is 24
[   14.733557] [drm]    pitch is 5120
[   14.792104] Console: switching to colour frame buffer device 160x64
[   14.798683] fb0: radeondrmfb frame buffer device
[   14.798685] drm: registered panic notifier
[   14.798692] Slow work thread pool: Starting up
[   14.798783] Slow work thread pool: Ready
[   14.798792] [drm] Initialized radeon 2.5.0 20080528 for 0000:02:00.0 on minor 0
[   14.870304] intel8x0_measure_ac97_clock: measured 60608 usecs (2968 samples)
[   14.870309] intel8x0: clocking to 47049
[   16.143358] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.429179] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.410015] eth0: no IPv6 routers present
[   29.740604] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[   29.740611] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[   29.740614] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   29.744031] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[   29.744037] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[   29.744040] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   33.207348] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[   33.207355] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[   33.207358] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   77.340026] Clocksource tsc unstable (delta = -256314904 ns)
[  204.276309] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  204.276309] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  204.276309] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  210.904285] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  210.904292] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  210.904295] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  216.537727] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  216.537734] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  216.537738] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  222.674990] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  222.674997] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  222.675001] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  328.022287] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  328.022299] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  328.022304] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  367.517368] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  367.517374] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  367.517377] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  374.475108] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[  374.475116] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[  374.475119] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 3579.565853] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:0b.1-3.1/input0, status -71
[ 3579.590213] hub 1-3:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 3579.590581] usb 1-3.1: USB disconnect, address 3
[ 3579.605848] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:0b.1-3.1/input0, status -71
[ 3579.882990] usb 1-3.1: new low speed USB device using ehci_hcd and address 7
[ 3579.999514] input: HID 1267:c002 as /devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3.1/1-3.1:1.0/input/input5
[ 3579.999937] generic-usb 0003:1267:C002.0002: input,hidraw0: USB HID v1.10 Mouse [HID 1267:c002] on usb-0000:00:0b.1-3.1/input0
[ 4577.444590] [drm:r100_cs_track_check] *ERROR* [drm] Buffer too small for color buffer 0 (need 393216 have 16384) !
[ 4577.444597] [drm:r100_cs_track_check] *ERROR* [drm] color buffer 0 (128 4 0 76
[ 4577.444599] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
```

---

### Post by oldos2er on 2011-02-15
You might want to try v0.10.6 from this PPA: [https://launchpad.net/~stellarium/+archive/stellarium-releases](https://launchpad.net/~stellarium/+archive/stellarium-releases)

I found a couple bug reports on "drmRadeonCmdBuffer":

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/481669)

[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/658975](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/658975)

---

### Post by lisati on 2011-02-15
> **weezyrider said:**
> I can't find the post. 


Click on the link: it's there.

---

### Post by weezyrider on 2011-02-15
> **lisati said:**
> Click on the link: it's there.


I'll give that link a try tomorrow. Now how do I fix that table error or is that just the way I entered or did not enter something. It says weezy@then computer name which is not quite kosher. It's a form of s***h****, then DMI, then table broken.[INDENT]I did get Adobe reader to run, Inkscape runs, printer works but is slower than molasses in January when printing from Inkscape or Reader. Print from Office is immediate. Scanner is slow but does work eventually.  Photoshop CS3 is running quite happily on this setup on the XP drive. I had the computer built around it. So there should be plenty of Ram.  
Thanks 
[/INDENT]

---

### Post by daggerstab on 2011-02-16
**weezyrider**,

This error message is bad news:
> drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

It means that the crash is caused by your graphics card's driver. You have an ATI Radeon, right?

As far as I know, it has been fixed in the latest kernel/driver, so you can:

[LIST]
[*]wait and see if a fix is released for the current version of Ubuntu;
[*]wait two months for Ubuntu 11.04 Natty Narwhal to be released in the end of April;
[*]try to install the new OpenGL library and mainline kernel from a PPA (personal package archive). For that, someone more Ubuntu-savvy should help you (a working method is mentioned in the comments **[here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557266")**)
[/LIST]

You can still install Cartes du Ciel/Starchart, though.

---

### Post by alphacrucis2 on 2011-02-16
I can't help the OP with Stellarium but Cartes Du Ciel should work fine (it doesn't require graphics accelleration). The Linux version can be downloaded here:

[http://www.ap-i.net/skychart/en/development_version]("http://www.ap-i.net/skychart/en/development_version")

Download the appropriate deb file (32 or 64 bit)

If you want the so called stable version, the deb can be downloaded here:

[http://www.ap-i.net/skychart/en/download]("http://www.ap-i.net/skychart/en/download")


I actually prefer the development version as it is considerably improved over the "stable" version.

---

### Post by weezyrider on 2011-02-16
The computer is not crashing. It just won't start/run/execute Stellarium. Nothing happens. Something does flash on the bottom task bar, but too fast for me to catch it.  I didn't understand those errors, but I didn't like the looks of them.
I think I'll print out that error list and take it to the tech.  Will also find out what card he put in. Like I said, the original card on the motherboard was going. Tech installed new video card in PCI slot.
I think the original was a Radeon, I'll have to find out what the new card is. 
I really want this to work. Trouble is, I'm just not hardware oriented.

---

### Post by weezyrider on 2011-02-16
The ATI Radeon is the card in the PC! slot. It was used, so the drivers could be out of date. 
How do you update drivers?

---

### Post by daggerstab on 2011-02-18
A user who had reported the same error message like you has reported that the problem is fixed by updating from these two PPAs:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

It's possible that only the first may be sufficient.

See comment #50 and later here:
[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669)

---

