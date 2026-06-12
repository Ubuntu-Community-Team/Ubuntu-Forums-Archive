---
title: "ZyXEL -- do i need ndiswrapper?"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by rygar on 2007-05-14
I have a desktop with a wireless PCI card.  It's a ZyXEL card, but im not sure of the model.  (what command do i use to find out?)

the wireless card shows up in hardware information, so i think the card is registered fine.
but it doesnt list my wireless network.  do i need ndiswrapper?  if not, what do i do to fix it?

---

### Post by GS2 on 2007-05-14
output of lspci please - and lspci -n

---

### Post by rygar on 2007-05-15
well since i can't copy paste, i just wrote down what i thought was the relevant information:

lspci
00:09.0 Network Controller: Texas Instruments ACX 111 54Mbps Wireless Interface

lspci -n
00:09.0 0600: 1106:3099

it DID recognize nearby networks for a few minutes, and i managed to connect, though painfully slow.  now its not detecting any networks again.  just earlier today, before i reformatted, i was using it with XP and it connected with no problems, and the internet ran perfectly.

by the way i found out it's a ZyXEL 302v2

---

### Post by GS2 on 2007-05-15
relevant output of dmesg after a reboot - will show what the OS is up to.

Set you network to open (no encryption) just to see if you can get connected - and use DHCP

If still no joy:

Possible the ACX open sources drivers will work although it could be a firmware issue.

Noticed this bug at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/81812](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/81812)
few months old, but may help if it is a firmware issue

---

