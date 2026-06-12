---
title: "Can't boot 7.04, Atheros PCI Problems"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by snyperof1 on 2007-05-30
I am running 7.04 Fiesty on a Thinkpad t40 with:
>1.4G Pentium M
>30 Gb Harddisk
>512mb RAM
>Atheros Mini PCI wireless card

I wanted to use the Madwifi drivers for the card so I followed this this thread:
[http://ubuntuforums.org/showthread.php?t=75451&highlight=madwifi+howto]("http://ubuntuforums.org/showthread.php?t=75451&highlight=madwifi+howto")
Everything appeared to work fine during the install. But when I reboot, my laptop boots for 30 seconds and then stops and flashes the Caps-Lock Light. After a 2nd reboot and removing the boot-screen with Ctrl-Alt-F(something) I see that the error deals with my Atheros wireless card and that the kernel panics when the card doesn't sync (see attatched Image). But I can't make sense of any of the other code. If someone could help or even just point me to another thread with the answer that would be wonderful.

---

### Post by spd106 on 2007-05-30
You do know that the latest (but one) driver is included in Feisty, right?

I suggest you attempt to boot in recovery mode or I think you can pass pci=off as a parameter. 
Failing those try a live cd, to mount the root partition and chroot into the install environment. Then re-install the linux-restricted-modules package. 

If you want compile madwifi with patches etc then I suggest you follow the guides on the madwifi.org site. The guide you linked to is rather old and was intended for Ubuntu 5.04.

---

