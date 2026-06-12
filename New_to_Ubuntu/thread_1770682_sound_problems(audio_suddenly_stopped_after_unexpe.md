---
title: "sound problems(audio suddenly stopped after unexpected restart)"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by ravikanth.vva on 2011-05-29
Suddenly after an unexpected power problem i restartd my computer and sound was gone....no audio!!...i checked everything and then tried it in my windows 7 and it was alright.....i even tried repairing the system....need help

thanks

---

### Post by khelben1979 on 2011-05-29
Post your output from ```
lspci
``` from a terminal and paste it here. Knowing what you got makes it easier.

Sometimes I haveto activate the button for Audigy Analog Digital in KMix (sound mixer software). In your case, it can be several things. A kernel upgrade are common to brake the sound driver. The fix would be to downgrade your Linux kernel, searching for the old one in [Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center").

---

### Post by ravikanth.vva on 2011-05-30
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by ravikanth.vva on 2011-05-30
it happend when the system shut down because of a power failure....i upgraded the software after that by booting in to the recovering mode hoping itll recover

---

### Post by khelben1979 on 2011-05-30
You can try and check [this thread]("http://ubuntuforums.org/showthread.php?p=5148501") to see if anything helps.

---

