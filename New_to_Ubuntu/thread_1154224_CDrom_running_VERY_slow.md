---
title: "CDrom running VERY slow"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by servicetech on 2009-05-09
I'm suspecting a DMA/Driver problem, the hardware works fine under windows.
CPU use is 80% doing a direct copy from one cd to another. Using IDE drives. 
SATA hard drive seems to be OK

---

### Post by servicetech on 2009-05-09
**I dug around looking for terminal commands and found this test command:**
dmesg | grep ata

**Results are:**
[    0.000000]  BIOS-e820: 000000006fde3000 - 000000006fdf0000 (ACPI data)
[    0.000000]  modified: 000000006fde3000 - 000000006fdf0000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.004000] Memory: 1792092k/1832832k available (4126k kernel code, 39364k reserved, 2208k data, 532k init, 927624k highmem)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.406082] libata version 3.00 loaded.
[    1.458810] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 2301
[    1.458813] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 2301
[    1.458816] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 2301
[    1.458819] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 2301
[    1.940017] ata1: softreset failed (device not ready)
[    1.940052] ata1: failed due to HW bug, retry pmp=0
[    2.104028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.104705] ata1.00: ATA-8: WDC WD5000AAKS-65A7B0, 01.03B01, max UDMA/133
[    2.104708] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.105465] ata1.00: configured for UDMA/133
[    2.440042] ata2: SATA link down (SStatus 0 SControl 300)
[    2.776030] ata3: SATA link down (SStatus 0 SControl 300)
[    3.112030] ata4: SATA link down (SStatus 0 SControl 300)
[    3.166592] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.166717] scsi4 : pata_atiixp
[    3.166775] scsi5 : pata_atiixp
[    3.167588] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    3.167591] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    4.217514] Write protecting the kernel read-only data: 1532k
[    4.691818] EXT3-fs: mounted filesystem with ordered data mode.

**I dunno if that actually means anything to anybody. The part that concerned me is:**

[    1.940017] ata1: softreset failed (device not ready)
[    1.940052] ata1: failed due to HW bug, retry pmp=0

**Is my motherboard just not Linux compatible? It's a Gigabyte GA-MA74GM-S2 rev 1.0, no Linux drivers are listed on Gigabytes website, they basically say you're on your own with Linux.**

---

### Post by servicetech on 2009-05-10
I did a search on the ata1 softreset thing and apparently it's a south bridge driver problem. Of course ATI/AMD doesn't have a Linux driver for the SB700. I'm not buying/recommending ANY ATI/AMD products until they start offering better driver support. My Nvidia box was MUCH easier to set up for Linux.

---

### Post by Didius Falco on 2009-05-10
I'm getting the "ATA3 soft Reset" error at every boot, and I've done everything I can to fix it - updated the bios to the latest version, changed the bios settings from AHCI to IDE - nothing helps.

My CD Rom is acting goofy too - I even switched a known-to-be working one in and had the same problem. I can burn CDs that work, but it always throws up random errors. Burning DVDs just doesn't work.

I'm running a Gigabyte MA790GP-DS4H motherboard.

---

### Post by wpshooter on 2009-05-10
> **Didius Falco said:**
> I'm getting the "ATA3 soft Reset" error at every boot, and I've done everything I can to fix it - updated the bios to the latest version, changed the bios settings from AHCI to IDE - nothing helps.

My CD Rom is acting goofy too - I even switched a known-to-be working one in and had the same problem. I can burn CDs that work, but it always throws up random errors. Burning DVDs just doesn't work.

I'm running a Gigabyte MA790GP-DS4H motherboard.

Do you have the latest & greatest FIRMWARE installed on your CD drive ?

---

### Post by servicetech on 2009-05-10
I'm also running a Gigabyte motherboard GA-MA74GM-S2. I tried unhooking the DVD Rom drives and still get the ata1 softreset error, I'm suspecting is some type of IDE controller issue. Interestingly enough the SATA Hard drive works fine. I might try IDE hard drive and see what happens.

Both of my DVD Rom drives worked fine with my old ASUS Nforce2 motherboard with Ubuntu 9.04 (same as I'm running now), I doubt it a drive firmware issue.

---

### Post by Didius Falco on 2009-05-10
Just to be sure, I went and tried to find one for my 2 year old AOpen DSW2012P CD/DVD RW (rebranded, I'm sure) drive.

No firmware ever produced for it that I can find. While I had it out of the case, I did change the jumper from Master to Cable Select and made it a slave drive. I'll have to check my bios again later and see if that changes the hard drive to Master status, because it has been showing up as a Sata slave...

I never had the problem with the "ataX soft reset" error under 8.10 - for that matter, I still have an active 8.10 install, and it doesn't get the error. I'm hoping that a future kernel update will solve it.

I'm also going to pick up a new CD/DVD burner in the next couple of days, and make sure I get a Sata one this time.

I'm also contemplating wiping and reinstalling my Win Xp install so I can install a Sata driver this time and just leave the Bios set to AHCI all the time.

Still, all in all, it isn't that big of a problem...

Regards,

Didius

---

### Post by servicetech on 2009-05-10
I hooked up an IDE hard drive and got 40MB/s transfer rate to the SATA drive at 65% CPU utilization (AMD 4850e dual core.) A 14GB file transfered in 8 minutes, fast enough for me considering one drive is IDE. It's the high CPU utilization that I'm most concerned about.

---

