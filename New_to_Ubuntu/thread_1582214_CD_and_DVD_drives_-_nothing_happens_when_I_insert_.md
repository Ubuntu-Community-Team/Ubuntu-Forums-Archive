---
title: "CD and DVD drives - nothing happens when I insert a disk"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by LiSrt on 2010-09-26
I've just started using Ubuntu (Kubuntu specifically) and have a problem with CDs/DVDs, specifically mounting them.

They never auto mount (i.e. when I insert a disk nothing appears in the device notifier icon in the system tray).

They sometimes mount, but only if I issue the mount command a few minutes after boot.

my /etc/fstab is:
```
UUID=78bc85f1-628a-4256-ba8d-ecc3c8698379       swap            swap                    sw                    0 0
UUID=f316760f-e99d-41ac-ab16-64c66299106b       /               ext3                    defaults              0 1
UUID=09850ab4-7b95-4bab-94e9-9d4320e5b5cf       /home           reiserfs                defaults              1 2
/dev/sr0                                        /media/cdrom    auto,iso9660            noauto,ro,users,exec  0 0
/dev/sr1                                        /media/CDRW_DVD auto,udf,iso9660        noauto,ro,users,exec  0 0

```the commands I try to mount them with are:

mount /media/cdrom
with result:
mount: no medium found on /dev/sr0

or

mount /media/CDRW_DVD
with result:
mount: no medium found on /dev/sr1

If it's a few minutes after booting, the DVD drive works, and then I can watch dvds in vlc.

It all seemed to work fine on Mandriva, can anyone let me know what I should do to get this working on (k)ubuntu?

thanks

---

### Post by P4man on 2010-09-26
Have a look in the output of dmesg. That may shed some light on the issue. Other things that come to mind are experimenting with AHCI (I think) settings in the bios, if its a sata cdrom. If all else fails, see if you can update the dvd writer's firmware.

---

### Post by LiSrt on 2010-09-29
I think this is the relevant part of all the information that the dmesg command dumps to the screen...

```
[58914.040018] ata3: lost interrupt (Status 0x58)
[58914.040046] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[58914.040051] sr 2:0:0:0: [sr0] CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[58914.040063] ata3.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[58914.040065]          res 58/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x6 (timeout)
[58914.040067] ata3.00: status: { DRDY DRQ }
[58914.040087] ata3: soft resetting link
[58914.340683] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58914.340687] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58914.360352] ata3.00: configured for UDMA/33
[58914.400230] ata3.01: configured for UDMA/33
[58919.400025] ata3.00: qc timeout (cmd 0xa0)
[58919.400031] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[58919.400052] ata3: soft resetting link
[58919.700693] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58919.700698] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58919.720360] ata3.00: configured for UDMA/33
[58919.760232] ata3.01: configured for UDMA/33
[58924.760026] ata3.00: qc timeout (cmd 0xa0)
[58924.760032] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[58924.760036] ata3.00: limiting speed to UDMA/33:PIO3
[58924.760056] ata3: soft resetting link
[58925.080300] ata3: nv_mode_filter: 0x738f&0x739f->0x738f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58925.080304] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58925.100359] ata3.00: configured for UDMA/33
[58925.140233] ata3.01: configured for UDMA/33
[58930.140023] ata3.00: qc timeout (cmd 0xa0)
[58930.140028] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[58930.140030] ata3.00: disabled
[58930.140036] ata3.01: TEST_UNIT_READY failed (err_mask=0x40)
[58930.140052] ata3: soft resetting link
[58930.440301] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58930.480228] ata3.01: configured for UDMA/33
[58935.480025] ata3.01: qc timeout (cmd 0xa0)
[58935.480031] ata3.01: TEST_UNIT_READY failed (err_mask=0x4)
[58935.480036] ata3.01: limiting speed to UDMA/33:PIO3
[58935.480056] ata3: soft resetting link
[58935.780307] ata3: nv_mode_filter: 0x738f&0x739f->0x738f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[58935.820233] ata3.01: configured for UDMA/33
[58940.820025] ata3.01: qc timeout (cmd 0xa0)
[58940.820032] ata3.01: TEST_UNIT_READY failed (err_mask=0x4)
[58940.820035] ata3.01: disabled
[58940.820063] ata3: soft resetting link
[58941.100084] ata3: EH complete
[58941.100186] VFS: busy inodes on changed media or resized disk sr0
[58941.104070] VFS: busy inodes on changed media or resized disk sr0
[58941.104162] VFS: busy inodes on changed media or resized disk sr0
[58941.183290] VFS: busy inodes on changed media or resized disk sr0
[58941.200057] VFS: busy inodes on changed media or resized disk sr0
[58941.200104] VFS: busy inodes on changed media or resized disk sr0
[58941.244030] VFS: busy inodes on changed media or resized disk sr0
[58941.244288] VFS: busy inodes on changed media or resized disk sr0
[58941.244400] VFS: busy inodes on changed media or resized disk sr0
[58941.415655] VFS: busy inodes on changed media or resized disk sr1
[58941.415785] VFS: busy inodes on changed media or resized disk sr1
[58941.415836] VFS: busy inodes on changed media or resized disk sr1
[58941.415882] VFS: busy inodes on changed media or resized disk sr1
[58941.415986] VFS: busy inodes on changed media or resized disk sr1
[58941.417445] VFS: busy inodes on changed media or resized disk sr1
```I have very little idea of what this all means though - I googled the inodes message but that seemed to suggest the problem was ejecting without umounting - which I didn't do. :confused:

---

### Post by P4man on 2010-09-29
Looks very similar to this issue:
[https://bugs.launchpad.net/ubuntu/+bug/576496](https://bugs.launchpad.net/ubuntu/+bug/576496)

Is that also an nvidia chipset you have?

You might want to give the 32 bit version of ubuntu a try (im assuming you are running the AMD64), and you may still try what I suggested above, play with BIOS settings for your sata controller.

---

### Post by lumore22 on 2010-09-29
Greetings-

I had a similar problem. I'm on Windows 7 dual boot w/ ubuntu Lucid Lynx. When I first loaded ubuntu on, all my devices worked. But as I installed additional software and  upgrades, somehow the drivers controlling the cd/dvd player were damaged/overwritten.

After much time spent on diagnostics, I inserted the original boot cd, and restored the drivers. All was fine after that. 
. 
There are apparently unknown dependencies among different software packages and upgrades that are available for Linux systems. So . . . don't waste too much time on this.

But it would be interesting and helpful to document what you did prior to the cd/dvd driver failure, for future reference. 

Can't stress enough that one should always document all events on *nix systems.

Regards

---

### Post by lumore22 on 2010-09-29
Oops - forgot to mention something about the dvd movie player Totem. If you are using Totem, look up all the threads on totem. I use rhythmbox which always worked fine. BUt I also did have totem-specific issues. Be sure you have all the codecs/ restricted extras installed. After installation, you still have to activate them. 

But for startes read up about totem and access the totem web page. 


Regards again

---

### Post by LiSrt on 2010-09-29
Thanks - that sounds exactly like what's happening to me - with occasional mouse pointer freezing as well.

Doubt I'll be going back to 32 bit though, I'll wait to see if Ubuntu get this sorted otherwise it's another distro for me. :neutral:

(unsure if this is significant - both my cd and dvd drive have IDE connections, not SATA - would this affect things in any way?)

---

### Post by P4man on 2010-09-29
> **LiSrt said:**
> 
(unsure if this is significant - both my cd and dvd drive have IDE connections, not SATA - would this affect things in any way?)

Well, clearly the kernel has problems communicating with the dvd drive. Note the "lost interrupt" on the first line of your log. It actually looks like a good old interrupt conflict? Does your bios have an option to assign an interrupt to the IDE controller?

I also recall nVidia nForce chipsets for AMD cpu's were notoriously buggy and had serious issues with IDE/SATA and data corruption. Is that by any chance what you have?

Last thought; it could just be a bad IDE cable. Although I wouldnt expect that to behave so predictable. Still wouldnt hurt swapping the cable  if you have a spare, or change master/slave or IDE channel.

---

### Post by P4man on 2010-09-29
Oops, its not just the chipsets for AMD. The intel ones had their issues too:
[http://www.theinquirer.net/inquirer/news/1009010/nforce-chipset-corruption](http://www.theinquirer.net/inquirer/news/1009010/nforce-chipset-corruption)

See if you can update your bios if you have an nForce board.

---

### Post by andrewthomas on 2010-09-29
> **LiSrt said:**
> 

my /etc/fstab is:
```
UUID=78bc85f1-628a-4256-ba8d-ecc3c8698379       swap            swap                    sw                    0 0
UUID=f316760f-e99d-41ac-ab16-64c66299106b       /               ext3                    defaults              0 1
UUID=09850ab4-7b95-4bab-94e9-9d4320e5b5cf       /home           reiserfs                defaults              1 2
[B]/dev/sr0                                        /media/cdrom    auto,iso9660            noauto,ro,users,exec  0 0
/dev/sr1                                        /media/CDRW_DVD auto,udf,iso9660        noauto,ro,users,exec  0 0[/B]

```
thanks
Get rid of those** /dev/sr0  & /dev/sr1 lines** and you will be fine.

---

### Post by LiSrt on 2010-10-06
Thanks to P4man and andrewthomas!

I removed the lines in fstab, which means the optical drives now work without having to be explicitly mounted.

Last night I updated the board's BIOS, too early to say if this has worked, but if it does I'll update the thread.

(no mouse freezing or wifi drops since either)

---

### Post by LiSrt on 2010-10-18
I think the main problem here was due to Ubuntu 10.04 - the BIOS update didn't solve the random drive unmounting, but changing to Ubuntu 10.10 did work.

---

