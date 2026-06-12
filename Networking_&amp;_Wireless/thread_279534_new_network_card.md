---
title: "new network card"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by RikoW on 2006-10-18
Hi all,

my laptop got a new motherboard today, which also means, that the network card was exchanged. After rebooting the machine into ubuntu with a network cable plugged in, no network was found. I had to configure a new network interface (eth2, eth0 was the old wired network card, eth1 is the wireless card). Can I somehow convince Ubuntu to re-use eth0 for the wired network?

I assume, I just need to remove some config file somewhere, or replace the old MAC address with the MAC address of the new card in some file. But don't know where.

Thanks for your help,

              Riko

---

### Post by spd106 on 2006-10-18
Try looking in /etc/iftab.

---

### Post by RikoW on 2006-10-18
Thanks, that was it :)

---

