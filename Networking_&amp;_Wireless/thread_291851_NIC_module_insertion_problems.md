---
title: "NIC module insertion problems"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by blualchemist on 2006-11-03
Well Well...

I have a DGE-530T dlink gigabit nic that uses the sk98lin driver.

I add 'alias eth0 sk98lin' to '/etc/modules' and '/etc/modules.d/alias' and upon a reboot a 'lsmod | grep sk98lin' outputs "sk98lin     166872  1"

I am using Ubuntu 5.1 2.6.12-9-386.

Im not sure how to make sk98lin the driver for eth0 besides those steps but i still cant break avg 38mb/s speed even tho the entire network is gigabit with the same cards and i have full speed windows to windows machines.

Any idea what commands/script additons i need??

Thanks!!

---

