---
title: "slow lan samba transfers"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by Jeek Elemental on 2007-07-30
Hi, having searched around abit I found no solution for this, hope someone can give me a hint:

setup: feisty with 2xgigabit ethernet (nvidia onboard), usb 11Mb wireless (3com) PC1
gutsy with 1xgigabit ethernet (realtek onboard) PC2
winXP 11Mb wireless (laptop) PC3
wireless router 11Mb connected to cable modem

PC2 connects to wireless thru PC1, internet is working fine on all pcs, full speed.

I set up tftp server on PC1 for PC2, this works fine (PXE boot). 
However using samba to transfer files PC1<>PC2 is extremely slow, 100-200KB/s on a straight gigabit link.
Same happens with PC1<>PC3, around 200KB/s.

If I use tftp PC1<>PC2 in same environment (ie full desktops) I get full speed.

Other than setting shares I havent messed around with samba, is there some magic setting Ive missed?

---

