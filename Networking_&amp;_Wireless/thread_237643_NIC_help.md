---
title: "NIC help"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by oldcity on 2006-08-16
Did a:
dmesg | grep eth0

eth0: Broadcom 4400 10/100 BaseT Ethernet 00:14:22:8e:ac:c9
ADDRCONF (NETDEV_UP): eth0: link is not ready

How to make ready?
tia
oldcity

---

### Post by tuxy on 2006-08-17
Conifgure the NIC card in /etc/network/interfaces.
OR try doing *ifdown eth0* and *ifup eth0*

---

### Post by oldcity on 2006-08-19
Tried your suggestion didn't work.
Conifgure the NIC card in /etc/network/interfaces.
OR try doing ifdown eth0 and ifup eth0
__________________
What happened was I was doing an update on July 21 using
the wireless connection. I clicked on the update icon.
It got to the end with 2 item remaining and then seemed
to time out. I rebooted and a system>admin.>network
the wireless option was gone. I did an modprobe ndiswrapper
and got the following message. I have no idea what to do to
get it back.
****
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-686/kernal/drivers/
net/ndiswrapper/ndiswrapper.ko): Invalid argument
****

---

