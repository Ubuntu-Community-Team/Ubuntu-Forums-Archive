---
title: "external sata and ide not working"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by corky748 on 2009-11-17
I have ubuntu 9.0.4 and am new to it all.
i also have a 60gb sata external and a 250gb ide external and they don't work. i've tried a few different forums and cant find anything that works,
i think it has something todo with mounting the drives but i don't know what i'm doing, also i don't want to kill my laptop by doing something wrong.
my ipod and my small pen drives don't seam to have this problem
any help is aprecated...

---

### Post by Paqman on 2009-11-17
So are these drives actually connecting with USB? Or is the SATA one over eSATA?

---

### Post by QLee on 2009-11-17
Yes, and another question corky748, what are you referring to when you say "work". What is it you want to accomplish, mount them? ... read from them? ...save to them? or?

---

### Post by corky748 on 2009-11-17
they are going through usb and when i insert them nothing happens, and they are no where to be found on the computer.
i want to read and write to them, they we running on windows xp before i switched to ubuntu, so they are nts as far as i know...

---

### Post by coffeecat on 2009-11-17
@corky748, how are you connecting those external drives? If by USB, they should just automount and a browser window open on your desktop - so long as the filesystem is recognised in Ubuntu. What filesystem is on them: NTFS, FAT32, HFS+, something else?

**Edit:**, also, what make are they? When I mean make, I mean the enclosure rather than the HDs themselves. Some people have problems with some Seagate drives - it's possible that the firmware in these drives causes problems in Linux.

---

### Post by corky748 on 2009-11-17
when i plug them in nothing happens. 
they are internal PC drives running on ide reader which converts them to usb, i think they are ntfs.

---

### Post by coffeecat on 2009-11-17
> **corky748 said:**
> they are internal PC drives running on ide reader which converts them to usb

Now you've confused me. :confused:

You said earlier that they were external drives. OK - HDs in external enclosures with USB connector? Or drives sitting inside your box connected to some sort of PCI card adapter?

Or something else? :?

We need more **detail**. :wink:

---

### Post by corky748 on 2009-11-17
the hd is a seagate but the sata is running in a packard bell box so i don't know if it's a seagate

---

### Post by corky748 on 2009-11-17
the hd is a iomega box but the old hard drive gave up so i bought a pc internal hard drive and put it in the iomega box...

---

### Post by corky748 on 2009-11-17
they are external hard drives running through usb one 250gb seagate and a 60gb sata running in a packard bell external box

---

### Post by QLee on 2009-11-17
> **corky748 said:**
> when i plug them in nothing happens. 
they are internal PC drives running on ide reader which converts them to usb, i think they are ntfs.
So, if I understand you correctly, these are drives in USB enclosures and when you plug them in, the drive light on the enclosure does not ever light up or flash, or have I misunderstood?

---

### Post by Wim Sturkenboom on 2009-11-17
Stick them in (one by one) and post the output (let's say last 15 lines) of the *dmesg* command for each of them. You run the dmesg command in a terminal.

---

### Post by corky748 on 2009-11-17
they are drives in usb enclosures.
they start up and the light is on but they are not being read... no auto play, no drive in file browser.
what is strange is my 2gb usb pen drive works as does my ipod..

---

### Post by QLee on 2009-11-17
> **corky748 said:**
> they are drives in usb enclosures.
they start up and the light is on but they are not being read... no auto play, no drive in file browser.
what is strange is my 2gb usb pen drive works as does my ipod..
Follow the advice poster Wim Sturkenboom gave.

You probably can get enough info using the command dmesg | tail, that will show you the last 10 lines and we'll want to see what the system thinks of those drives.

Is there any chance you unplugged them from a Windows system without using the safely remove applet?

---

### Post by corky748 on 2009-11-17
i tried "dmesg" and these are the last few line

[ 1345.296079] usb 1-1: new full speed USB device using uhci_hcd and address 14
[ 1345.442136] usb 1-1: not running at top speed; connect to a high speed hub
[ 1345.497050] usb 1-1: configuration #1 chosen from 1 choice
[ 1345.536616] scsi14 : SCSI emulation for USB Mass Storage devices
[ 1345.539241] usb-storage: device found at 14
[ 1345.539250] usb-storage: waiting for device to settle before scanning
[ 1345.816131] usb 1-1: USB disconnect, address 14
[ 1643.144116] usb 1-1: new full speed USB device using uhci_hcd and address 15
[ 1643.290091] usb 1-1: not running at top speed; connect to a high speed hub
[ 1643.344967] usb 1-1: configuration #1 chosen from 1 choice
[ 1643.381759] scsi15 : SCSI emulation for USB Mass Storage devices
[ 1643.385057] usb-storage: device found at 15
[ 1643.385065] usb-storage: waiting for device to settle before scanning
[ 1643.664133] usb 1-1: USB disconnect, address 15
[ 1755.736099] usb 1-1: new full speed USB device using uhci_hcd and address 16
[ 1755.882124] usb 1-1: not running at top speed; connect to a high speed hub
[ 1755.938321] usb 1-1: configuration #1 chosen from 1 choice
[ 1755.979065] scsi16 : SCSI emulation for USB Mass Storage devices
[ 1755.992758] usb-storage: device found at 16
[ 1755.992766] usb-storage: waiting for device to settle before scanning
[ 1756.504124] usb 1-1: USB disconnect, address 16
[ 2275.820104] usb 1-1: new full speed USB device using uhci_hcd and address 17
[ 2275.966104] usb 1-1: not running at top speed; connect to a high speed hub
[ 2276.020713] usb 1-1: configuration #1 chosen from 1 choice
[ 2276.058108] scsi17 : SCSI emulation for USB Mass Storage devices
[ 2276.061445] usb-storage: device found at 17
[ 2276.061452] usb-storage: waiting for device to settle before scanning
[ 2276.312136] usb 1-1: USB disconnect, address 17
[ 2573.632135] usb 1-1: new full speed USB device using uhci_hcd and address 18
[ 2573.778132] usb 1-1: not running at top speed; connect to a high speed hub
[ 2573.832487] usb 1-1: configuration #1 chosen from 1 choice
[ 2573.864905] scsi18 : SCSI emulation for USB Mass Storage devices
[ 2573.867530] usb-storage: device found at 18
[ 2573.867538] usb-storage: waiting for device to settle before scanning
[ 2574.160127] usb 1-1: USB disconnect, address 18

---

### Post by ZhuaSD on 2009-11-25
bump.  I have seen these problems before.  I had to re-format a drive because of this stuff.

---

