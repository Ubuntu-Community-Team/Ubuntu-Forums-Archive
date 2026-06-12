---
title: "Netgear MA311 stopped working on upgrade"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by ceilingfish on 2005-11-29
Hi,
I just installed the latest batch of updates on my computer, and it seems to have killed my computer. The most significant seems to have been an upgrade to kernel 2.6.12 from 2.6.10.

It has stopped most of my applications connecting to the internet, and I can only occasionally get a DHCP lease. I disabled IPv6, because I found a couple of threads on here that recommended it, but it doesn't seem to have improved much.

Help anyone! Please!!

Tom

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=ceilingfish]Hi,
I just installed the latest batch of updates on my computer, and it seems to have killed my computer. The most significant seems to have been an upgrade to kernel 2.6.12 from 2.6.10.

It has stopped most of my applications connecting to the internet, and I can only occasionally get a DHCP lease. I disabled IPv6, because I found a couple of threads on here that recommended it, but it doesn't seem to have improved much.

Help anyone! Please!!

Tom[/QUOTE]

If you reboot and choose the 2.6.10 kernel from grub, does it seem to work again?

---

### Post by ceilingfish on 2005-11-29
How do I do that?

Sorry, serious noobiness going on.

---

### Post by ceilingfish on 2005-11-29
Hi,
I got loaded into kernel 2.6.10, and my internet connection works again! Thankyou!

How do I set it so that it loads 2.6.10 by default?

Cheers,
Tom

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=ceilingfish]Hi,
I got loaded into kernel 2.6.10, and my internet connection works again! Thankyou!

How do I set it so that it loads 2.6.10 by default?

Cheers,
Tom[/QUOTE]
Well, you can edit /boot/grub/menu.lst and change the "default" setting.  Be careful, though.  If you mess that file, you might have problems booting back into the system to correct it.  It is best to have a Live CD like Knoppix that you know you can use to get into the system and fix things if you make a typo.

---

### Post by ajohn2550 on 2007-02-04
hey i am trying to use the same card and i am having trubble installing it on xubuntu 6.10

---

