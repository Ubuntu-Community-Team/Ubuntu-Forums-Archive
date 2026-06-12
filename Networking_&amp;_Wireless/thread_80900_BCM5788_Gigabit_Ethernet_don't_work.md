---
title: "BCM5788 Gigabit Ethernet don't work"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by Fitti on 2005-10-23
Hello,

My laptop (Acer Aspire 1692) have a Broadcom Corporation BCM5788 Gigabit Ethernet (rev 03) LAN card and I can't configure the card.

I tried to use DHCP and static IP but the connection doesn`t work. I don't know what is the problem. Any ideas?

Thanks.
PD: Sorry for my english.

---

### Post by Colsta on 2005-10-24
I can confirm the same problem with a fresh Breezy install on my Acer 1692 WLMi as well (same NIC).  Wouldn't use DHCP during the install at all (despite Hoary and Win XP using the same router successfully) and refused to assign an IP to the interface even when configuring as static.
Searching through the forum, there seems to be a general problem with Breezy and networking 'out of the box'.  I lack the time to play about this time around, so have reverted to Hoary for now.

---

### Post by Fitti on 2005-10-24
And what about wifi? Works? 

I can't connect to any ap. I think that the problem is someting with the lans (lan or wifi) and breezy.

---

### Post by Fitti on 2005-10-25
I install an old linux-image (2.6.11) and the lan card works fine in breezy.

---

### Post by chatuser on 2005-11-23
- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Everything works now, damn ACPI !!

---

### Post by Fitti on 2005-11-26
[QUOTE=chatuser]- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Everything works now, damn ACPI !![/QUOTE]

Yeah!! Great work! :) 

Thanks :KS

---

### Post by owenevl on 2008-01-14
> **Fitti said:**
> Yeah!! Great work! :) 

Thanks :KS
so i have to have breezy? i cant use gutsy with this w/lan card?

---

