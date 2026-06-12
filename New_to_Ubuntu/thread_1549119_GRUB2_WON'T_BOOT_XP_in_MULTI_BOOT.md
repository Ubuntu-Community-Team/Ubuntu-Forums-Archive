---
title: "GRUB2 WON'T BOOT XP in MULTI BOOT"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by woo10jw on 2010-08-09
Computer SetUp: 5 HDs
SSD--Dual Boot - Karmic & Lucid (EXT4)(64bit)
Raptor--Dual Boot - XPProSP2 (32bit) & Win 7 (Home64bit) (NTFS)
Other drives - Data, Music and Movies (NTFS)

Karmic & Lucid work properly, Grub2 fine.
 
Select Win7 loader. Choices - Win 7 & earlier Win ver (XP)
Select Win7 - everything fine, boots ok,
Select earlier win ver(XP) - system reboots, won't load XP

Unplug Ubuntu drive or hit F12 for boot menu, select Windows drive to boot from, XP & Win 7 boot fine.

Installation procedure on Raptor:
installed XP (1st part)/ installed Win 7 (2nd part)/ Ubuntu swap 3rd part.
Installation procedure on SSD:
installed Boot 1st part sda1 / installed Karmic /(root) sda5 / installed Lucid /(root) sda6
(rest of drive unallocated)

Didn't have this problem when XP & Win 7 installed on separate HD's. Grub2 gave me XP & Win 7 Choices everything booted fine. Only when I put the 2 windows systems on the same drive did this happen. Don't know much about Win 7.

Can anyone give me some ideas, can't seem to figure this one out

---

