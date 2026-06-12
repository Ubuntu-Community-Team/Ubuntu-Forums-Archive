---
title: "PCI - SATA controler problem"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by naelya on 2010-12-27
Hello,

I am an absolute beginner here so please excuse the lack of details due to the fact that I do not really know where to begin from.

The objective is very simple here. I am trying to add a SATA new hard drive to my OLD pc which is running Ubuntu 10.10 with no luck.

The Disk is not mounted automatically, and not even detected by GParted.

I found an interesting message in dmseg which says SATA Link down as shown below:

```
1.716743] sata_via 0000:00:0d.0: version 2.6
[    1.716786] sata_via 0000:00:0d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.716990] sata_via 0000:00:0d.0: routed to hard irq line 11
[    1.734509] scsi2 : sata_via
[    1.744393] scsi3 : sata_via
[    1.746930] scsi4 : sata_via
[    1.747141] ata3: SATA max UDMA/133 port i16@0xc400 bmdma 0xd400 irq 11
[    1.747203] ata4: SATA max UDMA/133 port i16@0xc800 bmdma 0xd408 irq 11
[    1.747261] ata5: PATA max UDMA/133 port i16@0xcc00 bmdma 0xd410 irq 11
[    1.747429] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.876633] ata1.00: ATA-6: ST340810A, 3.99, max UDMA/100
[    1.876704] ata1.00: 78165360 sectors, multi 16: LBA 
[    1.876797] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.892471] ata1.00: configured for UDMA/33
[    1.892807] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        3.99 PQ: 0 ANSI: 5
[    1.893293] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.894129] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.894306] sd 0:0:0:0: [sda] Write Protect is off
[    1.894364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.894406] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.894815]  sda: sda1 sda2 < sda5 >
[    1.966542] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.078836] ata3: SATA link down (SStatus 0 SControl 310)
[    2.406842] ata4: SATA link down (SStatus 0 SControl 310)
```

I hope I didn't post to many unnecessary lines.
I am totally desperate for a solution here especially that I've been fighting with this problem for a very long time.

Anyone's got ideas, please let me know.

Thanks.

---

### Post by khelben1979 on 2010-12-27
Type **lspci** from a text console and put the information in this thread. It will give us some information about your hardware, and especially what kind of SATA chipset which Ubuntu has problems with in this case.

You should also check your BIOS settings to make sure that SATA chipset is enabled in there, otherwise Ubuntu has no way of detecting your new SATA harddrive.

---

### Post by naelya on 2010-12-27
Hello!

Thank you so much for your quick response.
Below is the output of lspci:

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

In regards to the BIOS I could not find anything related to SATA. I must also mention that I do not have native SATA ports on my motherboard. I actually had to add a PCI - SATA controller in order to connect the disk.
My BIOS is (phoenix award v6.00pg)

Please let me know if you need any further information, and I am looking forward to hearing from you soon.

Thanks.

---

### Post by amsterdamharu on 2010-12-27
[http://ubuntuforums.org/archive/index.php/t-1400996.html](http://ubuntuforums.org/archive/index.php/t-1400996.html)
Could you try the following?
Press alt + F2, type "gksu gedit /etc/default/grub" press run.
Replace the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
with
```
GRUB_CMDLINE_LINUX_DEFAULT="pci=nomsi"
```
Later you can add quiet nosplash again but for now this might give you more output while booting.
Save the file and open a terminal; press alt + F2, type gnome-terminal and click run
Copy and paste the following command in the terminal:
```
sudo update-grub
```

Now reboot and see if that solved the problem.

---

### Post by khelben1979 on 2010-12-27
From [this webpage]("http://www.via.com.tw/en/products/peripherals/serial-ata_raid/vt6421/") I can see your SATA controller card.

The next step now is to make the Linux kernel recoqnize it and for that it needs to be compiled in your Linux kernel. If the support is already there, then the module for the kernel driver needs to get loaded. Once the proper kernel module has been identified, it can be loaded by using the **modprobe** command.

I also made a google search and found a driver for your controller card over at [this webpage]("http://driverscollection.com/?H=VT6421&By=VIA&SS=Linux"). So you can take a look at that! :)

---

### Post by MartyBuntu on 2010-12-27
FWIW, I never had problems with VIA controller cards being instantly recognised by Ubuntu.

Have you tried a different PCI slot?

---

### Post by naelya on 2010-12-28
Thank you for your suggestion "amsterdamharu" however it did not change anything :(

Any other ideas?

Regards.

---

### Post by naelya on 2010-12-28
Hello "khelben1979"

What you've suggested sounds very interesting. However being the beginner I am.. I guess I would destroy the whole thing.
What are the chances I can get a step by step guide on this subject?!
The other thought that comes to my mind. How would the new system behave with system updates, and upgrades?! Am I going to have to recompile the kernel every time the kernel is updated?

I appreciate your input, and I am looking forward to hearing from you soon.

Thanks.

---

### Post by naelya on 2010-12-28
> **MartyBuntu said:**
> FWIW, I never had problems with VIA controller cards being instantly recognised by Ubuntu.

Have you tried a different PCI slot?

Hello,

In fact I didn't. However I will do this later on today and I will let you know how it goes.

Thanks!

---

### Post by naelya on 2010-12-28
Hello,

I have done a little experiment and it showed an interesting result.

I connected a Hitachi Deskstar 7K1000.B 1 TB (HDT721010SLA360) to the same PC in question. Ubuntu actually detected the disk and mounted it automatically.

However the disk I wish to connect is a Seagate Barracuda 7200.12 SATA 3Gb/s 500GB (ST3500418AS).

Would these findings change anything? Is there a chance that the disk is not compatible with the PCI SATA controller?

Any thoughts?

Regards,

---

### Post by khelben1979 on 2010-12-28
I think I know what the problem is. The Seagate Barracuda harddrive is configured to use a [SATA II]("http://en.wikipedia.org/wiki/Serial_ATA#SATA_Revision_2.0_.28SATA_3_Gbit.2Fs.29") interface and if the SATA harddrive isn't backward compatible with the older SATA interface, it will not work.

Western Digital SATA harddrives is often backward compatible with it's older SATA interface.

---

### Post by inobe on 2010-12-28
is their a jumper setting for backwards compatibility, not sure for that particular model ?

---

### Post by naelya on 2010-12-28
> **khelben1979 said:**
> I think I know what the problem is. The Seagate Barracuda harddrive is configured to use a [SATA II]("http://en.wikipedia.org/wiki/Serial_ATA#SATA_Revision_2.0_.28SATA_3_Gbit.2Fs.29") interface and if the SATA harddrive isn't backward compatible with the older SATA interface, it will not work.

Western Digital SATA harddrives is often backward compatible with it's older SATA interface.

> **inobe said:**
> is their a jumper setting for backwards compatibility, not sure for that particular model ?

According to the Seagate disk [[COLOR="Blue"]specs[/COLOR]]("http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%207200.12/100529369h.pdf") there is jumper to limit transfer speed from 3.0 Gbits/sec to 1.5 Gbits/sec. 
However I do not know if SATA II to SATA for example! or is it something totally different.
having said that, I will try setting the jumper and checking the effect of that as soon as possible, and I will let you know.

thank you.

---

### Post by naelya on 2010-12-28
Hello,

The usage of a jumper to limit the speed of the disk did not fix the problem.
So the question now is. What is next?


dmesg | grep SATA
returns the following:

[    1.751652] ata3: SATA max UDMA/133 port i16@0xc400 bmdma 0xd400 irq 11
[    1.751713] ata4: SATA max UDMA/133 port i16@0xc800 bmdma 0xd408 irq 11
[    2.082837] ata3: SATA link down (SStatus 0 SControl 310)
[    2.410843] ata4: SATA link down (SStatus 0 SControl 310)

and lspci returns:


00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


Any thoughts?!

Regards.

---

### Post by naelya on 2011-01-10
Hello,

After all the problem was very simple.

Seagate Barracuda 7200.12 SATA 3Gb/s 500GB (ST3500418AS) uses SATA II only and it is not backwards compatible.

I changed my motherboard and it works like a charm.

Thank you all.

---

