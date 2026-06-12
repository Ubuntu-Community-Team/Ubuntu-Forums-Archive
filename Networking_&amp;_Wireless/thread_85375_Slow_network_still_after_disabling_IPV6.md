---
title: "Slow network still after disabling IPV6"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by REInvestor on 2005-11-02
I have just installed Ubuntu on an old IBM Thinkpad 600.  The network card I am using is a linksys pcm200.  The card was not detected during install, so I skipped network configuration at that point, but it was present (and disabled) once installation was complete.  I enabled it, but was unable to get an IP using DHCP until I searched the forums and found about the IPV6 "issue".  I did the following to /etc/modprobe.d/aliases

alias net-pf-10 off

After rebooting I am now able to get an IP, but it seems like it takes a very long time for this to happen during boot (>20 seconds).  I can access the internet with Firefox sometimes, but only partially. This is only after editing Firefox according to the forum:

[http://ubuntuforums.org/showthread.php?t=76096](http://ubuntuforums.org/showthread.php?t=76096)

I can get google to open up, but not really anything else, so I do technically have a connection, but AOL dialup would seem like light speed next to this.

Synaptics can not access the online packages, or just times out trying.

I will try to add other relevant info, but since I am not able to access this forum from the affected computer, copying and pasting terminal outputs is not possible.

Also - the IBM Thinkpad 600 had 2 other issues (for those searching for answers), the screen resolution kept coming up 800x600 and the sound does not work.  

The screen resolution fix was easy, but it took me hours to figure it out.  Get out of GDM with ctl-alt-backspace then reconfigure X using "sudo dpkg-reconfigure xserver-xorg" and do not change anything except color depth - which needs to be 16bit instead of 24bit.  I tried changing everything else in an attempt to fix this problem - which is why it took so long.  If I had only known.

The sound problem I think can be fixed with alsaconf but it is not included with the base system.  After fighting with sound on this laptop with numerous other distributions, I finally found out the BIOS quick boot needed to be disabled in order to get the sound working using the CS4236 driver.  If anyone has sound working on this machine without adding to the base packages, please let me know.

But, I can live with no sound for a time, no internet on the otherhand makes the laptop worthless.  Is it possible I have the wrong driver installed?  How can I check this or correct that type of problem?

---

### Post by Wharry on 2005-11-02
Check out Mips' 'Option 1' here. [http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by REInvestor on 2005-11-02
Yup... did the same thing (plus more) using the info from a different forum (Link referenced in my original post. 

A small update, I can run synaptic, but I have been been waiting for more then an hour for 2MB (for alsasource) to download.  Any other ideas are welcomed.

---

### Post by mips on 2005-11-03
REInvestor,

Look at this thread again as I updated it 15hrs ago, dunno if you saw the updated version or not. Might help.
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by REInvestor on 2005-11-03
Thanks Mips, glad I caught your attentions, since it appears you are a bit of a guru here.  I was able to run synaptic sortof, but the download spped was so slow, it couldn't even be detected.  It would once and a while pop up with something like 1922B/s, then go back to unknown.  Anyway, it appears to be a system wide problem, not just Firefox.

Does something else "call" to ipv6 maybe?  In my network settings, I have the following hosts:

IP Address     Aliases
ff00::0          ip6-mcastprefix
127.0.0.1      localhost.localdomain localhost
fe00::0         ip6-localnet
ff02::2         ip6-allrouters
ff02::1         ip6-allnodes 
::1              ip6-localhost ip6-loopback
ff02::3         ip6-allhosts

These look like ipv6 settings to me, not ipv4, but I really know nothing about it beyond the basics I read yesterday when it appeared to me it was not being disabled completely. 

Any help you can provide is appreciated.  I created a new "location" in network settings (keeping what was above), then removed them from the default setting (keeping only 127.0.0.1), but after a reboot, I can no longer obtain an ip.

Any light you can shed on this is very much appreciated.

---

### Post by REInvestor on 2005-11-03
One more thing... important to note, this card on this computer works fine with fc4, suse9.1, simplymepis, etc.  I have good reasons for not wanting to run any of those distributions, but they did demonstrate to me it is not a hardware problem.  I am not dual booting with windoz, so I can not do option 3 on the computer, but I have another laptop with same hw config with mepis installed that I can pull relevant info from if needed.

---

### Post by mips on 2005-11-03
Lets see your **/etc/network/interfaces** file
Lets see output of  **ifconfig -a** command
Lets see output of **mii-diag** command
Lets see output of **mii-tool** command
Lets see output of **sudo dmesg** command (just for shits & giggles, sometimes you need a sense of humour)

I assume the cable is good from previous tests ?
What make&model hub are you using ?
Can you configure anything on the hub (speed/duplex/frames etc) ?
Does it work with a LiveCD ?

---

### Post by REInvestor on 2005-11-03
/etc/network/interfaces (I can't copy paste, so I'm going to leave the commented lines out
#
#
#
auto lo
iface lo inet loopback
#
#
mapping hotplug
     script grep
     map eth0

iface eth0 inet dhcp
auto eth0

ipconfig -a

command not found

sudo ipconfig -a
command not found

ifconfig -a (in case your post had a typo)

eth0  Link encap:Ethernet HWaddr 00:04:5A:A4:92:B9
inet addr: 192.168.123.172 Bcast 192.168.123.255 Mask 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:13 errors:0 dropped:0 overruns:0 frame:0
TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelan:1000
RX bytes:4012 (3.9 KiB) TX bytes:3420 (3.3 KiB)
Interrupt:9 Base address:0x4000

lo Link encap:Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:165 errors:0 dropped:0 overruns:0 frame:0
TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelan:0
RX bytes:8272 (8.0 KiB) TX bytes:8272 (8.0 KiB)

---

### Post by REInvestor on 2005-11-03
mii-diag
Using the default interface 'eth0'
SIOCGMIIPHY on eth0 failed: Operation not supported
(oops, keep forgetting sudo)

sudo mii-diag
Using the default interface 'eth0'
Basic registers of MII PHY #1:  1000 786d 001d 2411 05e1 45e1 0007 2001.
The autonegotiated capability is 01e0
The autonegotiated media type is 100baseTx-FD
Basic mode control register 0x1000: Auto-negotiation enabled
You have link beat, and everything is working OK.
Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/802.3x flow control.
End of basic transceiver information.

sudo mii-tool
eth0: negotiated 100baseTx-FD flow-control, link ok

sudo dmesg
uh... the output is way too much for me to type, please keep in mind nothing above is copy paste, I manually entered everything from another (gulp) windoz machine.

I will try to paste the output up here later if I can at least get a minimal connection to something going...

As for your other questions, currently I am using a Linksys router/hub that worked properly with the machine in question while it had Suse 9.1 installed and the same network card and cable.  Also, I have another Thinkpad 600 Laptop with Simplymepis installed that functions properly with the network card/cable/router configuration I am using (just tested it again to make sure).  I am quite certain it is not a hardware problem external to the system and would be suprised if it is a hardware problem internal (I am a linux newbie of sorts, but I understand the hardware aspects - at least the basics - relatively well in my humble opinion). 

Again, your help is very much appreciated.  Something has really caught my attention with Ubuntu that makes me want to stick with it.  This laptop is a test case that I will use to prove to myself I can function without a windoze computer.  I think it will still take a little help from Wine, but if I can do it I will be buying a "real" laptop to put ubuntu on.

---

### Post by mips on 2005-11-03
[QUOTE=REInvestor]mii-diag
sudo dmesg
uh... the output is way too much for me to type, please keep in mind nothing above is copy paste, I manually entered everything from another (gulp) windoz machine.

I will try to paste the output up here later if I can at least get a minimal connection to something going...

As for your other questions, currently I am using a Linksys router/hub that worked properly with the machine in question while it had Suse 9.1 installed and the same network card and cable.  [/QUOTE]

Ouch, did not know you are entering this manually, dont you have a small memory stick or something you can copy and paste to ?

I will have a good look at this a bit later, need some zzzzzzzzz's now. Sorry I did a typo on ifconfig, to much windoze in my blood.

Have you tried the card in a different PCMCIA/cardbus slot ?

Last question, what **model** Linksys Router do you have & **Firmware** version please ???

---

### Post by mips on 2005-11-03
I dont see anything glaringly wrong here.

Did you ever try this laptop/network card with Ubuntu Hoary (maybe LiveCD) by any chance ?

Have you tried static IP addresses ?

I have noticed that 'some' things that worked in hoary dont always have the same results in breezy.

Sorry for the millions of questions, this one is weird and probably something simple not thought of... (I'm beginning to resemble my avatar, lol)

---

### Post by REInvestor on 2005-11-03
[QUOTE=mips]Ouch, did not know you are entering this manually, dont you have a small memory stick or something you can copy and paste to ?

I will have a good look at this a bit later, need some zzzzzzzzz's now. Sorry I did a typo on ifconfig, to much windoze in my blood.

Have you tried the card in a different PCMCIA/cardbus slot ?

Last question, what **model** Linksys Router do you have & **Firmware** version please ???[/QUOTE]

Tried it in both slots with the same results (or lack there of)

The router is actually not a linksys... oops... it is an Asante FriendlyNet FR1104-G Router... I just had to roll out my 51" TV to have a look.  My whole house is wired (did it myself), I have a 16 port Linksys Switch EZXS16W supplying the internet feed to the Asante (the Asante is my wireless for the house, but I was plugging into it so I could mess with the system while watching TV).  I have tried plugging directly into the Linksys switch before, but I still have the same problem.  BTW, the Linksys is behind an old box running FC2 that serves as my gateway/firewall/router and I also have Vonage (VOIP) inbetween that box and my Cable Modem.  It turns out to be 3 routers (including what is built into the Vonage box - Linksys RT31P2) which I know is a bit overkill, but I wanted to keep all of the wireless traffic seperated from my internal network.

I have a slow connection that I seem to be able to access the forums from, so I will post the output of dmesg soon

---

### Post by REInvestor on 2005-11-03
OK... here goes...

rob@ubuntu:~$ sudo dmesg
um II (Deschutes) stepping 00
[4294670.113000] Enabling fast FPU save and restore... done.
[4294670.113000] Checking 'hlt' instruction... OK.
[4294670.117000] Checking for popad bug... OK.
[4294670.117000] checking if image is initramfs... it is
[4294673.352000] Freeing initrd memory: 4821k freed
[4294673.358000] ACPI: Looking for DSDT in initrd... not found!
[4294673.859000]  not found!
[4294674.148000] ACPI: setting ELCR to 0200 (from 0800)
[4294674.172000] NET: Registered protocol family 16
[4294674.172000] EISA bus registered
[4294674.172000] ACPI: bus type pci registered
[4294674.175000] PCI: PCI BIOS revision 2.10 entry at 0xfd880, last bus=6
[4294674.175000] PCI: Using configuration type 1
[4294674.175000] mtrr: v2.0 (20020519)
[4294674.177000] ACPI: Subsystem revision 20050729
[4294675.057000] ACPI: Interpreter enabled
[4294675.057000] ACPI: Using PIC for interrupt routing
[4294675.063000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294675.069000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294675.075000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294675.080000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294675.084000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294675.084000] PCI: Probing PCI hardware (bus 00)
[4294675.090000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294675.090000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294675.160000] Boot video device is 0000:00:03.0
[4294675.217000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294675.221000] ACPI: Power Resource [PSIO] (on)
[4294675.300000] burst-mode-ec-10-Aug
[4294675.300000] ACPI: Embedded Controller [EC0] (gpe 9)
[4294675.330000] ACPI: Power Resource [PFN0] (off)
[4294675.332000] ACPI: Power Resource [PVID] (on)
[4294675.333000] ACPI: Power Resource [PRSD] (off)
[4294675.334000] ACPI: Power Resource [PDCK] (on)
[4294675.334000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294675.334000] pnp: PnP ACPI init
[4294675.404000] pnp: PnP ACPI: found 17 devices
[4294675.404000] PnPBIOS: Disabled by ACPI PNP
[4294675.404000] PCI: Using ACPI for IRQ routing
[4294675.404000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294675.414000] pnp: 00:0c: ioport range 0x15e0-0x15ef has been reserved
[4294675.414000] pnp: 00:0c: ioport range 0xef00-0xef3f could not be reserved
[4294675.414000] pnp: 00:0c: ioport range 0xefa0-0xefaf has been reserved
[4294675.419000] audit: initializing netlink socket (disabled)
[4294675.419000] audit: initialized
[4294675.420000] VFS: Disk quotas dquot_6.5.1
[4294675.420000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294675.420000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294675.421000] devfs: boot_options: 0x0
[4294675.421000] Initializing Cryptographic API
[4294675.421000] Limiting direct PCI/PCI transfers.
[4294675.422000] isapnp: Scanning for PnP cards...
[4294675.775000] isapnp: No Plug & Play device found
[4294675.961000] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:MOU0] at 0x60,0x64 irq 1,12
[4294675.973000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294675.974000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294675.974000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294675.975000] ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[4294676.000000] pnp: Device 00:02 activated.
[4294676.001000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294676.002000] io scheduler noop registered
[4294676.003000] io scheduler anticipatory registered
[4294676.003000] io scheduler deadline registered
[4294676.003000] io scheduler cfq registered
[4294676.006000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294676.009000] EISA: Probing bus 0 at eisa.0
[4294676.009000] Cannot allocate resource for EISA slot 8
[4294676.009000] EISA: Detected 0 cards.
[4294676.009000] NET: Registered protocol family 2
[4294676.019000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294676.020000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294676.021000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294676.021000] TCP: Hash tables configured (established 16384 bind 16384)
[4294676.022000] NET: Registered protocol family 8
[4294676.022000] NET: Registered protocol family 20
[4294676.024000] ACPI wakeup devices:
[4294676.024000] LID0 SLPB PCI0 UAR1 MWV0 BAT0 USB0
[4294676.024000] ACPI: (supports S0 S1 S3 S4 S5)
[4294676.028000] Freeing unused kernel memory: 224k freed
[4294676.100000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294676.156000] vga16fb: initializing
[4294676.156000] vga16fb: mapped to 0xc00a0000
[4294676.323000] Console: switching to colour frame buffer device 80x30
[4294676.323000] fb0: VGA16 VGA frame buffer device
[4294677.742000] Capability LSM initialized
[4294677.840000] NET: Registered protocol family 1
[4294677.952000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294677.952000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294677.952000] ACPI: bus type ide registered
[4294677.983000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294677.983000] PIIX4: chipset revision 1
[4294677.983000] PIIX4: not 100% native mode: will probe irqs later
[4294677.983000]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
[4294677.983000]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd:pio
[4294677.983000] Probing IDE interface ide0...
[4294678.247000] hda: TOSHIBA MK6021GAS, ATA DISK drive
[4294678.861000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294678.867000] Probing IDE interface ide1...
[4294679.540000] hdc: TOSHIBA CD-ROM XM-1702BC, ATAPI CD/DVD-ROM drive
[4294679.847000] ide1 at 0x170-0x177,0x376 on irq 15
[4294679.848000] Probing IDE interface ide2...
[4294680.361000] Probing IDE interface ide3...
[4294680.874000] Probing IDE interface ide4...
[4294681.387000] Probing IDE interface ide5...
[4294681.935000] hda: max request size: 128KiB
[4294681.998000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(33)
[4294681.999000] hda: cache flushes supported
[4294681.999000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294682.110000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[4294682.110000] Uniform CD-ROM driver Revision: 3.20
[4294684.200000] Attempting manual resume
[4294684.278000] swsusp: Suspend partition has wrong signature?
[4294684.725000] usbcore: registered new driver usbfs
[4294684.726000] usbcore: registered new driver hub
[4294684.737000] USB Universal Host Controller Interface driver v2.2
[4294684.741000] ACPI: PCI Interrupt Link [LNKD] disabled and referenced, BIOS bug.
[4294684.742000] ACPI: PCI Interrupt Link [LNKD] BIOS reported IRQ 0, using IRQ 9
[4294684.743000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294684.743000] PCI: setting IRQ 9 as level-triggered
[4294684.743000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294684.743000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[4294684.805000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294684.805000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00008400
[4294684.806000] hub 1-0:1.0: USB hub found
[4294684.806000] hub 1-0:1.0: 2 ports detected
[4294689.138000] ACPI: Fan [FN00] (off)
[4294689.139000] ACPI: Fan [FN20] (off)
[4294689.139000] ACPI: Fan [FN60] (off)
[4294689.167000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294689.197000] ACPI: Thermal Zone [THM0] (61 C)
[4294689.202000] ACPI: Thermal Zone [THM2] (41 C)
[4294689.207000] ACPI: Thermal Zone [THM6] (31 C)
[4294689.681000] Attempting manual resume
[4294689.707000] swsusp: Suspend partition has wrong signature?
[4294689.822000] kjournald starting.  Commit interval 5 seconds
[4294689.822000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.823000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294703.285000] Adding 843372k swap on /dev/hda5.  Priority:-1 extents:1
[4294703.803000] EXT3 FS on hda1, internal journal
[4294716.886000] parport: PnPBIOS parport detected.
[4294716.886000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[4294717.005000] lp0: using parport0 (interrupt-driven).
[4294717.206000] mice: PS/2 mouse device common for all mice
[4294718.289000] input: PS/2 Generic Mouse on isa0060/serio1
[4294720.683000] ts: Compaq touchscreen protocol output
[4294724.670000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294726.473000] cdrom: open failed.
[4294732.045000] Linux Kernel Card Services
[4294732.046000]   options:  [pci] [cardbus] [pm]
[4294732.152000] ACPI: PCI Interrupt Link [LNKA] disabled and referenced, BIOS bug.
[4294732.154000] ACPI: PCI Interrupt Link [LNKA] BIOS reported IRQ 0, using IRQ 9
[4294732.154000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[4294732.154000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294732.154000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0092]
[4294732.154000] Yenta: Enabling burst memory read transactions
[4294732.154000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294732.154000] Yenta: Routing CardBus interrupts to PCI
[4294732.154000] Yenta TI: socket 0000:00:02.0, mfunc 0xfba97543, devctl 0x62
[4294732.255000] Yenta TI: socket 0000:00:02.0 probing PCI interrupt failed, trying to fix
[4294732.356000] Yenta TI: socket 0000:00:02.0 no PCI interrupts. Fish. Please report.
[4294732.476000] Yenta: ISA IRQ mask 0x0418, PCI irq 0
[4294732.476000] Socket status: 30000020
[4294732.568000] ACPI: PCI Interrupt Link [LNKB] disabled and referenced, BIOS bug.
[4294732.570000] ACPI: PCI Interrupt Link [LNKB] BIOS reported IRQ 0, using IRQ 10
[4294732.570000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294732.570000] PCI: setting IRQ 10 as level-triggered
[4294732.570000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294732.570000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0092]
[4294732.570000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294732.570000] Yenta: Routing CardBus interrupts to PCI
[4294732.570000] Yenta TI: socket 0000:00:02.1, mfunc 0xfba97543, devctl 0x62
[4294733.400000] irq 10: nobody cared (try booting with the "irqpoll" option.
[4294733.400000]  [<c012de13>] __report_bad_irq+0x31/0x74
[4294733.400000]  [<c012deeb>] note_interrupt+0x7d/0xa2
[4294733.400000]  [<c012da10>] __do_IRQ+0x85/0xb1
[4294733.400000]  [<c0104ca5>] do_IRQ+0x19/0x24
[4294733.400000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294733.400000]  [<c0119058>] __do_softirq+0x2c/0x7d
[4294733.400000]  [<c01190cb>] do_softirq+0x22/0x26
[4294733.400000]  [<c0104caa>] do_IRQ+0x1e/0x24
[4294733.400000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294733.400000]  [<c012dbee>] setup_irq+0x9d/0xc1
[4294733.400000]  [<d29d7e79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294733.400000]  [<c012dd07>] request_irq+0x72/0x8b
[4294733.400000]  [<d29d7f1c>] yenta_probe_cb_irq+0x69/0xeb [yenta_socket]
[4294733.400000]  [<d29d7e79>] yenta_probe_handler+0x0/0x3a [yenta_socket]
[4294733.400000]  [<d29d73fb>] ti12xx_irqroute_func1+0x9e/0x1f3 [yenta_socket]
[4294733.400000]  [<d29d7937>] ti12xx_override+0x124/0x13d [yenta_socket]
[4294733.400000]  [<d29d79b9>] ti1250_override+0x69/0x6e [yenta_socket]
[4294733.400000]  [<d29d8228>] yenta_probe+0x131/0x1f9 [yenta_socket]
[4294733.400000]  [<c01a2cdd>] pci_device_probe_static+0x2e/0x41
[4294733.400000]  [<c01a2d0f>] __pci_device_probe+0x1f/0x32
[4294733.400000]  [<c01a2d3e>] pci_device_probe+0x1c/0x31
[4294733.400000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294733.400000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4294733.400000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4294733.400000]  [<c01ec7a5>] driver_register+0x23/0x25
[4294733.400000]  [<c01a2f01>] pci_register_driver+0x5f/0x72
[4294733.400000]  [<d289000a>] yenta_socket_init+0xa/0xc [yenta_socket]
[4294733.400000]  [<c0129682>] sys_init_module+0xb5/0x172
[4294733.400000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294733.400000] handlers:
[4294733.400000] [<d29d7e79>] (yenta_probe_handler+0x0/0x3a [yenta_socket])
[4294733.400000] Disabling IRQ #10
[4294733.503000] Yenta TI: socket 0000:00:02.1 probing PCI interrupt failed, trying to fix
[4294733.604000] Yenta TI: socket 0000:00:02.1 no PCI interrupts. Fish. Please report.
[4294733.724000] Yenta: ISA IRQ mask 0x0018, PCI irq 0
[4294733.724000] Socket status: 30000006
[4294735.483000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294735.490000] PCI: Enabling device 0000:01:00.0 (0000 -> 0003)
[4294735.491000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294735.491000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294735.492000] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[4294735.508000] eth0: ADMtek Comet rev 17 at 00014000, 00:04:5A:A4:92:B9, IRQ 9.
[4294737.835000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294737.835000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[4294737.835000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[4294739.801000] Floppy drive(s): fd0 is 1.44M
[4294739.813000] FDC 0 is a National Semiconductor PC87306
[4294741.257000] irda_init()
[4294741.257000] NET: Registered protocol family 23
[4294742.427000] gameport: NS558 ISA Gameport is isa0200/gameport0, io 0x202, speed 641kHz
[4294742.466000] pnp: Unable to assign resources to device 00:07.
[4294742.466000] ns558: probe of 00:07 failed with error -16
[4294743.905000] input: PC Speaker
[4294745.837000] Real Time Clock Driver v1.12
[4294748.680000] NET: Registered protocol family 17
[4294751.592000] 0000:01:00.0: tulip_stop_rxtx() failed
[4294751.592000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4294818.135000] 0000:01:00.0: tulip_stop_rxtx() failed
[4294818.138000] ACPI: AC Adapter [AC] (on-line)
[4294818.550000] ACPI: Battery Slot [BAT0] (battery present)
[4294818.713000] ACPI: Power Button (FF) [PWRF]
[4294818.713000] ACPI: Lid Switch [LID0]
[4294818.713000] ACPI: Sleep Button (CM) [SLPB]
[4294819.537000] ibm_acpi: ec object not found
[4294820.443000] ACPI: Video Device [VID0] (multi-head: yes  rom: no  post: no)
[4294845.642000] IBM machine detected. Enabling interrupts during APM calls.
[4294845.642000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294845.642000] apm: overridden by ACPI.
[4294849.408000] cs: IO port probe 0x100-0x4ff: excluding 0x130-0x137 0x220-0x22f 0x388-0x38f 0x4d0-0x4d7
[4294849.410000] cs: IO port probe 0x100-0x4ff: excluding 0x130-0x137 0x220-0x22f 0x388-0x38f 0x4d0-0x4d7
[4294849.414000] cs: IO port probe 0xc00-0xcf7: clean.
[4294849.415000] cs: IO port probe 0xc00-0xcf7: clean.
[4294849.416000] cs: IO port probe 0xa00-0xaff: clean.
[4294849.417000] cs: IO port probe 0xa00-0xaff: clean.
[4294854.058000] Bluetooth: Core ver 2.7
[4294854.058000] NET: Registered protocol family 31
[4294854.058000] Bluetooth: HCI device and connection manager initialized
[4294854.058000] Bluetooth: HCI socket layer initialized
[4294854.201000] Bluetooth: L2CAP ver 2.7
[4294854.201000] Bluetooth: L2CAP socket layer initialized
[4294854.315000] Bluetooth: RFCOMM ver 1.5
[4294854.315000] Bluetooth: RFCOMM socket layer initialized
[4294854.315000] Bluetooth: RFCOMM TTY layer initialized

Hope this points to something MIPS, I am at a loss with no clue on what to do next.  Network settings still show ip6 items, are they normal even if ipv6 is disabled in aliases?

---

### Post by REInvestor on 2005-11-03
Sorry for the smilies, guess I should have checked the "no smilies" box.  If anyone can explain this output to me, that would be great... hahahaha... I understand some of it I think, but it's been 12 years since I finished my EE degree and have not really delved into the inner workings since.

---

### Post by REInvestor on 2005-11-04
ok... I added acpi=off to the linux boot line in GRUB and now all seems well...

Can someone explain this to me and tell me if there is another boot line parameter I should be using.

---

### Post by mips on 2005-11-04
Unfortunately I have no knowledge of acpi. All I know is that it has to do with advanced config & power interface. I have not touched it on my HP laptop yet as all seemed fine but i'll probably have to next week when I install a new wireless adapter. [http://www.acpi.info/](http://www.acpi.info/)

Does the fan on you IBM work ?

The good thing is that it working.

---

