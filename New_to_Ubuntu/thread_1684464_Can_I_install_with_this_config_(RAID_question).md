---
title: "Can I install with this config (RAID question)"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by PeeJay16 on 2011-02-09
Hi - I'd previously posted under this thread

[http://ubuntuforums.org/showthread.php?t=1678314](http://ubuntuforums.org/showthread.php?t=1678314)

as I was getting issues trying to install via WUBI. I've received a lot of helpful guidance from forum members and it now seems to be an issue with my PC configuration.

The system is a PC running XP SP3 with an ASUS A8V deluxe motherboard, a single internal  hard drive (shown in device manager as a Promise 1+0 stripe/RAID0 SCSI  disc drive) and a VIA Serial ATA RAID Controller. It also uses the fast  build utility.

I've checked inide the case and the HDD is connected to a SATA port on the motherboard. It doesn't look therefore as though the current hard disc can simply be switched to IDE.

What I'd like to achieve is a dual boot system with Ubuntu and XP, however I'm not sure whether I can get a successful install with this config?

I've enclosed a copy of the boot info script. sda is the internal drive, sdb is an external 500gb drive. I'd like to install on sda if possible but it's not essential.

[ATTACH]183062[/ATTACH]

---

### Post by YesWeCan on 2011-02-09
Is this a desktop PC or laptop? What make and model?
How did get Grub on the 500GB drive? It does not appear to have any linux partitions on it.

---

### Post by PeeJay16 on 2011-02-09
It's a desktop, made by a UK company called Mesh. It's quite a few years old but if you have specific questions about the spec I can get the info.

I've had a few attempts at installing Linux which have never worked, which is probably why there is a grub install on there. I removed the partitions after the failed install

---

### Post by psusi on 2011-02-09
Do not use Wubi; do a real install.

Also by definition RAID is more than one disk, so either you are not using RAID or you have more than one physical disk.

---

### Post by PeeJay16 on 2011-02-09
A real install is what I'm trying to achieve. I appreciate your comment about RAID however I only have one disk and it's being reported (via both Everest and XP device manager) as a 'Promise 1+0 stripe/RAID0 SCSI disk device'. I'm appreciate I'm using the word RAID out of it's usual context but it's how the system is being reported and from the previous thread it also may be the cause of the issues I was having.

In the previous thread I started I was advised to 'get rid of raid' (I'm paraphrasing) and re-post the boot info before I tried installing again. I've posted on a few other forums about removing the raid config and I'm not getting a lot of replies so I'm trying to ascertain from the experts on here whether my current config is going to cause an issue if I try and re-install Ubuntu into a dual boot configuration

---

### Post by YesWeCan on 2011-02-09
Ok.
Well, to begin with my experience is that you should always install Ubuntu on a different disk to Windows if you possibly can. That is why I wanted to check whether it was a laptop or not (many laptops only have one HD bay). Ubuntu can be installed on a very small disk if this makes it easier to find one or you can probably buy an 80GB disk these days for US$25. If you are feeling flush you could even buy a 120GB SSD and then you can blink and miss Ubuntu's boot! :p

Installing Ubuntu on a separate HD will avoid the question you are asking and make your life a whole lot simpler. Also, like me, you may well want to use your Windows installation from time to time. There are some applications and things that are unavailable on Linux or don't work well on Linux.

You mentioned in the other thread about installing Ubuntu on the 500GB external USB. That you can do without any problems (provided your mobo supports booting off USB) but it will be very slow compared to a sata HD installation and so this would not be a permanent solution. If you want a temporary solution for trying Ubuntu out then that's fine. You can also play using a live CD as you know.

Regarding the curious RAID on your existing HD: Clearly it is not a RAID because two disks are required. So there is some ghost of a RAID here. Was this PC ever used with two HDs in RAID mode? Or did the HD come from another PC that used it in RAID mode?

I am not sure how to remove the RAID ghosts while preserving the Windows installation. Again, I'd advise you leave it well alone until such time, if ever, you are happy to wipe the disk clean. I know that "moving" Windows is a real pain in the butt and takes ages. BTW at some point in the future, if you take to linux, you can use both disks for Ubuntu and migrate Windows to VirtualBox where it will be cosseted and safe and easy to relocate.

:)

---

### Post by psusi on 2011-02-09
Windows will only see one "drive" that is the array rather than the physical disks.  If you open the case you should see more than one.  If you boot the Ubuntu cd it should also see multiple physical disks.  It would be helpful if you do that and post the results of running this command in a terminal window:

```

sudo blkid

```

---

### Post by YesWeCan on 2011-02-09
There is a blkid output in the RESULTS.TXT file. I had a good look at this and the fisk output and couldn't see any evidence of two drives, even thought there is evidence of raid detection. I think the OP said, in the other thread, that he/she popped the hood and only saw one disk. It isn't clear to me what is going on:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_bjijfeceaf1 A82A-F795                              vfat       RECOVERY                      
/dev/mapper/pdc_bjijfeceaf2 01CBB1D56F9383C0                       ntfs       Windows                       
/dev/mapper/pdc_bjijfeceaf: PTTYPE="dos" 
/dev/sda1        A82A-F795                              vfat       RECOVERY                      
/dev/sda2        01CBB1D56F9383C0                       ntfs       Windows                       
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        FE2074A820746A13                       ntfs       500GB disk                    
/dev/sdb: PTTYPE="dos" 
```

---

### Post by YesWeCan on 2011-02-09
[http://www.promise.com/storage/raid_series.aspx?region=en-global&m=175&sub_m=sub_m_6&rsn1=5&rsn3=9](http://www.promise.com/storage/raid_series.aspx?region=en-global&m=175&sub_m=sub_m_6&rsn1=5&rsn3=9)

Presumably this disk (assuming there is only one) was formerly used as a disk in a hardware RAID array.

---

### Post by psusi on 2011-02-09
Ahh, that could be it.  How about the output from:

```

sudo dmraid -n

```

---

### Post by PeeJay16 on 2011-02-12
Sorry for the delay - been doing other things for a few days.

I've just tried to install Ubuntu onto a clean empty external HDD. Everything looked OK but when I tried to close down for the re-boot at the end of the install I saw some normal shut down type messages followed by a page or two of 

[1838.nnnnn] end request, I/O error, dev sr0, sector nnnnnnnnnn where n is a number. The system then hung until I powered off and on, at which point there is no option for Ubuntu and it goes into Windows normally.

I thought it might be the CD but I've just seen this thread

[http://ubuntuforums.org/showthread.php?t=968194](http://ubuntuforums.org/showthread.php?t=968194)

Which appears similar but I don't get the Buffer I/O error messages, just the end request ones. Incidentally I am running an AMD64 chipset and have the AMD64 iso

I'm in Windows at the moment but next time I re-boot I'll re-run the boot info script and post it in case someone can advise on a way of salvaging the install.

Thanks for all the assistance

---

### Post by PeeJay16 on 2011-02-12
Here's the results.txt file

---

### Post by psusi on 2011-02-12
You have two hard disks that were in a raid array.  You appear to have broken that array by installing Ubuntu to one of the physical disks, bypassing the raid layer.

---

### Post by PeeJay16 on 2011-02-13
Unfortunately I don't think that's the case :smile:

The system originally had one HDD (internal) which was, and still is, set in 'RAID mode' in the BIOS. I'm not sure how you can get any sort of RAID with one drive but that's how it came from the manufacturer. The second drive is an external that I bought a couple of years ago, so I don't believe I've ever had an array to break.

I'm trying to find out (via another forum) how I can change the internal HDD from a RAID to a normal IDE, however as the HDD is plugged into a SATA port on the motherboard it's proving more difficult than I thought it would be as simply turning RAID mode off in the BIOS results in windows not being able to find any discs, and I'm hunting around for the right drivers.

Is there a way of salvaging the Ubuntu install I currently have or should I scrap it?

---

### Post by Quackers on 2011-02-13
If you go into your bios you may or may not see a raid array reported. There may also be an option to delete the raid array, or to use "non-raid". See what's in there and report back please.
But beware! If you are using a raid array and you set it to non-raid, you may lose any installed operating systems.

---

### Post by psusi on 2011-02-13
Both sda and sdb claim to be members of a raid array.  sudo dmraid -n /dev/sd[ab] will provide more details.

---

### Post by PeeJay16 on 2011-02-14
Motherboard is an ASUS A8V deluxe. In the BIOS advanced options, under onboard device configuration the onboard promise controller is enabled and the operating mode is set to RAID mode. If I change RAID mode to the other option 'Onboard IDE mode' Windows can't find the internal HDD although it seems to be recognised in the BIOS during startup. Primary IDE master is set to Auto in the BIOS and showing  not detected. Looking in the case the internal HD is plugged into a SATA port.

As part of startup something called the 'FastBuild' utility runs. This seems to have something to do with the RAID on the drive but when I deleted the RAID array using this I got as far as the Windows start screen and then the system rebooted.

Looking at the results.txt file sda is the external HD, which has the Linux partitions as well as an NTFS partition, sdb is the internal HD. sdb1 is some sort of hidden partition that is marked as a recovery partition. I've never used it and it can go if necessary. sdb2 is the windows partition.

Running  sudo dmraid -n /dev/sda gives 'no raid disks and with names: "/dev/sda"

For sdb I get

/dev/sdb (pdc):
0x000 promise_id: "Promise Technology, Inc."
0x018 unknown_0: 0x20000 131072
0x01c magic_0: 0x69760210
0x020 unknown_1: 0x10012 65554
0x024 magic_1: 0x70150210
0x028 unknown_2: 0x12 18
0x200 raid.flags: 0x80
0x204 raid.unknown_0: 0x7 7
0x205 raid.disk_number: 0
0x206 raid.channel: 1
0x207 raid.device: 0
0x208 raid.magic_0: 0x69760210
0x20c raid.unknown_1: 0x10012 65554
0x210 raid.start: 0xedeeeff0 3991859184
0x214 raid.disk_secs: 398297025
0x218 raid.unknown_3: 0xffffffff 4294967295
0x21c raid.unknown_4: 0x1 1
0x21e raid.status: 0xf
0x21f raid.type: 0x0
0x220 raid.total_disks: 1
0x221 raid.raid0_shift: 7
0x222 raid.raid0_disks: 1
0x223 raid.array_number: 0
0x224 raid.total_secs: 398296960
0x228 raid.cylinders: 24791
0x22a raid.heads: 254
0x22b raid.sectors: 63
0x22c raid.magic_1: 0x70150210
0x230 raid.unknown_5: 0x12 18
0x234 raid.disk[0].unknown_0: 0x7
0x236 raid.disk[0].channel: 1
0x237 raid.disk[0].device: 0
0x238 raid.disk[0].magic_0: 0x69760210
0x23c raid.disk[0].disk_number: 65554
0x7fc checksum: 0xce09c21f Ok

Hope this helps.

I really appreciate all the help I'm getting to try and resolve this. I'm quite happy to reload windows is that's required as part of the fix.

---

### Post by psusi on 2011-02-15
The only conclusion that I can reach is that at some point you used the bios utility to create a raid array using both the internal and external disk, and have since broken that array.  At this point you need to use the bios utility to destroy the raid array ( you already seem to have done that for one disk, but not the other ), and do a complete reinstall.

---

### Post by PeeJay16 on 2011-02-19
I'm posting the solution in case anyone searches in here. The HD was plugged into a SATA_RAID port on the motherboard. Plugging it into a normal SATA port and disabling the Promise controller in the BIOS (to stop error messages at startup) got rid of the RAID issue and it now looks like a normal drive.

---

### Post by psusi on 2011-02-19
> **PeeJay16 said:**
> I'm posting the solution in case anyone searches in here. The HD was plugged into a SATA_RAID port on the motherboard. Plugging it into a normal SATA port and disabling the Promise controller in the BIOS (to stop error messages at startup) got rid of the RAID issue and it now looks like a normal drive.

That does not resolve the issue.  The raid metadata is still on the drive, and while the bios won't recognize it, Ubuntu will.  You need to remove it either with the bios raid utility, or by running sudo dmraid -E /dev/sdXX.

---

