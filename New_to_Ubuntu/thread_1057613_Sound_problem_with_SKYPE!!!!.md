---
title: "Sound problem with SKYPE!!!!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by fr.theo on 2009-02-02
I have successfully installed skype and logged in, however when i try to make a test call I get the error message "problem with audio play back" ?

I have remove pulse audio, configured skype to every sound device I have and even when one sound device will allow skype to dial out there is no sound?


Not sure what to do but I am guessing that there must be a configuration file some where to edit, I have done this even on games like Enemy Territory Quake Wars and got my usb mic to work and my sound by editing the config file of the game, so that i am able to voice chat with other players. 

skype should be more simpler than a game, I am just assuming that don't quote me, could any one help.

I have a Creative labs Audgy 2 sound card it works with everything else except Skype!.

Thanks in advance.

---

### Post by Crafty Kisses on 2009-02-02
What are the results of this command?
```
lspci
```

---

### Post by fr.theo on 2009-02-02
here is the results for "lspci"

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

---

### Post by fr.theo on 2009-02-02
solved thankyou.

---

