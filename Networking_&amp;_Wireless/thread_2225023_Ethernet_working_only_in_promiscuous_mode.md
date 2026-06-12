---
title: "Ethernet working only in promiscuous mode"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by adityashah30 on 2014-05-19
I recently installed Ubuntu 14.04 LTS on my Dell XPS 15 l502x. I also installed TLP tools to enhance battery life and I have been experiencing a strange behavior. My ethernet is working fine after a fresh reboot but when I suspend, it stops working and works only if I put the ethernet card in promiscuous mode. Any idea as to why this happens? I confirmed this problem is solely due to TLP as when I uninstalled TLP, the problem disappeared.

Thanks

---

### Post by grahammechanical on 2014-05-19
Why?

To reduce power consumption during the period of time the machine is suspended. What is actually happening is that state of the OS is stored in RAM and most of the electronics are switched off except the power to the RAM. So, the ethernet adapter is powered off. A switching off and rebooting will power on the ethernet adapter but its seems that resume from suspend is not able to power the ethernet adapter back on.

Regards.

---

### Post by adityashah30 on 2014-05-19
Thanks for the input but then it doesn't explain why it works fine when put in promiscuous mode. Also can you suggest any tweak in the settings of TLP by which this can be avoided?
Thanks

---

### Post by adityashah30 on 2014-05-19
I enabled the Wake On Lan in TLP and that solved the problem. While this does solve the original problem, I still can't wrap my head around the weird phenomenon in which setting adapter in promiscuous mode magically makes it start working.

---

