---
title: "how to make Windows startup disks"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-16
Dear Forum,

I've a client who uses propriety software to manage business processes so I purchased a laptop for the project.

The laptop did have XP pre-installed and no CD/DVD. There is software to create backup DVD image though.

Since I use Ubuntu exclusively, I wanted to get Ubuntu on the system. I don't want dual boot because it is too much effort and doesn't allow copying of clipboard between OS.

So I created the DVD.iso, stored it to my network fileserver, installed Karmic Netbook with the USB and reformatted the drive. Then I installed open source Virtual box and tried to boot from the image.

Needless to say, the DVD is specific for the machine (OEM recovery edition) and doesn't work in VB.

XP doesn't install from external drives (didn't know that before hand).

I want to now install XP, Virtual box and Ubuntu in that order this time. Can anyone tell me how to get files onto the harddisk (or an external HDD). I have the recovery DVD, WinXP original CDs and an external harddisk.

All the disks I have are licensed so I'm not doing anything illegal.

TIA


Rich

---

### Post by phillw on 2009-11-16
> **RichardCL said:**
> Dear Forum,

I've a client who uses propriety software to manage business processes so I purchased a laptop for the project.

The laptop did have XP pre-installed and no CD/DVD. There is software to create backup DVD image though.

Since I use Ubuntu exclusively, I wanted to get Ubuntu on the system. I don't want dual boot because it is too much effort and doesn't allow copying of clipboard between OS.

So I created the DVD.iso, stored it to my network fileserver, installed Karmic Netbook with the USB and reformatted the drive. Then I installed open source Virtual box and tried to boot from the image.

Needless to say, the DVD is specific for the machine (OEM recovery edition) and doesn't work in VB.

XP doesn't install from external drives (didn't know that before hand).

I want to now install XP, Virtual box and Ubuntu in that order this time. Can anyone tell me how to get files onto the harddisk (or an external HDD). I have the recovery DVD, WinXP original CDs and an external harddisk.

All the disks I have are licensed so I'm not doing anything illegal.

TIA


Rich

If you can boot from USB, then you can create a Windows USB boot stick, boot and run XP.. Google has plenty of results for that.

/edit .. there's even instructions for dual-booting off a pen-drive - lol

Regards,

Phill.

---

### Post by RichardCL on 2009-11-16
I found many, many tutorials for making a pen drive with XP on it. Most of them required Windows either to install a PE program like BartPE or a driver like HP USB. None of them worked on Linux even under Wine.

Then I tried Uunetbootin and Ubuntu's USB disk create to try to put the files from the backup-iso onto a hard disk. Neither worked.

In the end, I burned the ISO to CD, purchased a USB DVD reader and installed Windows.

Now I could make a USB (since I have XP running on the system).

All a bit chicken/egg.

---

