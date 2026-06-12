---
title: "Ubuntu and SATA hdd?????"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by stalkier on 2011-08-26
Ok HUGE mystery here. Ubuntu can NOT see any sata hard discs on my PC. I have 4 physical hdds. 2xSATA, 2xIDE. It detects the IDE fine. I can install Ubuntu on one of the IDE drives but GRUB will not work correctly. I have Windows 7 installed on the first SATA, the 2nd is free and is in 2 partitions. Even with the IDE drives unplugged it will NOT detect them. After hours of messing with it I am fed up. Please help, or I will have to just stay with windows and not dual-boot.

---

### Post by westie457 on 2011-08-26
Hi.
The obvious question to me is 'Have you checked the settings in the BIOS'? Just to make sure they are recognized there.

---

### Post by stalkier on 2011-08-26
> **westie457 said:**
> Hi.
The obvious question to me is 'Have you checked the settings in the BIOS'? Just to make sure they are recognized there.

Yes everything checks out fine. Windows boots fine, detects the other hdds. I used Cute Partition Manager, it also detects all drives. I just find it weird and frustrating.

---

### Post by jtarin on 2011-08-26
Try opening your box and disconnect/reconnect your hard drive(s) (from both ends, drive+mb). Disconnect and reattach its power supply as well.

---

### Post by Irony on 2011-08-26
If you used the ubuntu livecd can you see the sata drives in gparted or disk utility?

I have a sata and pata drive and for some months it saw the sata as sda but it inexplicably changed to sdb which confused grub until I noticed the difference and so re-installed grub and updated fstab.

---

### Post by prshah on 2011-08-26
> **stalkier said:**
> Ubuntu can NOT see any sata hard discs on my PC. 

From Ubuntu 8.04 onwards, SATA drivers are built in; previous versions didn't have them. Windows too had the same issue (no driver recognized in installer) so many manufacturers enable a kind of "IDE" compatibility mode in the BIOS.

You should look in your BIOS for settings related to SATA: Eg; "SATA Native mode", "Legacy Mode", "Compatibility mode", "IDE mode", "RAID" etc. Since this option varies from BIOS to BIOS, there is no exact step to follow. You will have to find a suitable-looking option and play with it. You can post whatever options you think look likely, if you'd like confirmation before doing anything.

This is one possible solution/workaround.

---

### Post by YesWeCan on 2011-08-26
Try toggling AHCI mode too.

---

### Post by LowSky on 2011-08-26
> **YesWeCan said:**
> Try toggling AHCI mode too.

Be careful with this option. if you reboot into windows it may crash if it is not set this way to default. Don't worry a simple Windows repair session fixes it quickly.

---

### Post by Irony on 2011-08-27
> **LowSky said:**
> Be careful with this option. if you reboot into windows it may crash if it is not set this way to default. Don't worry a simple Windows repair session fixes it quickly.

You can sort AHCI by going here; [http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

---

