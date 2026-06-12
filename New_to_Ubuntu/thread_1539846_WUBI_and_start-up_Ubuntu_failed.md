---
title: "WUBI and start-up Ubuntu failed"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Angelique-van-Campen on 2010-07-27
Hi all,

I hope this is the correct place to post my message. I've got the following problem installing Ubuntu via Wubi.

Downloaded Wubi, all works fine and at the end while in Windows 7 64 bits, it requested to reboot my PC. Reboot fine, Ubuntu option added to the boot screen and chose for Ubuntu. At the next selection screen I left it at the first option (Ubuntu, Linux 2.6.32-21-generic). Quickly after that I got the following fault message or I suppose so since loading Ubuntu stopped.
The fault message was:
[COLOR=SeaGreen]Alert! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
Busybox v.1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)[/COLOR]

I did a restart and this time I decided to go for the 2nd option "Ubuntu, Linux 2.6.32-21-generic (recovery)".
A screen full of commands is passing over the screen and suddenly it stops at:
[COLOR=SeaGreen][9.559018] sd 6:0:0:0:1: [sdf] attached SCSI removable disk[/COLOR]

Nothing happened after this till I pressed the Enter key. That resulted in [COLOR=SeaGreen](initramfs)[/COLOR].

I thought it was so easy, but although I'm not a specialist in hardware at all, I've got the idea it has something to do with my hardware and in this case a HD.

[COLOR=Red]Anybody who can help me since I'm lost to be honest[/COLOR] :confused:?

Probably it helps adding my hardware specs to this posting:
- Asus P6T Deluxe V2 i7 X58/ddr3
- Samsung SH-S223B/BEBE
- EVGA GeForce GTX 285
- Intel Core i7 Extreme Edition i7-965
- Corsair TR3X6G1600C8D Dominator PC3-12800/1600MHz 6G
- Western Digital WD3000HLFS Velociraptor 300GB 16MB
- Western Digital WD10EADS Caviar Green 1TB 7200RPM 32M

Thanks in advance for your reply,

Kind regards,
Angelique van Campen

---

### Post by P4man on 2010-07-27
Seems like ubuntu can not access the windows partition. This could be because its "dirty", which happens when windows is not shut down properly. To remediate that just boot windows and perform a chkdsk.

That said; im not a wubi fan and I would strongly advice you to create a livecd (or usb stick), boot from that  to test if your system works well with ubuntu and install from the livecd so you have a proper dual boot where ubuntu is not dependent on windows file system.

---

### Post by justincase_2008 on 2010-07-27
The bad thing is installing the live cd can mess up the windows partition. Windows 7 and vista both hide system files at the end of its partitions. So that when you resize them to make room for ubuntu it sometimes kills windows. Thats why wubi is a risk free way to have both. The best thing would be as he said test it with a live cd i do that all the time works great. If all goes good try loading wubi again. Wubi has to run with out anything else so kill all other processes then run wubi and make sure it goes uninterrupted. Heres a youtube on doing wubi on windows 7. [http://www.youtube.com/watch?v=Fy1ISEJIv84](http://www.youtube.com/watch?v=Fy1ISEJIv84)

---

### Post by Angelique-van-Campen on 2010-07-27
> **P4man said:**
> Seems like ubuntu can not access the windows partition. This could be because its "dirty", which happens when windows is not shut down properly. To remediate that just boot windows and perform a chkdsk.

That said; im not a wubi fan and I would strongly advice you to create a livecd (or usb stick), boot from that  to test if your system works well with ubuntu and install from the livecd so you have a proper dual boot where ubuntu is not dependent on windows file system.

Hey,

For some reason even after several CHKDSK commands, it still doesn't work. Making a partition on my current Windows 7 HD is not a problem. I'm only worrying about the boot menu. With WUBI I've seen that it adds "Ubuntu" to my existing boot menu. I'm not sure if this happens also when I use the CD installation without WUBI.

---

### Post by Angelique-van-Campen on 2010-07-27
> **justincase_2008 said:**
> The bad thing is installing the live cd can mess up the windows partition. Windows 7 and vista both hide system files at the end of its partitions. So that when you resize them to make room for ubuntu it sometimes kills windows. Thats why wubi is a risk free way to have both. The best thing would be as he said test it with a live cd i do that all the time works great. If all goes good try loading wubi again. Wubi has to run with out anything else so kill all other processes then run wubi and make sure it goes uninterrupted. Heres a youtube on doing wubi on windows 7. [http://www.youtube.com/watch?v=Fy1ISEJIv84](http://www.youtube.com/watch?v=Fy1ISEJIv84)

Hi,

Although I've read more people having problems with WUBI, the YouTube movie is indeed an option. On option to get Ubuntu on a separate partition instead of a folder within Windows. I think I'll try this option first. I'm curious how I can handle Linux for my writing and flight simulator testing. Most programs are available for Linux however, for MSFS I still need Windows except for reviewing X-Plane products.

Thanks so far for the help.

---

### Post by Angelique-van-Campen on 2010-07-27
Guys, 

Thanks for the help so far. I'll let you know the outcome. I'll try on my PC WUBI on a separate partition, while on my other PC I'll try the use the Ubuntu CD.

To be continued.


Greetings,
Angelique

---

### Post by Angelique-van-Campen on 2010-07-27
Guys,

Here the promised update.

I created a separate partition - 31GB -  for Ubuntu. Started WUBI and directed it to this partition. At start-up of the PC, I chose for the first Ubuntu menu option "Ubuntu, Linux 2.6.32-21-generic". Very quickly after that, a screen full of fault messages appeared (see screenshot [http://img825.imageshack.us/img825/5644/dscn3597.jpg](http://img825.imageshack.us/img825/5644/dscn3597.jpg)
I couldn't use Cltr+Alt+Del, so I used the reset knob.

During my second attempt I used the 2nd Ubuntu menu option "Ubuntu, Linux 2.6.32-21-generic (recovery)". This resulted also in a fatal error message. See for this screenshot [http://img818.imageshack.us/i/dscn3600.jpg/](http://img818.imageshack.us/i/dscn3600.jpg/)

Any ideas?

---

### Post by P4man on 2010-07-27
You cant do a native install using wubi. Stop using wubi. boot the livecd or usb stick. Follow the instruction here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

and be sure to scroll down to see steps 2, 3 and (eventually, after you tested it and it works for you) 4.

---

### Post by Angelique-van-Campen on 2010-07-27
> **P4man said:**
> You cant do a native install using wubi. Stop using wubi. boot the livecd or usb stick. Follow the instruction here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

and be sure to scroll down to see steps 2, 3 and (eventually, after you tested it and it works for you) 4.

P4man,

Thanks so far for the help.
I'll try your suggestion tomorrow. Let you know the outcome.

---

### Post by Angelique-van-Campen on 2010-07-28
Here's the promised feedback.

Did a Ubuntu *try out* via the CD. Worked perfect and no problems where detected except for the video driver, which makes sense.

Decided to use my previous created Ubuntu partition (> 30GB) to install Ubuntu. Just a quick note of my HD configuration:
- HD 1-1 (300GB): Windows 7 Ultimate + X-Plane (partition I)
- HD 1-2 (300GB): planned for Ubuntu (partition II)
- HD 2 (300GB): Flight Simulator X (not partitioned)
- HD 3 (300GB): Windows 7 + FSX + FS9 (used for flight sim reviews and not partitioned)
- HD 4 (1TB): Data (not partitioned)
The above means that I have already a Windows BOOT menu to select between Windows versions HD1-1 and HD-3.

Ok, Inserted the liveCD, started PC, Ubuntu configuration came up and at step 4 or 5 it asked me where to install. It showed me that there was no OS detected (strange?) and I couldn't find my previous created Ubuntu partition. Because of this, I stopped the installation else I could end up in no Windows 7 access.
[COLOR=Red]Did I do something wrong or was it logic that the Ubuntu partition wasn't visible?[/COLOR] The partition was created in Windows 7 and NTFS formatted.

---

### Post by P4man on 2010-07-28
Its clear now that there is something about the NTFS filesystem(s) that ubuntu doesnt like. I have seen this before (well; seen it posted here) and then it was due to the drives having been part of a RAID array and there was metadata left on the drives.

If you are sure you are not using a raid under windows, then try these 2 things:

1) check your bios settings and make sure the SATA controller is not configured to work as raid but just as plain IDE/SATA.
2) boot the live cd again. Open a terminal  (application > accessories > terminal). In the terminal enter the following commands and copy/paste the output here:

```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdc
sudo dmraid -E -r /dev/sdd

```

Please note this is entirely case sensitive. Also note if you are using a raid then you will likely get into serious trouble as it will remove the RAID metadata. Only run those if you are confident you are not actually using a raid (which seems rather likely with your HDD config; but still).

After that; start the ubuntu installer again; I dont think it requires a reboot but if it fails try a reboot and try again and Im pretty hopeful it will detect your partitions and windows installations correctly.

---

### Post by P4man on 2010-07-28
And one more thing.. can you not use the 1TB drive for ubuntu? While dual boot tends to work fine; I like to put my OSs on seperate drives that can all boot independantly. If something goes wrong with one OS or drive or bootloader then i can still boot any of the other OSes.

The complete failsafe way would be to disconnect all your drives except the 1 TB one and install ubuntu there. That will put the ubuntu bootloader on that drive too and not touch anything on the disconnected windows drives. After installing; reconnect the other drives; configure bios to boot from the 1TB drive and run "sudo update-grub" so ubuntu will detect the windows installations and offer dual or triple boot.

If anything goes wrong; you can just change the bios boot order to get back to windows at no risk.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> And one more thing.. can you not use the 1TB drive for ubuntu? While dual boot tends to work fine; I like to put my OSs on seperate drives that can all boot independantly. If something goes wrong with one OS or drive or bootloader then i can still boot any of the other OSes.

The complete failsafe way would be to disconnect all your drives except the 1 TB one and install ubuntu there. That will put the ubuntu bootloader on that drive too and not touch anything on the disconnected windows drives. After installing; reconnect the other drives; configure bios to boot from the 1TB drive and run "sudo update-grub" so ubuntu will detect the windows installations and offer dual or triple boot.

If anything goes wrong; you can just change the bios boot order to get back to windows at no risk.

I can't use the internal 1TB for Ubuntu because my 1TB drive is for all my data.

Instead of that and eventually this will take place, it will get a complete 300GB drive. The drive that currently holds my 2nd Windows 7 Reviews version will become the Ubuntu drive. Said that there's a problem doing that straightaway or I think that could lead to a problem.
A while ago I installed Win7 on HD1 with all my programs. Because there was only one Windows, there was no boot menu. Then I installed on a separate drive my 2nd Win7. The problem is that this drive holds the Windows boot information. When I decide to install on this drive (holding the 2nd Windows version) Ubuntu I lose my Windows bootmenu and thus the possibility to access my main Windows system or at least I think this is the way it works. When I'm wrong, please correct me.

I'll first try your previous posting and see what the outcome is.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> Its clear now that there is something about the NTFS filesystem(s) that ubuntu doesnt like. I have seen this before (well; seen it posted here) and then it was due to the drives having been part of a RAID array and there was metadata left on the drives.

If you are sure you are not using a raid under windows, then try these 2 things:

1) check your bios settings and make sure the SATA controller is not configured to work as raid but just as plain IDE/SATA.
2) boot the live cd again. Open a terminal  (application > accessories > terminal). In the terminal enter the following commands and copy/paste the output here:

```

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdc
sudo dmraid -E -r /dev/sdd

```Please note this is entirely case sensitive. Also note if you are using a raid then you will likely get into serious trouble as it will remove the RAID metadata. Only run those if you are confident you are not actually using a raid (which seems rather likely with your HDD config; but still).

After that; start the ubuntu installer again; I dont think it requires a reboot but if it fails try a reboot and try again and Im pretty hopeful it will detect your partitions and windows installations correctly.

Ok, I checked my BIOS and found the following settings under Main -> Storage Configuration:
- SATA Configuration -> [Enhanced]. Other options are "compatible" and "disable".
- Configure SATA as -> [IDE]. Other options are RAID and ACHI.

Started LiveCD and checked the four dmraid commands. See the output below:
sudo dmraid -E -r /dev/sda
[COLOR=Red]no raid disks and with names: "/dev/sda"[/COLOR]
sudo dmraid -E -r /dev/sdb
[COLOR=Red]no raid disks and with names: "/dev/sdb"[/COLOR]
sudo dmraid -E -r /dev/sdc
[COLOR=Red]no raid disks and with names: "/dev/sdc"[/COLOR]
sudo dmraid -E -r /dev/sdd
[COLOR=Red]no raid disks and with names: "/dev/sdd"[/COLOR]

---

### Post by P4man on 2010-07-28
Windows; like ubuntu, needs a bootloader. It sits at the beginning of a drive and the OS installer in either case will install it on the drive the BIOS is configured to boot from (even if the OS gets installed elsewhere). So on the "first" drive. If there is only one OS installed (or detected) neither windows nor ubuntu bootloader will show a menu.

Windows bootloader can not chainload to a an OS that is not on a FAT or NTFS partition, like ubuntu (unless you use WUBI). That is why ubuntu will by default replace the windows bootloader with its own (called GRUB) and let you chainload the windows bootstrapper.

It doesnt really matter on what drives the OSs are installed. The bootloader goes to the first drive, in your case the windows drive, even if ubuntu ends up installed on a different drive. 

And when youd reinstall windows it will overwrite the grub bootloader again on the first drive, replace it with windows own bootloader and render ubuntu unbootable regardless of what drive its on (its not hard to fix that; but it does involve booting the livecd and restoring grub).

I dont like this approach too much. I prefer to keep the windows bootloader intact on its own drive and have ubuntu have its own drive with its own grub bootloader. I just configure my bios to boot my ubuntu drive first. Then grub will let me chainload in to windows if I want to. If remove the ubuntu drive; windows will boot like it did before as that drive still contains the windows bootloader. If I remove or format the windows drive; ubuntu will still boot with no problem. 

To achieve this with no chance of error; I tend to disconnect each drive except the one I really need for the OS. That makes it impossible for the OS installer to install the bootloader on the "wrong" drive. in ubuntu installer in the last step you can change the location of the bootloader but this isnt always very clear and unplugging a few drives makes it 100% idiot proof.

Anyway, you dont have to do this. But just to say if you install ubuntu (assuming the raid thing fixes the problem) by default ubuntu will install on whatever drive you tell it to; but will also replace the windows bootloader with grub on the first bootable drive. As a result; if ever you remove that windows drive, ubuntu will no longer be able to boot even if its on a different drive. You will have to boot the livecd and install grub on the other drive then. Those are not terrible hassles but I rather avoid them :)

---

### Post by P4man on 2010-07-28
> **Angelique-van-Campen said:**
> Ok, I checked my BIOS and found the following settings under Main -> Storage Configuration:
- SATA Configuration -> [Enhanced]. Other options are "compatible" and "disable".
- Configure SATA as -> [IDE]. Other options are RAID and ACHI.

Started LiveCD and checked the four dmraid commands. See the output below:
sudo dmraid -E -r /dev/sda
[COLOR=Red]no raid disks and with names: "/dev/sda"[/COLOR]
sudo dmraid -E -r /dev/sdb
[COLOR=Red]no raid disks and with names: "/dev/sdb"[/COLOR]
sudo dmraid -E -r /dev/sdc
[COLOR=Red]no raid disks and with names: "/dev/sdc"[/COLOR]
sudo dmraid -E -r /dev/sdd
[COLOR=Red]no raid disks and with names: "/dev/sdd"[/COLOR]

Bummer. So its not a raid thing then. That leaves GPT. Did you ever try to install OS-X hackintosh on this machine?

regardless, open a terminal and type

```
sudo fdisk -l
```

(thats a lowercase L at the end). Copy paste the output. Im guessing the first lines will include an error about GPT. Something like:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


If that is indeed the case; have a look at this post:

[http://ubuntuforums.org/showpost.php?p=9464066&postcount=3](http://ubuntuforums.org/showpost.php?p=9464066&postcount=3)

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> Windows; like ubuntu, needs a bootloader. It sits at the beginning of a drive and the OS installer in either case will install it on the drive the BIOS is configured to boot from (even if the OS gets installed elsewhere). So on the "first" drive. If there is only one OS installed (or detected) neither windows nor ubuntu bootloader will show a menu.

Windows bootloader can not chainload to a an OS that is not on a FAT or NTFS partition, like ubuntu (unless you use WUBI). That is why ubuntu will by default replace the windows bootloader with its own (called GRUB) and let you chainload the windows bootstrapper.

It doesnt really matter on what drives the OSs are installed. The bootloader goes to the first drive, in your case the windows drive, even if ubuntu ends up installed on a different drive. 

And when youd reinstall windows it will overwrite the grub bootloader again on the first drive, replace it with windows own bootloader and render ubuntu unbootable regardless of what drive its on (its not hard to fix that; but it does involve booting the livecd and restoring grub).

I dont like this approach too much. I prefer to keep the windows bootloader intact on its own drive and have ubuntu have its own drive with its own grub bootloader. I just configure my bios to boot my ubuntu drive first. Then grub will let me chainload in to windows if I want to. If remove the ubuntu drive; windows will boot like it did before as that drive still contains the windows bootloader. If I remove or format the windows drive; ubuntu will still boot with no problem. 

To achieve this with no chance of error; I tend to disconnect each drive except the one I really need for the OS. That makes it impossible for the OS installer to install the bootloader on the "wrong" drive. in ubuntu installer in the last step you can change the location of the bootloader but this isnt always very clear and unplugging a few drives makes it 100% idiot proof.

Anyway, you dont have to do this. But just to say if you install ubuntu (assuming the raid thing fixes the problem) by default ubuntu will install on whatever drive you tell it to; but will also replace the windows bootloader with grub on the first bootable drive. As a result; if ever you remove that windows drive, ubuntu will no longer be able to boot even if its on a different drive. You will have to boot the livecd and install grub on the other drive then. Those are not terrible hassles but I rather avoid them :)

While typing this from LiveCD Ubuntu, I'm almost ready to install Ubuntu on a complete drive, so no partition. The only thing to figure out for me was which drive "/dev/sda or b or c or d" is which software. I mounted one drive at the time, started the installer and the installer showed me which one was mounted and if it could unmount is. Finer for me, but important was that I could link them the sda (or sdb, sdc and sdd) to my Windows naming.
Anyway, I have decided to install Ubuntu to /dev/sdd which was my 2nd Windows 7 Reviews disk. I hardly use it so let' see if this works and hopefully that at the first boot, I can choose between the remaining  (and most important Windows 7 config) Windows and Ubuntu. Later I can if I want make Ubuntu to first drive to start from.
Now it's time to try it out .....:)

---

### Post by P4man on 2010-07-28
I doubt dual boot will work as long as the NTFS/partition issue isnt solved. So be very careful. If you are going to install ubuntu on whatever drive while the windows drive is still connected and set as first boot drive in the BIOS, then there is a very good chance windows will not be bootable anymore as ubuntu will put its bootloader on the windows drive and apparently isnt seeing the windows OS installed on that drive.

disconnect all drives except the one you want to install on; is still my advice. Then later try setting up the dual boot but even if that fails or you havent figured it out yet;  you can still use the BIOS boot order to select your OS.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> I doubt dual boot will work as long as the NTFS/partition issue isnt solved. So be very careful. If you are going to install ubuntu on whatever drive while the windows drive is still connected and set as first boot drive in the BIOS, then there is a very good chance windows will not be bootable anymore as ubuntu will put its bootloader on the windows drive and apparently isnt seeing the windows OS installed on that drive.

disconnect all drives except the one you want to install on; is still my advice. Then later try setting up the dual boot but even if that fails or you havent figured it out yet;  you can still use the BIOS boot order to select your OS.

You're quite right .. it went wrong!
After the installation of Ubuntu, the PC didn't restart. The only thing there was, was a black screen with a cursor. For sure, I did something, so I can't blame anybody.

Ok, I took my Paragon Rescue & Recovery CD and let it search for my boot loader. It (Paragon) found it so I could boot my main Windows 7 config. If it right or not, I installed EasyBCD and added a Ubuntu entry, but at the same time I also "disabled' the boot menu. Just to see with a restart if it works. I must first see it before I believe it!

Ok, when this works, I'll try it again. Ubuntu installation on my /dev/sdd (disk 3) drive and then I'll tell Ubuntu to install the boot on the same drive as Ubuntu itself. I hope I write this correctly down and when we'll see what happens. This is the news for now.
To be continued!

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> I doubt dual boot will work as long as the NTFS/partition issue isnt solved. So be very careful. If you are going to install ubuntu on whatever drive while the windows drive is still connected and set as first boot drive in the BIOS, then there is a very good chance windows will not be bootable anymore as ubuntu will put its bootloader on the windows drive and apparently isnt seeing the windows OS installed on that drive.

disconnect all drives except the one you want to install on; is still my advice. Then later try setting up the dual boot but even if that fails or you havent figured it out yet;  you can still use the BIOS boot order to select your OS.

P4man,

I'll try to disable all the drives I don't need (and if I can find) that are in the BIOS :)!

---

### Post by justincase_2008 on 2010-07-28
Yeah he is right loading on a separate drive is the best way. With all my laptops i get a second drive load ubuntu on it and swap drives as its needed. The desktop has two drives as well.

---

### Post by P4man on 2010-07-28
> **Angelique-van-Campen said:**
> P4man,

I'll try to disable all the drives I don't need (and if I can find) that are in the BIOS :)!

Disabling in the bios doesnt always work. Ive seen ubuntu detect and work just fine with drives that were disabled in the bios. I guess it depends on the bios though. i just unplug them but to each their own :) You could also set that drive on which you want to install ubuntu as first boot drive in the bios and that *should* work too, its just that with disconnected drives you cant mess up :)


**edit: **Note however /dev/sdb or a or c will change. a is just the first; b the second etc. So if you disable 3 drives, the remaining will become /dev/sda regardless if it was /dev/sdc before. IF you change boot order those letters will (usually) change too. Ubuntu uses a unique identifier called UUID to avoid mixing up drives; but sda or sdb is not unique per drive; its in order of boot.


Also you havent yet replied on the part about GPT. Did ubuntu complain about GPT when you ran sudo fdisk -l ?

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> Disabling in the bios doesnt always work. Ive seen ubuntu detect and work just fine with drives that were disabled in the bios. I guess it depends on the bios though. i just unplug them but to each their own :) You could also set that drive on which you want to install ubuntu as first boot drive in the bios and that *should* work too, its just that with disconnected drives you cant mess up :)


**edit: **Note however /dev/sdb or a or c will change. a is just the first; b the second etc. So if you disable 3 drives, the remaining will become /dev/sda regardless if it was /dev/sdc before. IF you change boot order those letters will (usually) change too. Ubuntu uses a unique identifier called UUID to avoid mixing up drives; but sda or sdb is not unique per drive; its in order of boot.


Also you havent yet replied on the part about GPT. Did ubuntu complain about GPT when you ran sudo fdisk -l ?

Ok, I never reached disabling HDD's in the BIOS nor that I don't want to open my PC. Lets' first finish this part before moving to the GPT option.
After I installed Ubuntu to a separate drive, I couldn't restart my PC, not in Ubuntu and not in Windows. Whatever I did wrong, after some hours I have restored with Paragon on of my last image files for my main Windows 7 system. While typing this I'm restoring the belonging FSX data on a separate drive too. What's left is a empty drive planned for Ubuntu. As it is now, I can boot the PC for my only Windows 7 without any problems. In other words, hours further but almost back to what it was before.

Let's first jump to the GPT.
For some "unknown reasons" I didn't try this because my HDD's where a mesh and I didn't understand why Paragon couldn't solve that problem. Sorry for I didn't follow your advice :oops:!

What's my current situation?
I've got Windows 7 on an own HD, FSX (Flight Simulation) on a disk and one 300GB spare disk for Ubuntu. That's what I want, but my only problem is ..... the Ubuntu software wants to know where to put the Ubuntu boot loader. [COLOR=Red]Shall I put that on the Ubuntu drive itself or does it make any difference where I put it?[/COLOR]

---

### Post by P4man on 2010-07-28
> **Angelique-van-Campen said:**
> 
What's my current situation?
I've got Windows 7 on an own HD, FSX (Flight Simulation) on a disk and one 300GB spare disk for Ubuntu. That's what I want, but my only problem is ..... the Ubuntu software wants to know where to put the Ubuntu boot loader. [COLOR=Red]Shall I put that on the Ubuntu drive itself or does it make any difference where I put it?[/COLOR]

I could be wrong but I think it will put the stage1 bootloader on the first disk (being your windows drive I assume) regardless what you set there; it will only put the grub files on the drive you select there. But I could be wrong. Not gonna repeat myself saying its safest to first make sure ubuntu installer recognizes the windows installation (the GPT thing) or disconnecting the other drives or at least changing the boot order in the bios so ubuntu sees the 300 GB drive as /dev/sda.

Anything else i cant guarantee windows will still boot.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> Bummer. So its not a raid thing then. That leaves GPT. Did you ever try to install OS-X hackintosh on this machine?

regardless, open a terminal and type

```
sudo fdisk -l
```(thats a lowercase L at the end). Copy paste the output. Im guessing the first lines will include an error about GPT. Something like:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


If that is indeed the case; have a look at this post:

[http://ubuntuforums.org/showpost.php?p=9464066&postcount=3](http://ubuntuforums.org/showpost.php?p=9464066&postcount=3)

P4man,

As promised, here's my output of the "sudo fdisk -l" command:

[COLOR=Blue]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20627650

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d6bc9db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36482   293033984    7  HPFS/NTFS

Disk /dev/sdd: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b0b3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2062764f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36482   293033984    7  HPFS/NTFS[/COLOR]

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> I could be wrong but I think it will put the stage1 bootloader on the first disk (being your windows drive I assume) regardless what you set there; it will only put the grub files on the drive you select there. But I could be wrong. Not gonna repeat myself saying its safest to first make sure ubuntu installer recognizes the windows installation (the GPT thing) or disconnecting the other drives or at least changing the boot order in the bios so ubuntu sees the 300 GB drive as /dev/sda.

Anything else i cant guarantee windows will still boot.

Ok,

Here we go. I've now physically identified with HD in my PC is which system (Windows 7, Data, FSX and Ubuntu). While typing this posting, only the windows 7 and "the to be" Ubuntu drives are still physically in my PC connected.
[COLOR=Blue]Do you suggest to disconnect the Windows 7 HD as well and then it's safe to install Ubuntu on the only available connected HD?[/COLOR]

BTW; thanks for all the help so far.
Much appreciated :D!

---

### Post by P4man on 2010-07-28
assuming you didnt accidentally leave out the WARNING line above the part you quoted, then I ran out of known issues why ubiquity (=ubuntu install program) doesnt detect the windows installation(s) :(

You could try a number of things though. Either just disconnect / disable the other drives and install ubuntu on the 300 GB and we will fix dual boot later on. Or you could try downloading a daily build of ubuntu 10.04 :

[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)

Alternatively, you could try updating ubuntu in the livesession (these updates wont survive a reboot) or only update ubiquity by running
```

sudo apt-get install ubiquity
```

in a terminal and then try to install.

Last thought.. whatever you did to fix windows; have you checked if ubuntu installation is now not recognizing your windows 7 install?

---

### Post by P4man on 2010-07-28
> **Angelique-van-Campen said:**
> 
[COLOR=Blue]Do you suggest to disconnect the Windows 7 HD as well and then it's safe to install Ubuntu on the only available connected HD?[/COLOR]

BTW; thanks for all the help so far.
Much appreciated :D!

**Especially** the windows 7 drive. At least if ubuntu installer still doesnt detect it.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> assuming you didnt accidentally leave out the WARNING line above the part you quoted, then I ran out of known issues why ubiquity (=ubuntu install program) doesnt detect the windows installation(s) :(

You could try a number of things though. Either just disconnect / disable the other drives and install ubuntu on the 300 GB and we will fix dual boot later on. Or you could try downloading a daily build of ubuntu 10.04 :

[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)

Alternatively, you could try updating ubuntu in the livesession (these updates wont survive a reboot) or only update ubiquity by running
```

sudo apt-get install ubiquity
```in a terminal and then try to install.

Last thought.. whatever you did to fix windows; have you checked if ubuntu installation is now not recognizing your windows 7 install?

The Windows 7 OS is finally detected.

So, I started the liveCD with only the Windows 7 and Ubuntu HDD's connected. At the install step 4 of 7 I can chose - of course - out of two drves (sda and sdb).
On this screenshot - [http://img530.imageshack.us/i/dscn3601.jpg/](http://img530.imageshack.us/i/dscn3601.jpg/) - when I chose this disk I delete the Windows 7 loader so not a good option I suppose. On the next screenshot - [http://img192.imageshack.us/i/dscn3602r.jpg/](http://img192.imageshack.us/i/dscn3602r.jpg/) - there's no OS on it, which is correct since this one is my planned Ubuntu drive.

[COLOR=Blue]My personal conclusion is - even with the Windows 7 HD detected - that I go for the 2nd screenshot and install Ubuntu on this drive (/dev/sdb).[/COLOR]

There's one question left;
At step 7 of 7 (Ready to Install) there's an Advanced button. When I click this, I can add a bootloader on either drive sda (Windows 7) or sdb (Ubuntu). By default it's ticked and set for drive sda. If I want to, I can untick it.
[COLOR=Blue]Just leave it to the default settings (drive sda and install the bootloader)?[/COLOR]

---

### Post by P4man on 2010-07-28
> **Angelique-van-Campen said:**
> The Windows 7 OS is finally detected.


Ah; good. In that case something was probably not quite right with the partitions and Paragon fixed that.

> There's one question left;
At step 7 of 7 (Ready to Install) there's an Advanced button. When I click this, I can add a bootloader on either drive sda (Windows 7) or sdb (Ubuntu). By default it's ticked and set for drive sda. If I want to, I can untick it.
[COLOR=Blue]Just leave it to the default settings (drive sda and install the bootloader)?[/COLOR]

I would set it to sdb (assuming that is where you install ubuntu).
When you do that and you dont change the bios boot order, the machine will most likely boot straight in to windows, no chance to select ubuntu. However do that and change the bios boot order to boot from the 300GB drive first; and you should be getting a grub menu chosing between ubuntu and windows. There is a slight chance grub will get confused and mix up both drives, or not adding windows but lets just take that chance for now its easy to fix.

If you set it to sda, you should also get that grub menu leting you chose windows or ubuntu, but your ubuntu drive will not boot without the windows drive installed and windows will only be booting via grub, requiring the ubuntu drive. Thats not a terrible thing but Id rather not do that if you dont have to.

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> Ah; good. In that case something was probably not quite right with the partitions and Paragon fixed that.



I would set it to sdb (assuming that is where you install ubuntu).
When you do that and you dont change the bios boot order, the machine will most likely boot straight in to windows, no chance to select ubuntu. However do that and change the bios boot order to boot from the 300GB drive first; and you should be getting a grub menu chosing between ubuntu and windows. There is a slight chance grub will get confused and mix up both drives, or not adding windows but lets just take that chance for now its easy to fix.

If you set it to sda, you should also get that grub menu leting you chose windows or ubuntu, but your ubuntu drive will not boot without the windows drive installed and windows will only be booting via grub, requiring the ubuntu drive. Thats not a terrible thing but Id rather not do that if you dont have to.

As said before, bootloader to sdb, which is the same drive that holds Ubuntu. What you said, after Ubuntu install without changing the BIOS HDD settings, Windows started automatically and no way to see anything of Ubuntu. I tried something within Windows 7 with EasyBCD, but this didn't work out. Next step, I changed the boot order in the BIOS. Now the Ubuntu drive is #1 however, the grub menu pops up and gives me the choice for Ubuntu or Windows 7 and that both works.

[SIZE=3]Finally ...... [/SIZE]:cool:

---

### Post by P4man on 2010-07-28
great! Have fun exploring ubuntu. im sure you'll run in to plenty of issues and questions but please mark this thread as solved (in thread tools).

---

### Post by Angelique-van-Campen on 2010-07-28
> **P4man said:**
> great! Have fun exploring ubuntu. im sure you'll run in to plenty of issues and questions but please mark this thread as solved (in thread tools).

I'll do and thanks for all the help!

Greetings,
Angelique

---

### Post by beew on 2010-07-28
> **P4man said:**
> Seems like ubuntu can not access the windows partition. This could be because its "dirty", which happens when windows is not shut down properly. To remediate that just boot windows and perform a chkdsk.
.

Yeah, actually I have a similar question even though I am not using Wubi for exactly the reason you stated, I want a full Ubuntu installation independent of Windows.

I set up a dual boot system between Windows XP with Ubuntu (I keep Windows basically for testing purpose now, say I can't get Skype working in Ubuntu I would try it in in XP and see if it works etc). 

At first I tried to use gparted from a live usb to partition the hard drive but kept getting bad sector warnings and it just wouldn't work. I booted backed into Xp and did chkdisk not once, but a few times in a row, defregged and then chdisk again. XP found nothing wrong, but when I booted into the live usb  again  gparted still complained that there were bad sectors and just wouldn't partition the drive.

Finally I did the partition using a free (as in free beer?) version of Easeus Partition Manager in  Windows to create room for Ubuntu. EPS carried that out without any complaint.

After that I was able to install Ubuntu in the usual way into the unallocated space created by EPS and everything went smoothly. But even now if I start gparted just to look at the hard drive (without doing anything of course) , there is still a little brown triangle with an exclamation mark beside the ntfs partition  where XP lives though the Ubuntu partition shows no error. 

I recently booted from a Fedora 13 live usb, I get a warning about bad hard disk sector right when the gnome desktop appeared. Again it reported  that there were bad sectors in the ntfs partition. I scanned again with Windows tools in XP and again found nothing.

I wonder if Linux may have a problem in recognizing certain versions of ntfs. Yes, apparently not all ntfs formats are the same,  even Windows has a problem keeping track itself. It seems that ntfs created by Windows 7 and XP are not compatible. Either Windows 7 cannot see the ntfs partition created by XP or the other way around,--can't remember which is which.

---

### Post by P4man on 2010-07-28
Dont confuse bad sectors with partition or file system problems. Bad sectors are on a much lower hardware level and independent of how you partition your drive or how you format it. 

The warnings you are getting about bad sectors may well be accurate, and they would be generated by "disk utility" smart monitoring tools. Go to system > adminstration > disk utility, select the harddrive in question and check out the smart status. Feel free to post a screenshot. (This tool does give false positives on some drives but it should be easy to spot as the number bad sectors will be insanely high like 65553).

Modern harddrives (basically any drive over 20GB) will automatically detect and remap bad sectors to spare ones. As long as you dont run out of spares, you can keep using the drive and usually not have any data loss or problems. But an increasing number of bad sectors almost always points to a dying drive. Take those warnings seriously. Double check with another smart monitoring tool. If they agree, better make double sure you have a backup and prepare to replace the disk.

as illustration here is a screenshot from my smart data:

[[IMG]http://img339.imageshack.us/img339/3338/screenshot048q.th.png[/IMG]](http://img339.imageshack.us/i/screenshot048q.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

The disk is healthy but it did overheat (and thats true). The one to pay special attention to is relocated sector count. Anything over zero is cause for concern. Anything over a few 100 is cause for alarm.

---

### Post by beew on 2010-07-28
P4Man

Thanks for the info, will do a check when I go home.  But I am still puzzled why didn't Windows and Easus find anything wrong.

It wouldn't surprise me if there are damages caused by overheating. It is an old Dell I have inherited from a friend. He used to complain that the laptop got so hot that it burned his thigh. :)  This is apparently a model that Dell got sued for overheating. When I got it the first thing I did was to download and install i8k (in windows and later in Ubuntu as well) and that sorts of keep the temperature under control.

But then if it is overheating, why is it only in the Windows partition? 

I am actually thinking of cloning my Ubuntu partition just in case and I am searching for a good way to do it so that I can restore the whole thing in a different computer in case something goes wrong. But I should search around the forum first and then start a new thread if needed. :)

---

### Post by P4man on 2010-07-28
> **beew said:**
> P4Man

Thanks for the info, will do a check when I go home.  But I am still puzzled why didn't Windows and Easus find anything wrong.

Because neither windows nor easus check SMART data by default. These kinds of errors are completely invisible to any operating system or even BIOS as the drive controller manages this by itself. You can no check a physical sector of a drive like you could in the old days; its all "virtualized". 

Information like this is only exposed through the SMART interface and you need a smart monitoring tool to read and interprete that data. It ships by default on ubuntu 9.10 and newer, afaik windows doesnt do this. You need an app like smartmontools or speedfan under windows (and some bioses will report errors if they exceed certain tresholds).

more info here:
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

---

### Post by beew on 2010-07-29
Hi, P4Man,

Try to run the SMART disk test with disk utility as you said. But it got stuck at power cycles 5178 and reported something like 196612 bad sectors! 
Here is a screen shot.

---

### Post by P4man on 2010-07-29
That very much looks like a false positive to me. Try running a smart utility under windows, but I dont think there is a problem. That number is way too high to be credible.

---

### Post by beew on 2010-07-29
Hi, P4man,

That is reassuring. :) But why do you think SMART scan got stuck at power cycles 5178? Why is it that I get bad sector warnings from not just gparted but also disk utility and whatever that Fedora uses? Is there a chance that it may have to do with an unusual ntfs format?

I think this guy might be in the same situation.
[URL="http://www.allquests.com/question/2301606/%5Bubuntu%5D-cant-resize-ntfs-partition-due-to-bad-sector.html"]http://www.allquests.com/question/2301606/%5Bubuntu%5D-cant-resize-ntfs-partition-due-to-bad-sector.html
[/URL]

---

### Post by P4man on 2010-07-29
> **beew said:**
> Hi, P4man,

That is reassuring. :) But why do you think SMART scan got stuck at power cycles 5178?

What do you mean it got stuck? The power cycles is just one of many parameters, it shows how often the disk has been powered on. If its accurate; it has been powered on and off a LOT btw.

If you mean the smart scanning tool froze, well, no idea but probably more evidence of a problem between palimpsest (thats the name of smart monitoring tool used) and your drive. 

>  Why is it that I get bad sector warnings from not just gparted but also disk utility and whatever that Fedora uses? 


Fedora also uses Palimsest. If you want confirmation of this problem, try running smartmontools on windows or speedfan or some other utility. Palimpsest is known to report relocated sector count wrongly on some drives (note the standards for reporting these values arent well defined and they are different between different drive manufacturers).
> 
Is there a chance that it may have to do with an unusual ntfs format?

None whatsoever. SMART monitoring is completely independent of partitioning or file systems. A windows smart tool can assess your drive without any issues even if it has Ext4 partition on it that windows understands nothing about. It works even if you zero fill the drive.

For an analogy... consider a RAID 5 setup on a server. you access files on that server over the network. To your client its completely invisible if the server uses NTFS or Ext or whatever. Its even invisible if one of the harddrives of the raid failed. You can run any tool you want you will never find out; unless you run a tool that can talk to the RAID controller on the server and that would report one disk has failed and needs replacing.

A hdd controller works somewhat like the RAID controller in the above analogy. No filesystem or partitioning tools can reveal what really goes on inside the drive. The "sectors" it sees and works with are logical, not physical. 

> I think this guy might be in the same situation.
[URL="http://www.allquests.com/question/2301606/%5Bubuntu%5D-cant-resize-ntfs-partition-due-to-bad-sector.html"]http://www.allquests.com/question/2301606/%5Bubuntu%5D-cant-resize-ntfs-partition-due-to-bad-sector.html
[/URL]

Possibly. I havent had a bad drive since I started using linux, so i dont know if gparted nowadays refuses to format or repartition if palimpsests reports serious problems (it wouldnt be a bad idea, but I dont know if it does. apparently so though?).

---

### Post by beew on 2010-07-29
Hi, P4man,

Thanks for the explanations, it is very educational. I meant to say that the self test got stuck forever apparently, I somehow put it in the wrong way.

---

