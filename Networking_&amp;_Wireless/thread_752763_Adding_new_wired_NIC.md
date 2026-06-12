---
title: "Adding new wired NIC"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by DariusVE on 2008-04-11
Hi all

I have an old Compaq Deskpro computer, that doesn't have an integrated NIC, so I installed an old Realtek NIC and work flawless.

A firend give me a much capable Compaq Deskpro motherboard, with integrated nic, so a installed this motherboard, a two NIC a 3COM 10/100 and the Realtek.

But the server detects the Realtek as eth0 and the two other cards are disabled, but I can enable it using ifconfig eth1 up and ifconfig eth2 up

My questions:
1) How can I tell LINUX that all nic must be enabled
2) How can I use the integrated nic as eth0.

Thanks

Darius

---

### Post by mohammadrizki on 2008-04-14
Hi, there,
Perhaps you can take a look at other discussion here, I think it quite similar to your problem.
1. [http://ubuntuforums.org/showthread.php?t=501221]("http://ubuntuforums.org/showthread.php?t=501221")
2. [http://ubuntuforums.org/showthread.php?t=401170]("http://ubuntuforums.org/showthread.php?t=401170")

Cheers & good luck,

---

