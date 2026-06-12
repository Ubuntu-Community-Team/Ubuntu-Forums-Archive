---
title: "hotplug and eth1 start fails"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by doctorphoton on 2005-10-23
hello,
I searched all the forum but didnt find solution for my problem.

I installed ettercap on my system and when restarted it,
at boot , it said
hotplug subsystem [fail]
Configured network interfaces [fail]

every thing is working fine but can not make my network interface card up
i used to manually start hotplug subsystem
started [ok] from Terminal

then tried to start eth1
#sudo ifup eth1
it says--- /etc/network/interfaces:17: too fewparameters for iface line
ifup: couldnt read interfaces fiole "/etc/network/interfaces"

eth1 uses irq 19
when i did ethtool eth1
it listed all the info
link detected: yes

when i reboot, deconfiguring eth1 [fail]

the /etc/network/interfaces have detected eth1

i mean to say, that eth1 is detecting but as hotplug fails at boot so , i am unable to start network card as well
through control center i used to start it but eth1 starts when i click enable and stops automatically after a second

Please help me solve thhis problem
thanks in advance

---

