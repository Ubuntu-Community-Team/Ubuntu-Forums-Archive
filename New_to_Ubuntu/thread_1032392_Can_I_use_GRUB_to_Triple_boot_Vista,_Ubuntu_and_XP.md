---
title: "Can I use GRUB to Triple boot: Vista, Ubuntu and XP?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-06
Hi, Can I use Grub to Triple boot Vista, Ubuntu and XP?

---

### Post by Maverick1712 on 2009-01-06
Yes, assuming they are on seperate partitions (obviously).

---

### Post by tuxxy on 2009-01-06
Yes indeed :)

---

### Post by EnGorDiaz on 2009-01-06
> **looi76 said:**
> Hi, Can I use Grub to Triple boot Vista, Ubuntu and XP?

check my sig full guide

---

### Post by looi76 on 2009-01-06
Sorry for not being clear in the beginning. I have Vista, XP and Ubunutu installed on my computer. My question was can I triple boot vista, xp and ubuntu using **ONLY GRUB** because at the moment if I want to boot xp or vista I have to go to Vista Boot Loader throguh Grub then I can choose if I want to boot Vista or XP. Is it possible to boot Vista and XP through GRUB?

---

### Post by Tim Sharitt on 2009-01-06
For some reason Vista removes XP's bootloader when installed. I believe it is possible to fix this by restoring XP's bootloader via the XP install CD, but you will likely need to reinstall grub afterwards.

Guide to reinstall grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by B34ST1Y on 2009-01-06
> **looi76 said:**
> Hi, Can I use Grub to Triple boot Vista, Ubuntu and XP?
yes, so long as you edit the grub configuration to point to the boot volumes of the relevant operating system

---

