---
title: "eth1 is wired connection?!"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by ReapeX on 2006-12-29
*Hopefully, this thread will help someone in the future with this **rare** Wireless changed to Wired problem.....*

Ack!

I was trying to mount my ntfs drive in Ubuntu 6.10 and somehow my wireless profile in System->Administration->Networking  eth1 was changed to a wire connection!

I restored the backup version of fstab but nothing changed, eth1 is still listed as a wire connection.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=5db61eba-3e7b-40b8-a285-6d0651cb9dc2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4bf2c555-fca5-442f-a459-739b4ae96dee /home           ext3    defaults        0       2
# /dev/hda2
/dev/hda2 /media/hda2 vfat iocharset=utf8,umask=000 0 0
# /dev/hda1
/dev/hda1 /WindowsXP ntfs umask=0000 0 0
# /dev/hda4
UUID=bc730911-ba9f-469c-a6ad-785c30231f0a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

interfaces:
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0


I'm totally new to troubleshooting wireless problems on Ubuntu with the command line interface and I don't want to reinstall Ubuntu [again ack].

Has anyone seen this problem before?  When eth1 changes to a wired connection after modfying fstab (I also set up evolution mail before the problem started but I doubt that is the reason for this).

---

### Post by ReapeX on 2006-12-29
Device Manager recognizes my 2200BG Wireless Card.

It has been working for weeks until I modify fstab so hda1 could be mounted to the desktop....note: the ntfs drive still isn't showing on the desktop bah.

Also is ther some other program that may work better for wireless than Ubuntu's default networking program?
Or will another program still detect eth1 as being a wired device since fstab was changed?

---

### Post by ReapeX on 2006-12-29
Another update, ifconfig shows the wireless card but the iwconfig command is not found.

Do I have to install ndiswrapper? I didn't have to originally.

---

### Post by ReapeX on 2006-12-29
alright now, I can't turn on eth0 or eth1 using the "ifconfig eth1 up" command.

I receieve a SIOCSIFFLAGS: Permission denied error.

---

### Post by ReapeX on 2006-12-29
Does reloading sound like a good idea?
I barerly have anything ont he drive right now, yes I will have to go back and reconfigure a lot of things, download updates and patches but that may be easier than spending 12+ hours on this problem.

---

### Post by dmizer on 2006-12-29
heck no.  don't reload.  we just need a lot more information.  for starters, we need more information about your wireless card ...

post the output of lspci and dmesg (please be sure to enclose these in [code] tags so they don't go scrolling to infinity.  if you have trouble with that, click on the "go advanced" button under the quick reply.

fstab should have nothing to do with networking unless you've moved a critical folder.  what do you mean by "mounted" your hda1 to the desktop?

---

### Post by ReapeX on 2006-12-29
Reduce version of lspci output:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5650] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

reduced version of dmesg:
[17179589.068000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179589.144000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0f:1f:1a:e3:02
[17179589.144000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179589.144000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[17179589.144000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179589.144000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:014e]
[17179589.144000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.144000] Yenta: Routing CardBus interrupts to PCI
[17179589.144000] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64
[17179589.264000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179589.264000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[[B]17179589.264000] Driver 'ipw2200' needs updating - please use bus_type methods
[[/B]17179589.376000] Yenta: ISA IRQ mask 0x0458, PCI irq 11
[17179589.376000] Socket status: 30000006
[17179589.376000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

If the above information isn't enough let me know and I can post the entire output.

What's intresting is what I put in bold.  But I can't use the ethernet lan anymore either hmm

---

### Post by ReapeX on 2006-12-29
I mounted hda1 NTFS partition to the media folder so it would display on my desktop.

hda1 is drive C
hda2 is drive D my fat32 partition, also contains my home directory I believe

while Linux is on a separate logical partition

I mounted hda1 and hda2 to media directory, when I did that the ethernet and wireless eventually stopped working.  So in essence I changed the mount point of the home directory I guess....

---

### Post by ReapeX on 2006-12-30
I just went to intel site and downloaded  & unpacked the driver for ipw2200;  I'm trying to install it now.

---

### Post by ReapeX on 2006-12-30
Note: My ethernet connection is working again, eth0 in Connection Properties

---

### Post by ReapeX on 2006-12-30
> **ReapeX said:**
> I just went to intel site and downloaded  & unpacked the driver for ipw2200;  I'm trying to install it now.

Didn't work but I'm not sure if I extracted right, because the driver contained two other cabinet files...any idea what I'm suppose to do with those?  One of them is name fw so I"m guessing firmware.

Any help will be greatly appreciated!

---

### Post by ReapeX on 2006-12-31
I am following the guide on:
[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

However the remove script listed is no longer available at:

[http://wael.nasreddine.com/files/ubuntu/remove-old](http://wael.nasreddine.com/files/ubuntu/remove-old).

I don't think the script is necessary...if anyone disagrees please tell me >>

I removed the old files manually with the check old something command that was given to me.
Everything installed fine except for ipw2200 using the make && sudo make install comand:

laptop:/tmp/wifi/intel_ipw2200_120$ make && sudo make install
make: *** No targets specified and no makefile found.  Stop.

Any ideas?

[I]I went ahead and launched the sudo modprobe ipw2200, command and it worked without any errors...however my wireless connection is still showing as a wired connection in Network Settings >.>
Hopefully this thread will help someone in the future with this RARE problem[/I]

---

### Post by ReapeX on 2006-12-31
Alright, my hardware media sound buttons aren't working any more either.

Sorry guys but if I don't get a ton of replies to this thread I'm going to have to do a reload...the problems keep multplying.

It's like I changed a reference pointer to where my sound and wireless drivers use to be but I don't understand enough about Ubuntu, yet, to fix the problem!  Hmm maybe...I'll hold off for a bit yeah, I won't do a reload until later next week (if I can't fix the problem).

---

### Post by ReapeX on 2007-01-01
I downloaded Network Monitoring tools and modfied the interfaces file, now it appears UBuntu can detect my wireless connection through the Network Monitoring Tools Softwares.  However, my ethernet connection is no longer working.  Also, I can't access my Administration Account and add to that I can't control the sound using the machine's hardware buttons.

It's good that I'm reinstalling one **final** time, I get to correct some mistakes that I made in the past.  Like installing grub to hd0, which is where another OS resides.

In SUMMARY, I found a work around for my original problems a large number issues are also appearing.  So I'm going to back up my home partition and do a reload, thanks to everyone who read my posts and\or tried to help.

---

