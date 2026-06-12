---
title: "Dual Boot: no DHCP address after XP"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by lamphax on 2008-03-26
Basically, If I boot into Linux straight away I get an IP address by DHCP and everything is happy. But, If I boot to Windows first, then reboot Linux I dont get a DHCP addy, Even if i set a static IP I still cant ping any other machines.
I see my network card listed from lspci and in the hardware info screen and the network manager says it is connecting (trying to get DCHP addy) but never gets one.
I Tried /etc/init.d/networking restart , still nothing. If i give up and come back the next day The same thing happens all over again.
I tried ipconfig /release before exiting windows and still didnt work.
One interesting caveat is that when this issue occurs, there are no status indicator lights blinking on my switch at all (its like the NIC is not even powered up).

P.S - Please dont tell me not to boot to Windows first. It is a nessesary evil for my job.


Thanks,
DC

---

### Post by desper on 2008-03-26
Setting a shorter ip lease life-span in router's administration page would perhaps solve the problem. but not sure.

---

### Post by lamphax on 2008-03-26
i am not convinced that DHCP is the issue. The reason is because the lights on the switch are not blinking and a static address does not work. Any other suggestions?

Thanks.

---

### Post by Iowan on 2008-03-26
Do you do a power-down reboot?  Seems like I read another thread around here that Windows doesn't always release/reset properly - a power-down reboot solved the problem.

---

