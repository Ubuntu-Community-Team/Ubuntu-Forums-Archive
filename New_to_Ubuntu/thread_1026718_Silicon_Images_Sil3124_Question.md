---
title: "Silicon Images Sil3124 Question"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by amp88 on 2008-12-31
Hi. I have a few questions centering around using a Silicon Images Sil3124 based RAID controller with Ubuntu 8.10. The first question (and most important) is that I have some existing volumes defined in the array with a lot of data on them. They were created using the SATA RAID Manager in a Windows environment (XP SP2). If I can get the card working properly in Ubuntu will I be able to use the existing volumes without losing any data?

If the above is true then read on, if it's not then stop here ;)

I've read some very confusing and conflicting information when it comes to the Sil3124 drivers and SATA RAID Manager software in Linux. The [User Guide](http://www.siliconimage.com/docs/SATARAID5-UserGuide_v1.30.pdf) has a section on using the RAID Manager on a Linux environment, but [drivers](http://www.siliconimage.com/support/searchresults.aspx?pid=27&cat=3&os=1) only seem to be available for a few distributions (not including Ubuntu). I've also found something called [libATA](http://linux-ata.org/faq.html) which looks like it has support for the Sil3124 in all distros of linux. Put simply I'm very confused with this whole situation. I've done quite a bit of research but I have yet to find definitive answers to the questions above.

Can anyone please answer the questions and/or point me in the direction of some sort of guide/tutorial to getting things working? I'd really appreciate it.

Thanks, Gus.

---

### Post by amp88 on 2009-01-01
I've installed the hwinfo package and looking at the output from hwinfo --storage it looks as though the system recognises the card:

```

09: PCI 406.0: 0104 RAID bus controller                         
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1095_3124
  Unique ID: +QnG.FE9tEZ91SW0
  Parent ID: qscc.ULOo3yhA66C
  SysFS ID: /devices/pci0000:00/0000:00:14.4/0000:04:06.0
  SysFS BusID: 0000:04:06.0
  Hardware Class: storage
  Model: "Silicon Image SiI 3124 PCI-X Serial ATA Controller"
  Vendor: pci 0x1095 "Silicon Image, Inc."
  Device: pci 0x3124 "SiI 3124 PCI-X Serial ATA Controller"
  SubVendor: pci 0x1095 "Silicon Image, Inc."
  SubDevice: pci 0x7124 
  Revision: 0x02
  Driver: "sata_sil24"
  Driver Modules: "sata_sil24"
  Memory Range: 0xfbfffc00-0xfbfffc7f (rw,non-prefetchable)
  Memory Range: 0xfbff0000-0xfbff7fff (rw,non-prefetchable)
  I/O Ports: 0xec00-0xec0f (rw)
  Memory Range: 0x80000000-0x8007ffff (ro,prefetchable,disabled)
  IRQ: 20 (no events)
  Module Alias: "pci:v00001095d00003124sv00001095sd00007124bc01sc04i00"
  Driver Info #0:
    Driver Status: sata_sil24 is active
    Driver Activation Cmd: "modprobe sata_sil24"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)

```

I'm just making very slow progress on my own and I'm worried that I might lose the data on the array if I keep blundering about. Reading up only gets you so far...there are plenty of incomplete guides that don't take into account what could go wrong when you're following them through. Please help me :)

---

### Post by Cracauer on 2009-01-01
It doesn't directly answer your question, but unless you want to run raid-0 I cannot recommend that you use any of that onboard SATA raid stuff. The recovery in case of an error is complicated enough for one dedicated RAID system, but in the case of these things you have them twice, once in the BIOS, once in the driver at runtime. Forums are full of reports of recovery failing (read: wipe out the good drive left over when one drive fails in a raid-1) when a reboot happens during recovery or something similar.

On the other hand, Linux' md driver (real software raid) is one of the finest pieces of Linux software and gets your behind out of the wheelbarrow all the time.

In addition to the better chance of recovery it has more advantages such as not limiting you which drives you can smack into the array. This can be a real-world data saver, too.

---

### Post by amp88 on 2009-01-01
> **Cracauer said:**
> It doesn't directly answer your question, but unless you want to run raid-0 I cannot recommend that you use any of that onboard SATA raid stuff. The recovery in case of an error is complicated enough for one dedicated RAID system, but in the case of these things you have them twice, once in the BIOS, once in the driver at runtime. Forums are full of reports of recovery failing (read: wipe out the good drive left over when one drive fails in a raid-1) when a reboot happens during recovery or something similar.

On the other hand, Linux' md driver (real software raid) is one of the finest pieces of Linux software and gets your behind out of the wheelbarrow all the time.

In addition to the better chance of recovery it has more advantages such as not limiting you which drives you can smack into the array. This can be a real-world data saver, too.

I already have 3 Raid5 NTFS volumes which were created through Windows on the RAID enclosure I intend to use with this card. I need to know if I can use these volumes in Linux as they are just now (i.e. I cannot copy the data off and rebuild new volumes for the data).

---

### Post by Cracauer on 2009-01-02
Did you ever simulate a fail and see how it recovers?

---

### Post by amp88 on 2009-01-02
> **Cracauer said:**
> Did you ever simulate a fail and see how it recovers?

No. I want to know if I can use the existing volumes in Linux. I'm not looking for a debate on the relative pros and cons of different setups. I have what I have and it's not going to change... :)

---

### Post by amp88 on 2009-01-03
Bump.

---

### Post by Cracauer on 2009-01-03
All right. I am not endorsing using this kind of RAID, but when it comes to drivers for using it:

you need to track down whether a driver for this is in the mainline kernel. Even if you want to use this kind of RAID, using a random binary driver downloaded from a non-Linux vendor is increasing your risk.

You should consult the libata documentation and see whether this chip is supported. You need to find out whether sil actually makes their own driver (unlikely) or just packages an existing driver, which is more likely and better for you. 

If the latter, then start using a kernel which has the driver put in by Linus. If you don't do that, a bad Linux driver might nuke your whole raid including the Windoze partitions.

---

### Post by amp88 on 2009-01-03
> **Cracauer said:**
> 
you need to track down whether a driver for this is in the mainline kernel. Even if you want to use this kind of RAID, using a random binary driver downloaded from a non-Linux vendor is increasing your risk.

You should consult the libata documentation and see whether this chip is supported. You need to find out whether sil actually makes their own driver (unlikely) or just packages an existing driver, which is more likely and better for you. 

Judging by the following quote on the [libATA driver status page](http://linux-ata.org/driver-status.html) I think driver support should be in Ubuntu 8.10:

[quote=libATA Page]This status report applies to the latest SATA driver release, found in kernels >= 2.6.18-git5 (i.e. what will be 2.6.19).[/quote]

[This](http://linux-ata.org/driver-status.html#sii3124) also seems suggest that the Sil3124 is supported by libATA.

The [User Guide](http://www.siliconimage.com/docs/SATARAID5-UserGuide_v1.60.pdf) for the SATA RAID Manager says the following: 

[quote=User Guide]
On a Linux system the SATARAID5 Manager and daemon can be installed into any subdirectory. Before launching the SATARAID5 Manager, the driver must be installed and the daemon must be running in background. If you are using a bootable version of the SATARAID5 driver, it is already included in your Linux kernel. If you are not using a bootable version of the SATARAID5 driver, you must manually load the driver by typing the following command:
• insmod si3XXXr5.ko (where “3XXX” refers to your specific SATA controller chip)
Then, the daemon must be started. If the daemon has been incorporated into the startup scripts (typically included within the /etc/rc directory structure, it will start automatically when you boot your system. Otherwise, you must manually start the daemon in a background mode by typing the following command:
• ./SATARaid5ConfigServer &
Finally, you can launch the SATARAID Manager by typing the following command:
• java –jar SATARaid5Manager
[/quote]

However, I can't find the package containing the deamon and RAID manager for Linux anywhere on the Silicon Image site. If you go to their [main support page](http://www.siliconimage.com/support/index.aspx), select the Sil3124 from the first drop down and select SATA Raid Tools from the second drop down, the third drop down (the one to select the OS) doesn't have an entry for Linux. There is a note saying "Any operating system not listed above is not supported.", but this is clearly in contradiction to the User Guide quote above. I just don't know where to go with this...

---

### Post by lummie on 2009-02-17
How did you get on ?  Have you got the controller running in ubuntu yet ?

I was looking to buy one of these [http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html#a15](http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html#a15) which has the same controller and sticking ubuntu server on it.

Is the general consensus to forget the hardware raid and use the linux software raid ?  Will this not impact the raids performance ? What is the advantage over the hardware raid ?

regards,

Matt

---

### Post by amp88 on 2009-02-17
I ended up just going back to Windows. However, someone else contacted me by PM a few days ago and they're still investigating getting the card working with Linux (openSUSE 11.1 though). I haven't got an update on their progress yet.

---

### Post by BikeHelmet on 2009-04-09
I'm considering buying a card with this controller.

I'm a bit sketchy on how this driver stuff works in Linux. If it's in the kernel, then we don't really need drivers from the manufacturer, right?

And the RAID tool can be taken from the [Fedora/RHEL drivers]("http://www.siliconimage.com/support/searchresults.aspx?pid=27&cat=3"), possibly?

I don't have enough ports, so I need to buy a card regardless. I'd prefer to get one with decent support under many different operating systems - but primarily Linux/Ubuntu. From the sound of it I should be looking at a different card?

---

### Post by Cracauer on 2009-04-09
> **BikeHelmet said:**
> I'm considering buying a card with this controller.

I'm a bit sketchy on how this driver stuff works in Linux. If it's in the kernel, then we don't really need drivers from the manufacturer, right?

And the RAID tool can be taken from the [Fedora/RHEL drivers]("http://www.siliconimage.com/support/searchresults.aspx?pid=27&cat=3"), possibly?

I don't have enough ports, so I need to buy a card regardless. I'd prefer to get one with decent support under many different operating systems - but primarily Linux/Ubuntu. From the sound of it I should be looking at a different card?

It certainly isn't a safe solution. If you do this for data redundancy (raid1, raid5 etc) I wouldn't trust anything SIL, NVidia, Via or all that stuff.

Linux' software raid is excellent, and XP has software raid (raid5 only in server variant). Whether the Windoze stuff is any good I don't know. And of course they can't read each other.

---

### Post by BikeHelmet on 2009-04-12
> **Cracauer said:**
> It certainly isn't a safe solution. If you do this for data redundancy (raid1, raid5 etc) I wouldn't trust anything SIL, NVidia, Via or all that stuff.

Linux' software raid is excellent, and XP has software raid (raid5 only in server variant). Whether the Windoze stuff is any good I don't know. And of course they can't read each other.
To use software raid, I need ports - which come on RAID cards - which are usually SiI, VIA, etc.; see my dilemma? :P

I wonder if this would work...
[http://ncix.com/products/index.php?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba](http://ncix.com/products/index.php?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba)

Apparently SiI 3114 has a bug from 2.6.23 to 2.6.25 that results in data corruption. But this bug is only present in fakeraid and libata? Using sata_sil, it apparently works fine.

I may pick one of these up. It's the cheapest card that has ports available. Then I just have to wrap the drives up in software raid, later...

---

### Post by Cracauer on 2009-04-12
> **BikeHelmet said:**
> To use software raid, I need ports - which come on RAID cards - which are usually SiI, VIA, etc.; see my dilemma? :P

I wonder if this would work...
[http://ncix.com/products/index.php?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba](http://ncix.com/products/index.php?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba)

Apparently SiI 3114 has a bug from 2.6.23 to 2.6.25 that results in data corruption. But this bug is only present in fakeraid and libata? Using sata_sil, it apparently works fine.

I may pick one of these up. It's the cheapest card that has ports available. Then I just have to wrap the drives up in software raid, later...

You can use the ports on these cards without using their raid functionality.

In the case of SIL I would doubt the reliability regardless.

I would get something AHCI based.

---

### Post by Master One on 2009-05-20
I am confused about the Sil3124 as well. I was just investigating the following product:

[CENTER][url=http://www.delock.de/produkte/gruppen/pci-express/Delock_Raid_5_PCI_Express_x8_SATA_II_4_x_eSATA_70161.html?setLanguage=EN][img]http://www.delock.de/pictures/products/2/493e56bb70376.jpg[/img]
Delock Raid 5 PCI Express x8 card SATA II > 4 x eSATA[/url][/CENTER]

As you can see on the picture, it even has a fan, so it looks pretty powerful, making me assume, that this is a real hardware RAID controller. According to the Delock support, that card is based on the Sil3124.

If it is just another softraid controller, I don't quite understand the huge difference in price to the 2-port PCI card from Delock, the above shown 4-port PCI Express card is indeed quite expensive, and definitely not worth it, if it is not a real hardware RAID controller.

---

### Post by Sidewinder1 on 2009-05-20
This post is primarily for Master One: I don't use any RAID but my SIL3x12, PCI (not express, I have an older system :-( ) works great with my external hard drives and has 2 eSATA ports which are ahellova lot faster than USB. They work with both Ubuntu and Winbloze. Not sure what your needs may be but figured I'd post for your info; didn't mean to hijack an ageing thread, :-)

HTH,
Side

---

### Post by Master One on 2009-05-20
Yes, I know that both cards (4-port PCI Express & 2-port PCI) based on Sil chips are working under Linux, when accessing the ports individually.

I already have one of that 2-port eSATA PCI card from Delock, and it's working great that way. The 2-port card would also support such a half-baked driver-supported RAID1, but that obviously does not make any sense, if you can also use the superior Linux SoftRAID with mdadm.

That 2-port card was really cheap, but the shown 4-port card costs more than 10 times more, which made me curious, if it's not a real Hardware RAID controller, but again such a half-baked driver supported one.

In the end I'll just buy another 2-port card, which really is worth the money, although 4-ports on one card would have been nice.

---

### Post by Sidewinder1 on 2009-05-20
I know what you mean. Couldn't beat the price with a stick, that's why I got two. :-)

---

### Post by mavila on 2009-05-22
Ive got a couple of these running in various machines - the idea with the 3124 is its ability to multiplex one eSATA port and let you address multiple drives - in my case I have an enclosure that has 5 500GB spindles in it.

Essentially its pretty decent as far as inexpensive interface goes. The five spindles in the external enclosure are put together in software, and the current Ubuntu 9.04 kernel supports it fine (both 32 bit and 64 bit).

One gottcha seems to be booting with the multiplexer.. it worked awhile ago (year an a half or so) and then bot timing issues crept into the picture - this seems to only be an issue wiht Intel chipsets. I dont run AMD so I cant personally attest to this fact, but it has been written in other forums. Turning off APCI sems to have no effect... on boot the machine will got to busybox, and I havent found a workaround.

That said, my simple solution is to disconnect the eSATA cable when re-booting, then sson as the boot starts plug it back in. Pain in the backside, but it works.

mdadm finds stuff just fine adn putting 5 spindles into a big repository has its advantages.

Anyway, its inexpensive (not "cheap") to implement... and the performance is fine for having a 2TB mount point out there. Way faster than NAS!

---

### Post by Master One on 2009-05-23
My idea is to get two of [**these**](http://www.conceptronic.net/site/DesktopDefault.aspx?tabindex=1&tabid=232&cid=30&gid=3010&pid=CH3B2E) 2-disk-enclosures, which support different modes, of which only JBOD and RAID1 are relevant for me.

Now the catch is the following:

If I use these devices in JBOD mode, and let mdadm handle the disks as SoftRAID1, I need the "expensive" 3124 controller card ([**that**](http://www.delock.de/produkte/gruppen/pci-express/Delock_Raid_5_PCI_Express_x8_SATA_II_4_x_eSATA_70161.html?setLanguage=EN) one), because both discs are only accessible over one eSATA port, which means it's exactly the fitting case for a Sil3124.

If I use these devices in RAID1 mode, they are real hardware RAID1, and I can use the cheap 2-port controller card ([**that**](http://www.delock.de/produkte/suche/Delock_Controller_2x_eSATA_mit_Raid_70155.html?setLanguage=EN) one).

Usually a hardware RAID is preferred, but the downside is, that the management software for that device is for M$ OS only, means, I have to regularly visually check if everything is OK (and they are placed in a remote location), whereas mdadm would inform me by email in case of a problem.

---

### Post by iczerjones on 2012-02-03
Sorry to dredge up this old thread, but I just wanted to comment on this in case anyone was looking to use this controller for anything.

The fan cooler on that card has nothing to do with the storage subsystem at all - it is, in fact, cooling a PCI-X -> PCIe bridge chip.  It seems that the sil3124 was a PCI-X native device and required the bridge to convert it to PCIe.

The sil3124 is a host controller (or 'soft' controller), so it will not provide any hardware I/O offload, but is perfectly suitable for simply connecting devices and for mdraid.



> **Master One said:**
> I am confused about the Sil3124 as well. I was just investigating the following product:

[CENTER][url=http://www.delock.de/produkte/gruppen/pci-express/Delock_Raid_5_PCI_Express_x8_SATA_II_4_x_eSATA_70161.html?setLanguage=EN][img]http://www.delock.de/pictures/products/2/493e56bb70376.jpg[/img]
Delock Raid 5 PCI Express x8 card SATA II > 4 x eSATA[/url][/CENTER]

As you can see on the picture, it even has a fan, so it looks pretty powerful, making me assume, that this is a real hardware RAID controller. According to the Delock support, that card is based on the Sil3124.

If it is just another softraid controller, I don't quite understand the huge difference in price to the 2-port PCI card from Delock, the above shown 4-port PCI Express card is indeed quite expensive, and definitely not worth it, if it is not a real hardware RAID controller.

---

### Post by oldos2er on 2012-02-03
Closed, necromancy.

---

