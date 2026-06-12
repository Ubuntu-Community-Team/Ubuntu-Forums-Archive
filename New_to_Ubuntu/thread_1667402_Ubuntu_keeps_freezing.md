---
title: "Ubuntu keeps freezing"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Howlin1 on 2011-01-14
Hello. I am totally new to Ubuntu.
I installed Ubunutu 10.10 onto my 8gb USB key a few days ago and for some reason it keeps freezing every now and then. On a laptop the screen greys out and on a desktop the screen freezes. 
Does anyone know why this is happening and how it can be resolved?

Attached is a screenshot of the Gparted (if it helps. I was on the #Ubuntu  IRC channel earlier and someone said it might have something to do with  the space on the USB).

---

### Post by rajeev1204 on 2011-01-15
Why is it installed to a USB? How about installing to a real HDD instead of a thumb drive.

Its freezing due to space constraints probably.

---

### Post by Howlin1 on 2011-01-15
> **rajeev1204 said:**
> Why is it installed to a USB? How about installing to a real HDD instead of a thumb drive.

Its freezing due to space constraints probably.
I have it on my thumb drive because I don't have a HDD (or the money for one), and I know of people who have Ubuntu on a USB key and it works just fine for them. Is there anything I can do to get some more space (other than being advised to not use a thumb drive and use a HDD)?

---

### Post by Howlin1 on 2011-01-15
Sorry double post.

---

### Post by Howlin1 on 2011-01-15
Sorry triple post

---

### Post by Howlin1 on 2011-01-15
Sorry quadruple post.

---

### Post by Howlin1 on 2011-01-15
Sorry quintuple post.

---

### Post by ronnielsen1 on 2011-01-15
What's the specs on the computer? Memory and Processor or model #

---

### Post by Howlin1 on 2011-01-15
> **ronnielsen1 said:**
> What's the specs on the computer? Memory and Processor or model #
My laptop is a Fujitsu Siemens Amilo li272 and the desktop has;
Intel(R) Celeron(R) D CPU 3.06GHz and it has 3gb of RAM.

Is that what you were referring to?
**

---

### Post by ronnielsen1 on 2011-01-15
> 
Is that what you were referring to?

Exactly. Just making sure that wasn't your problem. It's not

---

### Post by Howlin1 on 2011-01-15
> **ronnielsen1 said:**
> Exactly. Just making sure that wasn't your problem. It's not
Could that be the problem with the laptop?

---

### Post by manters2000 on 2011-01-15
> **Howlin1 said:**
> Hello. I am totally new to Ubuntu.
I installed Ubunutu 10.10 onto my 8gb USB key a few days ago and for some reason it keeps freezing every now and then. On a laptop the screen greys out and on a desktop the screen freezes. 
Does anyone know why this is happening and how it can be resolved?

Attached is a screenshot of the Gparted (if it helps. I was on the #Ubuntu  IRC channel earlier and someone said it might have something to do with  the space on the USB).

Same problem with me, but my Ubuntu 10.10 was installed in hard disk dual booted with Windows.

It usually happens around 30 or 40 mins after log in, and bang, it freezes and totally unresponsive. This usually happens when I browse the web using Mozilla Firefox !

---

### Post by Howlin1 on 2011-01-16
So can anyone help me?

---

### Post by rajeev1204 on 2011-01-16
Can you paste output of /var/log/kern.org 

```
cat /var/log/kern.log
```

---

### Post by Howlin1 on 2011-01-16
> **rajeev1204 said:**
> Can you paste output of /var/log/kern.org 

```
cat /var/log/kern.log
```
Sure. 
```
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372283] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372475] hub 1-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372482] hub 1-0:1.0: 4 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372585]   alloc irq_desc for 23 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372588]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372598] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372624] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372628] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372679] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.372714] ehci_hcd 0000:00:1d.7: debug port 1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.376605] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.376630] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400040] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400240] hub 2-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400246] hub 2-0:1.0: 6 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400357] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400378] uhci_hcd: USB Universal Host Controller Interface driver
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400431] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400441] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400446] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400496] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400548] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400694] hub 3-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400699] hub 3-0:1.0: 2 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400774]   alloc irq_desc for 21 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400777]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400785] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400792] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400797] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400843] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.400884] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401036] hub 4-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401041] hub 4-0:1.0: 2 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401117] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401125] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401129] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401168] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401198] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401336] hub 5-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401341] hub 5-0:1.0: 2 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401416] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401424] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401428] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401464] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401504] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401644] hub 6-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401648] hub 6-0:1.0: 2 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401719] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401726] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401730] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401773] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401805] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401938] hub 7-0:1.0: USB hub found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.401943] hub 7-0:1.0: 2 ports detected
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.402094] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.410267] i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425169] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425185] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425188] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425192] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425195] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425312] mice: PS/2 mouse device common for all mice
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425484] rtc_cmos 00:07: RTC can wake from S4
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425538] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425574] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.425715] device-mapper: uevent: version 1.0.3
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.450605] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468298] device-mapper: multipath: version 1.1.1 loaded
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468304] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468533] EISA: Probing bus 0 at eisa.0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468536] EISA: Cannot allocate resource for mainboard
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468539] Cannot allocate resource for EISA slot 1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468541] Cannot allocate resource for EISA slot 2
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468543] Cannot allocate resource for EISA slot 3
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468546] Cannot allocate resource for EISA slot 4
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468548] Cannot allocate resource for EISA slot 5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468550] Cannot allocate resource for EISA slot 6
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468552] Cannot allocate resource for EISA slot 7
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468555] Cannot allocate resource for EISA slot 8
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.468557] EISA: Detected 0 cards.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.488266] cpuidle: using governor ladder
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.488365] cpuidle: using governor menu
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.488786] TCP cubic registered
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.488951] NET: Registered protocol family 10
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.489392] lo: Disabled Privacy Extensions
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.489678] NET: Registered protocol family 17
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.490490] Using IPI No-Shortcut mode
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.490610] PM: Resume from disk failed.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.490625] registered taskstats version 1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.491029]   Magic number: 11:428:601
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.491139] rtc_cmos 00:07: setting system clock to 2011-01-16 21:33:49 UTC (1295213629)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.491142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.491144] EDD information not available.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.503148] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.527882] ata1.00: ATAPI: Optiarc DVD RW AD-7590A, 1.41, max UDMA/33
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.544608] ata1.00: configured for UDMA/33
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.707429] Freeing initrd memory: 15536k freed
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.713779] isapnp: No Plug & Play device found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.720070] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7590A  1.41 PQ: 0 ANSI: 5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743020] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743025] Uniform CD-ROM driver Revision: 3.20
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743178] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743261] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743337] Freeing unused kernel memory: 684k freed
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743897] Write protecting the kernel text: 4932k
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.743959] Write protecting the kernel read-only data: 1976k
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.744055] usb 2-3: new high speed USB device using ehci_hcd and address 2
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.768465] udev[87]: starting version 163
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930227] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930260] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930329] r8169 0000:02:00.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930416]   alloc irq_desc for 43 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930418]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.930439] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.931094] r8169 0000:02:00.0: eth0: RTL8101e at 0xf810e000, 00:1f:16:00:43:d0, XID 94200000 IRQ 43
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.976410] Linux agpgart interface v0.103
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.979842] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    0.980452] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.005998] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006161] ahci 0000:00:1f.2: version 3.0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006186] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006240]   alloc irq_desc for 44 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006243]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006257] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006355] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006359] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.006366] ahci 0000:00:1f.2: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.007871] scsi2 : ahci
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.008099] scsi3 : ahci
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.008191] scsi4 : ahci
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.008400] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 44
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.008405] ata4: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 44
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.008409] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 44
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.015392] Initializing USB Mass Storage driver...
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.015540] scsi5 : usb-storage 2-3:1.0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.015653] usbcore: registered new interface driver usb-storage
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.015655] USB Mass Storage support registered.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.110493] [drm] Initialized drm 1.1.0 20060810
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.324054] ata5: SATA link down (SStatus 0 SControl 300)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.324059] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.324094] ata4: SATA link down (SStatus 0 SControl 300)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.324986] ata3.00: unexpected _GTF length (8)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.702437] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.702441] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.703822] ata3.00: unexpected _GTF length (8)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.704079] ata3.00: configured for UDMA/133
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720183] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720390] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720405] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720492] sd 2:0:0:0: [sda] Write Protect is off
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720496] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720531] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.720862]  sda: sda1 sda2 sda3
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.723574] sd 2:0:0:0: [sda] Attached SCSI disk
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.753722] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.753729] i915 0000:00:02.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.772294]   alloc irq_desc for 45 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.772299]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.772309] i915 0000:00:02.0: irq 45 for MSI/MSI-X
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.772323] [drm] set up 7M of stolen space
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.878240] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    1.878554] [drm] initialized overlay support
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.264038] Skipping EDID probe due to cached edid
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.346454] scsi 5:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0 CCS
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.347208] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.348571] sd 5:0:0:0: [sdb] 15360000 512-byte logical blocks: (7.86 GB/7.32 GiB)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.349300] sd 5:0:0:0: [sdb] Write Protect is off
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.349303] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.349306] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.351798] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.351805]  sdb: sdb1 sdb2 sdb3 < sdb5 > sdb4
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.357193] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.357198] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.692383] Console: switching to colour frame buffer device 160x50
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.696576] fb0: inteldrmfb frame buffer device
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.696578] drm: registered panic notifier
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.696588] Slow work thread pool: Starting up
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.696739] Slow work thread pool: Ready
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.713253] acpi device:03: registered as cooling_device2
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.713717] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.713845] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.713967] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    2.924033] Skipping EDID probe due to cached edid
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [    3.414195] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.433601] udev[458]: starting version 163
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.437269] Adding 1678332k swap on /dev/sdb4.  Priority:-1 extents:1 across:1678332k 
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.603959] lp: driver loaded but no devices found
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.787578] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.813399] cfg80211: Calling CRDA to update world regulatory domain
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.900574] acer-wmi: Acer Laptop ACPI-WMI Extras
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923349] cfg80211: World regulatory domain updated:
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923355]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923359]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923362]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923365]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923369]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.923372]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.926840] type=1400 audit(1295213639.932:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=744 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.927648] type=1400 audit(1295213639.932:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=744 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.928172] type=1400 audit(1295213639.936:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=744 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.941665] ath5k 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.941680] ath5k 0000:08:00.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   10.941741] ath5k 0000:08:00.0: registered as 'phy0'
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.258912]   alloc irq_desc for 22 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.258916]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.258925] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.258992]   alloc irq_desc for 46 on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.258995]   alloc kstat_irqs on node -1
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.259009] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.259054] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.304574] hda_codec: ALC268: BIOS auto-probing.
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.446220] ath: EEPROM regdomain: 0x30
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.446224] ath: EEPROM indicates we should expect a direct regpair map
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.446228] ath: Country alpha2 being used: AM
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.446230] ath: Regpair used: 0x30
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.457169] phy0: Selected rate control algorithm 'minstrel'
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.457959] Registered led device: ath5k-phy0::rx
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.457984] Registered led device: ath5k-phy0::tx
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.457988] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.458156] cfg80211: Calling CRDA for country: AM
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.466248] cfg80211: Regulatory domain changed to country: AM
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.466252]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.466256]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.466259]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.466262]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.494550] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1280b1, caps: 0xa04711/0xa04000/0x0
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   11.544157] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.481638] type=1400 audit(1295213642.488:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1118 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.482442] type=1400 audit(1295213642.488:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1118 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.482879] type=1400 audit(1295213642.488:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1118 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.484830] type=1400 audit(1295213642.488:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1117 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.496453] type=1400 audit(1295213642.500:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1122 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.501097] type=1400 audit(1295213642.508:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1127 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.502066] type=1400 audit(1295213642.508:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1127 comm="apparmor_parser"
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.531140] ppdev: user-space parallel port driver
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.610709] r8169 0000:02:00.0: eth0: link up
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.610714] r8169 0000:02:00.0: eth0: link up
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.633420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 16 21:34:02 joseph-AMILO-Li-2727 kernel: [   13.708150] Skipping EDID probe due to cached edid
Jan 16 21:34:03 joseph-AMILO-Li-2727 kernel: [   14.060880] Skipping EDID probe due to cached edid
Jan 16 21:34:07 joseph-AMILO-Li-2727 kernel: [   18.581054] Skipping EDID probe due to cached edid
Jan 16 21:34:07 joseph-AMILO-Li-2727 kernel: [   18.944070] Skipping EDID probe due to cached edid
Jan 16 21:34:09 joseph-AMILO-Li-2727 kernel: [   20.084106] Skipping EDID probe due to cached edid
Jan 16 21:34:09 joseph-AMILO-Li-2727 kernel: [   20.433056] Skipping EDID probe due to cached edid
Jan 16 21:34:13 joseph-AMILO-Li-2727 kernel: [   24.496019] eth0: no IPv6 routers present
Jan 16 21:34:56 joseph-AMILO-Li-2727 kernel: [   71.150384] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
Jan 16 21:35:58 joseph-AMILO-Li-2727 kernel: [  132.996511] padlock: VIA PadLock not detected.
Jan 16 21:36:07 joseph-AMILO-Li-2727 kernel: [  142.092092] Skipping EDID probe due to cached edid
Jan 16 21:36:08 joseph-AMILO-Li-2727 kernel: [  142.445058] Skipping EDID probe due to cached edid
Jan 16 21:36:08 joseph-AMILO-Li-2727 kernel: [  142.809092] Skipping EDID probe due to cached edid
Jan 16 21:36:08 joseph-AMILO-Li-2727 kernel: [  143.168079] Skipping EDID probe due to cached edid
Jan 16 21:36:16 joseph-AMILO-Li-2727 kernel: [  151.168080] Skipping EDID probe due to cached edid
Jan 16 21:40:45 joseph-AMILO-Li-2727 kernel: [  419.241087] Skipping EDID probe due to cached edid

```

---

### Post by rajeev1204 on 2011-01-17
This is not the entire contents of the log but np.In future you can do a cat /var/log/kern.log > somefile.txt 

Ok now  post this from a terminal :

$ dmesg : tail 

Also, does the system freeze when trying to resume from sleep or period of inactivity? Or when doing some work.Check syslog and xorg.log for any signs or messages too.

Can you give more details of what you were doing when this happens?

---

### Post by Howlin1 on 2011-01-17
> **rajeev1204 said:**
> This is not the entire contents of the log but np.In future you can do a cat /var/log/kern.log > somefile.txt 

Ok now  post this from a terminal :

$ dmesg : tail 

Also, does the system freeze when trying to resume from sleep or period of inactivity? Or when doing some work.Check syslog and xorg.log for any signs or messages too.

Can you give more details of what you were doing when this happens?
You mean:
```

[    0.203977] pci 0000:00:1f.2: PME# disabled
[    0.204020] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.204051] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.204207] pci 0000:02:00.0: reg 10: [io  0x2000-0x20ff]
[    0.204240] pci 0000:02:00.0: reg 18: [mem 0xf6000000-0xf6000fff 64bit]
[    0.204274] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.204346] pci 0000:02:00.0: supports D1 D2
[    0.204349] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.204357] pci 0000:02:00.0: PME# disabled
[    0.204393] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.204409] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.204416] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.204422] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.204432] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.204503] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.204509] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.204516] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.204525] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.204652] pci 0000:08:00.0: reg 10: [mem 0xfa000000-0xfa00ffff 64bit]
[    0.204794] pci 0000:08:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.204809] pci 0000:00:1c.2: PCI bridge to [bus 08-09]
[    0.204815] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.204821] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.204831] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.204937] pci 0000:00:1e.0: PCI bridge to [bus 10-10] (subtractive decode)
[    0.204943] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.204949] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.204959] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.204962] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.204965] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.204968] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.204971] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.204974] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.204977] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.204981] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.204984] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.204987] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.205019] pci_bus 0000:00: on NUMA node 0
[    0.205027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.205503] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.205603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.205759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.226579] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.226705] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.226832] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.226953] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.227074] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.227196] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.227318] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.227439] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.227500] HEST: Table is not found!
[    0.227599] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.227621] vgaarb: loaded
[    0.227829] SCSI subsystem initialized
[    0.228000] libata version 3.00 loaded.
[    0.228012] usbcore: registered new interface driver usbfs
[    0.228026] usbcore: registered new interface driver hub
[    0.228062] usbcore: registered new device driver usb
[    0.228371] ACPI: WMI: Mapper loaded
[    0.228373] PCI: Using ACPI for IRQ routing
[    0.228377] PCI: pci_cache_line_size set to 64 bytes
[    0.228510] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.228514] reserve RAM buffer: 000000007f6d0000 - 000000007fffffff 
[    0.228628] NetLabel: Initializing
[    0.228630] NetLabel:  domain hash size = 128
[    0.228632] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.228647] NetLabel:  unlabeled traffic allowed by default
[    0.228688] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.228697] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.228703] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.232037] Switching to clocksource tsc
[    0.245427] AppArmor: AppArmor Filesystem Enabled
[    0.245450] pnp: PnP ACPI init
[    0.245477] ACPI: bus type pnp registered
[    0.249965] pnp: PnP ACPI: found 10 devices
[    0.249968] ACPI: ACPI bus type pnp unregistered
[    0.249974] PnPBIOS: Disabled by ACPI PNP
[    0.249990] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.249993] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.249997] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.250000] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.250004] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.250007] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.250010] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.250019] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.250027] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.250030] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.250034] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.250037] system 00:06: [io  0xfe00] has been reserved
[    0.250041] system 00:06: [mem 0xff800000-0xff800fff] has been reserved
[    0.286435] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80000000-0x800000ff]
[    0.286447] pci 0000:00:1f.3: BAR 0: set to [mem 0x80000000-0x800000ff] (PCI address [0x80000000-0x800000ff]
[    0.286452] pci 0000:02:00.0: BAR 6: assigned [mem 0xf0000000-0xf001ffff pref]
[    0.286456] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.286460] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.286468] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.286474] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.286484] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.286488] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.286496] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.286502] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.286511] pci 0000:00:1c.2: PCI bridge to [bus 08-09]
[    0.286515] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.286523] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.286529] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.286539] pci 0000:00:1e.0: PCI bridge to [bus 10-10]
[    0.286541] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.286548] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.286553] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.286582]   alloc irq_desc for 17 on node -1
[    0.286585]   alloc kstat_irqs on node -1
[    0.286594] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.286602] pci 0000:00:1c.0: setting latency timer to 64
[    0.286615]   alloc irq_desc for 16 on node -1
[    0.286617]   alloc kstat_irqs on node -1
[    0.286622] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.286628] pci 0000:00:1c.1: setting latency timer to 64
[    0.286641]   alloc irq_desc for 18 on node -1
[    0.286643]   alloc kstat_irqs on node -1
[    0.286647] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.286653] pci 0000:00:1c.2: setting latency timer to 64
[    0.286664] pci 0000:00:1e.0: setting latency timer to 64
[    0.286670] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.286673] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.286676] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.286679] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.286682] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.286684] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.286687] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.286690] pci_bus 0000:00: resource 11 [mem 0x80000000-0xdfffffff]
[    0.286693] pci_bus 0000:00: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.286696] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.286698] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.286701] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.286704] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.286707] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.286710] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.286713] pci_bus 0000:08: resource 0 [io  0x4000-0x4fff]
[    0.286716] pci_bus 0000:08: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.286719] pci_bus 0000:08: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.286722] pci_bus 0000:10: resource 4 [io  0x0000-0x0cf7]
[    0.286724] pci_bus 0000:10: resource 5 [io  0x0d00-0xffff]
[    0.286727] pci_bus 0000:10: resource 6 [mem 0x000a0000-0x000bffff]
[    0.286730] pci_bus 0000:10: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.286733] pci_bus 0000:10: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.286736] pci_bus 0000:10: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.286738] pci_bus 0000:10: resource 10 [mem 0x000dc000-0x000dffff]
[    0.286741] pci_bus 0000:10: resource 11 [mem 0x80000000-0xdfffffff]
[    0.286744] pci_bus 0000:10: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.286810] NET: Registered protocol family 2
[    0.286899] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.287235] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.287899] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.288249] TCP: Hash tables configured (established 131072 bind 65536)
[    0.288252] TCP reno registered
[    0.288257] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.288271] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.288404] NET: Registered protocol family 1
[    0.288429] pci 0000:00:02.0: Boot video device
[    0.288644] PCI: CLS 64 bytes, default 64
[    0.288678] Simple Boot Flag at 0x36 set to 0x1
[    0.288891] cpufreq-nforce2: No nForce2 chipset.
[    0.288926] Scanning for low memory corruption every 60 seconds
[    0.289085] audit: initializing netlink socket (disabled)
[    0.289097] type=2000 audit(1295295153.284:1): initialized
[    0.301063] highmem bounce pool size: 64 pages
[    0.301071] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.302833] VFS: Disk quotas dquot_6.5.2
[    0.302916] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.303638] fuse init (API version 7.14)
[    0.303761] msgmni has been set to 1673
[    0.304117] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.304122] io scheduler noop registered
[    0.304124] io scheduler deadline registered
[    0.304140] io scheduler cfq registered (default)
[    0.304289] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.304349]   alloc irq_desc for 40 on node -1
[    0.304351]   alloc kstat_irqs on node -1
[    0.304366] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.304492] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.304548]   alloc irq_desc for 41 on node -1
[    0.304550]   alloc kstat_irqs on node -1
[    0.304561] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.304679] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.304733]   alloc irq_desc for 42 on node -1
[    0.304735]   alloc kstat_irqs on node -1
[    0.304746] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.304896] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.305013] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.305127] intel_idle: MWAIT substates: 0x1110
[    0.305130] intel_idle: does not run on family 6 model 15
[    0.306016] ACPI: AC Adapter [ADP1] (on-line)
[    0.306097] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.306990] ACPI: Lid Switch [LID0]
[    0.307050] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.307056] ACPI: Sleep Button [SLPB]
[    0.307128] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.307132] ACPI: Power Button [PWRF]
[    0.307457] ACPI: acpi_idle registered with cpuidle
[    0.315815] Monitor-Mwait will be used to enter C-1 state
[    0.315882] Monitor-Mwait will be used to enter C-2 state
[    0.315894] Marking TSC unstable due to TSC halts in idle
[    0.315963] Switching to clocksource hpet
[    0.343635] thermal LNXTHERM:01: registered as thermal_zone0
[    0.343649] ACPI: Thermal Zone [TZS0] (25 C)
[    0.349082] thermal LNXTHERM:02: registered as thermal_zone1
[    0.349095] ACPI: Thermal Zone [TZS1] (30 C)
[    0.349276] ERST: Table is not found!
[    0.349595] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.351413] brd: module loaded
[    0.352100] loop: module loaded
[    0.352346] ata_piix 0000:00:1f.1: version 2.13
[    0.352366]   alloc irq_desc for 19 on node -1
[    0.352369]   alloc kstat_irqs on node -1
[    0.352378] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.352430] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.352541] scsi0 : ata_piix
[    0.352642] scsi1 : ata_piix
[    0.353434] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.353438] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.353833] Fixed MDIO Bus: probed
[    0.353875] PPP generic driver version 2.4.2
[    0.353951] tun: Universal TUN/TAP device driver, 1.6
[    0.353953] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.354060] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.354089] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.354113] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.354118] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.354159] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.354196] ehci_hcd 0000:00:1a.7: debug port 1
[    0.358086] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.358114] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc404800
[    0.362183] isapnp: Scanning for PnP cards...
[    0.364543] ACPI: Battery Slot [BAT0] (battery absent)
[    0.376309] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.376501] hub 1-0:1.0: USB hub found
[    0.376508] hub 1-0:1.0: 4 ports detected
[    0.376612]   alloc irq_desc for 23 on node -1
[    0.376615]   alloc kstat_irqs on node -1
[    0.376624] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.376649] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.376653] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.376709] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.376745] ehci_hcd 0000:00:1d.7: debug port 1
[    0.380637] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.380662] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    0.404105] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.404306] hub 2-0:1.0: USB hub found
[    0.404313] hub 2-0:1.0: 6 ports detected
[    0.404423] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.404444] uhci_hcd: USB Universal Host Controller Interface driver
[    0.404497] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.404507] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.404512] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.404557] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.404608] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.404761] hub 3-0:1.0: USB hub found
[    0.404767] hub 3-0:1.0: 2 ports detected
[    0.404843]   alloc irq_desc for 21 on node -1
[    0.404846]   alloc kstat_irqs on node -1
[    0.404854] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.404861] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.404866] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.404914] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.404955] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.405106] hub 4-0:1.0: USB hub found
[    0.405111] hub 4-0:1.0: 2 ports detected
[    0.405189] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.405196] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.405200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.405238] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.405269] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.405408] hub 5-0:1.0: USB hub found
[    0.405412] hub 5-0:1.0: 2 ports detected
[    0.405487] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.405494] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.405499] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.405538] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.405579] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.405718] hub 6-0:1.0: USB hub found
[    0.405723] hub 6-0:1.0: 2 ports detected
[    0.405795] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.405803] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.405808] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.405850] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.405881] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.406014] hub 7-0:1.0: USB hub found
[    0.406019] hub 7-0:1.0: 2 ports detected
[    0.406172] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.415047] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.429150] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.429166] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.429169] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.429173] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.429176] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.429293] mice: PS/2 mouse device common for all mice
[    0.429462] rtc_cmos 00:07: RTC can wake from S4
[    0.429516] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.429553] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.429695] device-mapper: uevent: version 1.0.3
[    0.455207] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.472040] device-mapper: multipath: version 1.1.1 loaded
[    0.472045] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.472271] EISA: Probing bus 0 at eisa.0
[    0.472275] EISA: Cannot allocate resource for mainboard
[    0.472278] Cannot allocate resource for EISA slot 1
[    0.472280] Cannot allocate resource for EISA slot 2
[    0.472282] Cannot allocate resource for EISA slot 3
[    0.472285] Cannot allocate resource for EISA slot 4
[    0.472287] Cannot allocate resource for EISA slot 5
[    0.472289] Cannot allocate resource for EISA slot 6
[    0.472291] Cannot allocate resource for EISA slot 7
[    0.472294] Cannot allocate resource for EISA slot 8
[    0.472296] EISA: Detected 0 cards.
[    0.492133] cpuidle: using governor ladder
[    0.492231] cpuidle: using governor menu
[    0.492659] TCP cubic registered
[    0.492824] NET: Registered protocol family 10
[    0.493271] lo: Disabled Privacy Extensions
[    0.493557] NET: Registered protocol family 17
[    0.494375] Using IPI No-Shortcut mode
[    0.494496] PM: Resume from disk failed.
[    0.494510] registered taskstats version 1
[    0.494909]   Magic number: 11:535:245
[    0.495022] rtc_cmos 00:07: setting system clock to 2011-01-17 20:12:33 UTC (1295295153)
[    0.495026] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.495028] EDD information not available.
[    0.510294] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.531868] ata1.00: ATAPI: Optiarc DVD RW AD-7590A, 1.41, max UDMA/33
[    0.548405] ata1.00: configured for UDMA/33
[    0.643424] Freeing initrd memory: 15536k freed
[    0.716042] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    0.717153] isapnp: No Plug & Play device found
[    0.722907] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7590A  1.41 PQ: 0 ANSI: 5
[    0.745991] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.745996] Uniform CD-ROM driver Revision: 3.20
[    0.746136] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.746213] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.746292] Freeing unused kernel memory: 684k freed
[    0.746842] Write protecting the kernel text: 4932k
[    0.746904] Write protecting the kernel read-only data: 1976k
[    0.771963] udev[87]: starting version 163
[    0.940283] ahci 0000:00:1f.2: version 3.0
[    0.940307] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.940367]   alloc irq_desc for 43 on node -1
[    0.940370]   alloc kstat_irqs on node -1
[    0.940384] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.940480] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.940484] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    0.940491] ahci 0000:00:1f.2: setting latency timer to 64
[    0.953285] Linux agpgart interface v0.103
[    0.954390] scsi2 : ahci
[    0.955673] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.955705] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.955774] r8169 0000:02:00.0: setting latency timer to 64
[    0.955862]   alloc irq_desc for 44 on node -1
[    0.955864]   alloc kstat_irqs on node -1
[    0.955885] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    0.959644] r8169 0000:02:00.0: eth0: RTL8101e at 0xf8132000, 00:1f:16:00:43:d0, XID 94200000 IRQ 44
[    0.962862] scsi3 : ahci
[    0.963049] scsi4 : ahci
[    0.963250] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 43
[    0.963255] ata4: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 43
[    0.963259] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 43
[    0.963404] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.963915] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    0.969634] Initializing USB Mass Storage driver...
[    0.970376] scsi5 : usb-storage 2-3:1.0
[    0.970563] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.971300] usbcore: registered new interface driver usb-storage
[    0.971304] USB Mass Storage support registered.
[    1.087877] [drm] Initialized drm 1.1.0 20060810
[    1.280037] ata4: SATA link down (SStatus 0 SControl 300)
[    1.280067] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.280990] ata3.00: unexpected _GTF length (8)
[    1.288048] ata5: SATA link down (SStatus 0 SControl 300)
[    1.664136] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.664140] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.665527] ata3.00: unexpected _GTF length (8)
[    1.665763] ata3.00: configured for UDMA/133
[    1.680213] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.680413] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.680452] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.680558] sd 2:0:0:0: [sda] Write Protect is off
[    1.680561] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.680600] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.680929]  sda: sda1 sda2 sda3
[    1.685307] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.715284] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.715291] i915 0000:00:02.0: setting latency timer to 64
[    1.733600]   alloc irq_desc for 45 on node -1
[    1.733605]   alloc kstat_irqs on node -1
[    1.733615] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    1.733630] [drm] set up 7M of stolen space
[    1.839570] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.839890] [drm] initialized overlay support
[    2.224026] Skipping EDID probe due to cached edid
[    2.312740] scsi 5:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0 CCS
[    2.313452] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.314540] sd 5:0:0:0: [sdb] 15360000 512-byte logical blocks: (7.86 GB/7.32 GiB)
[    2.315216] sd 5:0:0:0: [sdb] Write Protect is off
[    2.315220] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.315223] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    2.317589] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    2.317597]  sdb: sdb1 sdb2 sdb3 < sdb5 > sdb4
[    2.322852] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    2.322858] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    2.704390] Console: switching to colour frame buffer device 160x50
[    2.708591] fb0: inteldrmfb frame buffer device
[    2.708593] drm: registered panic notifier
[    2.708597] Slow work thread pool: Starting up
[    2.708687] Slow work thread pool: Ready
[    2.726457] acpi device:03: registered as cooling_device2
[    2.726923] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.727055] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.727183] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.924034] Skipping EDID probe due to cached edid
[    3.415088] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   10.974959] Adding 1678332k swap on /dev/sdb4.  Priority:-1 extents:1 across:1678332k 
[   11.002071] udev[409]: starting version 163
[   11.052611] lp: driver loaded but no devices found
[   11.303596] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   11.401746] type=1400 audit(1295295164.401:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=658 comm="apparmor_parser"
[   11.402548] type=1400 audit(1295295164.401:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=658 comm="apparmor_parser"
[   11.402988] type=1400 audit(1295295164.401:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=658 comm="apparmor_parser"
[   11.419984] cfg80211: Calling CRDA to update world regulatory domain
[   11.508691] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.533959] cfg80211: World regulatory domain updated:
[   11.533963]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.533967]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.533971]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.533974]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.533977]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.533981]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.559914] ath5k 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.559931] ath5k 0000:08:00.0: setting latency timer to 64
[   11.560051] ath5k 0000:08:00.0: registered as 'phy0'
[   11.777114]   alloc irq_desc for 22 on node -1
[   11.777118]   alloc kstat_irqs on node -1
[   11.777127] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.777196]   alloc irq_desc for 46 on node -1
[   11.777198]   alloc kstat_irqs on node -1
[   11.777211] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   11.777254] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.834279] hda_codec: ALC268: BIOS auto-probing.
[   12.057239] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1280b1, caps: 0xa04711/0xa04000/0x0
[   12.063302] ath: EEPROM regdomain: 0x30
[   12.063304] ath: EEPROM indicates we should expect a direct regpair map
[   12.063308] ath: Country alpha2 being used: AM
[   12.063310] ath: Regpair used: 0x30
[   12.074284] phy0: Selected rate control algorithm 'minstrel'
[   12.075092] Registered led device: ath5k-phy0::rx
[   12.075117] Registered led device: ath5k-phy0::tx
[   12.075121] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   12.075285] cfg80211: Calling CRDA for country: AM
[   12.081888] cfg80211: Regulatory domain changed to country: AM
[   12.081893]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.081896]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   12.081899]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   12.081902]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   12.106547] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[   13.013795] ppdev: user-space parallel port driver
[   13.016296] type=1400 audit(1295295166.017:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=981 comm="apparmor_parser"
[   13.022746] type=1400 audit(1295295166.021:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=980 comm="apparmor_parser"
[   13.024357] type=1400 audit(1295295166.025:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=981 comm="apparmor_parser"
[   13.024820] type=1400 audit(1295295166.025:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=981 comm="apparmor_parser"
[   13.055617] type=1400 audit(1295295166.053:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=985 comm="apparmor_parser"
[   13.056967] r8169 0000:02:00.0: eth0: link up
[   13.056975] r8169 0000:02:00.0: eth0: link up
[   13.071503] type=1400 audit(1295295166.069:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=991 comm="apparmor_parser"
[   13.072561] type=1400 audit(1295295166.073:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=991 comm="apparmor_parser"
[   13.100448] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.252195] Skipping EDID probe due to cached edid
[   13.609120] Skipping EDID probe due to cached edid
[   23.672029] eth0: no IPv6 routers present
[   52.712107] Skipping EDID probe due to cached edid
[   53.072043] Skipping EDID probe due to cached edid
[   53.809038] Skipping EDID probe due to cached edid
[   54.180026] Skipping EDID probe due to cached edid
[   68.745673] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
[  118.933574] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
[  131.833763] padlock: VIA PadLock not detected.
[  145.293082] Skipping EDID probe due to cached edid
[  145.656116] Skipping EDID probe due to cached edid
[  146.020070] Skipping EDID probe due to cached edid
[  146.385069] Skipping EDID probe due to cached edid
[  159.088060] Skipping EDID probe due to cached edid
[ 3322.316082] Skipping EDID probe due to cached edid
[ 4546.425458] show_signal_msg: 9 callbacks suppressed
[ 4546.425470] dsyslog[2364]: segfault at 0 ip 00ae3330 sp bfdce7ec error 4 in libc-2.12.1.so[9ff000+157000]
[ 7023.636108] Skipping EDID probe due to cached edid
[10581.089094] Skipping EDID probe due to cached edid
[10613.448068] Skipping EDID probe due to cached edid
[10858.698487] ptrace of non-child pid 1772 was attempted by: firefox-bin (pid 3245)
[10858.698495] ptrace of non-child pid 1778 was attempted by: firefox-bin (pid 3245)
[10858.698501] ptrace of non-child pid 1793 was attempted by: firefox-bin (pid 3245)
[10858.698506] ptrace of non-child pid 1794 was attempted by: firefox-bin (pid 3245)
[10858.698510] ptrace of non-child pid 1795 was attempted by: firefox-bin (pid 3245)
[10858.698515] ptrace of non-child pid 1796 was attempted by: firefox-bin (pid 3245)
[10858.698520] ptrace of non-child pid 1807 was attempted by: firefox-bin (pid 3245)
[10858.698525] ptrace of non-child pid 1842 was attempted by: firefox-bin (pid 3245)
[10858.698531] ptrace of non-child pid 1851 was attempted by: firefox-bin (pid 3245)
[10858.698537] ptrace of non-child pid 1852 was attempted by: firefox-bin (pid 3245)
[11240.740138] Skipping EDID probe due to cached edid

```
It is happening to me on Firefox 3.6.10, I would be just browsing the Internet or w/e and would freeze and then unfreeze. 
I haven't noticed Ubuntu to be lag when I resume from sleep.

---

